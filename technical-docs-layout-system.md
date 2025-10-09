---
title: Technical Dive into the Layout System
description: This is a technical document about how FancyMenu's layout system works INTERNALLY. This is not something normal users should ever be interested in.
published: true
date: 2025-10-09T03:00:19.216Z
tags: technical
editor: markdown
dateCreated: 2025-10-09T03:00:19.216Z
---

# Technical Dive into the Layout System

This document is more like a nerd thing (and actually only exists for the Discord AI bot to better understand layouts).
If you're interested in the technical side of FancyMenu, this could be interesting for you too maybe.

## Storage Layout
- Layout configuration files live under `config/fancymenu/customization`, the directory created by `LayoutHandler.LAYOUT_DIR`. The base config root `config/fancymenu` itself comes from `FancyMenu.MOD_DIR`.
- Layouts are plain text files with the `.txt` suffix; `reloadLayouts()` only deserializes files whose path ends with `.txt`.
- User-provided assets referenced from layouts (images, audio, etc.) are expected in `config/fancymenu/assets`, created alongside the layout directory.
- Screen opt-in state is persisted separately in `config/fancymenu/customizablemenus.txt`, managed via `ScreenCustomization.CUSTOMIZABLE_MENUS_FILE`. Only fully-qualified screen class names are recorded; universal identifiers are filtered out when the file is read.

## Layout File Format
FancyMenu stores layouts as `PropertyContainerSet` structures serialized to text. Each file begins with `type = fancymenu_layout` (legacy files may use `type = menu`, still handled by the loader).

### Core Containers
- **`layout-meta`** &ndash; Primary metadata emitted by `Layout.serialize()` and parsed by `Layout.deserialize()`. Key fields:
  - `identifier`: screen identifier (classpath or universal) or `%fancymenu:universal_layout%` for global layouts.
  - `layout_index`: order used when stacking multiple layouts.
  - `is_enabled`, `last_edited_time`, `render_custom_elements_behind_vanilla`, and randomization flags (`randommode`, `randomgroup`, `randomonlyfirsttime`) control runtime behaviour.
  - Universal layout whitelists/blacklists serialize as semicolon-delimited strings to scope opt-in menus.
  - Layout-wide loading requirements are inlined here through `LoadingRequirementContainer.serializeToExistingPropertyContainer`.
- **`customization`** sections encode high-level actions (`setscale`, `autoscale`, `backgroundoptions`, `setopenaudio`, `setcloseaudio`, etc.) that mutate the base `LayoutBase`.
- **`menu_background`** holds serialized background builders. Only one entry is considered for standard layouts and deserialized through the `MenuBackgroundRegistry`.
- **`scroll_list_customization`** governs list header/footer textures, aspect ratio, blur, and overlay flags.
- **`layout_action_executable_blocks`** embeds optional scripting blocks that run on menu open/close; identifiers map into `GenericExecutableBlock` instances through `ExecutableBlockDeserializer`.

### Element Containers
- Layout elements are stored as containers with the type `element` (new format) or `customization` (legacy). Each must carry `element_type` so `ElementRegistry` can deserialize it back into an `AbstractElement`.
- Vanilla widget overrides are emitted with type `vanilla_button` and handled by `VanillaWidgetElementBuilder`, allowing FancyMenu to restyle or hide native buttons.
- `Layout.renderElementsBehindVanilla` determines whether deserialized elements populate the background or foreground lists.

### Example Skeleton
```ini
type = fancymenu_layout

layout-meta {
  identifier = net.minecraft.client.gui.screens.TitleScreen
  layout_index = 0
  render_custom_elements_behind_vanilla = false
  is_enabled = true
}

customization {
  action = setscale
  scale = 2
}

menu_background {
  background_type = fancymenu:image
  path = assets/example.png
}

element {
  element_type = image
  instance_identifier = custom_logo
  x = 10
  y = 10
}
```

## Initialization and Reload Flow
- FancyMenu initializes its customization engine during the `Minecraft$GameLoadCookie` construction, ensuring all other mods finished bootstrapping first.
- `ScreenCustomization.init()` wires registries, listeners, and finally invokes `LayoutHandler.init()`. The handler converts legacy folders and immediately calls `reloadLayouts()` to hydrate in-memory state.
- Layouts can be reloaded on demand via `/fmlayout` toggles or the in-game reload pipeline. `ScreenCustomization.reloadFancyMenu()` re-reads options, resources, and runs `LayoutHandler.reloadLayouts()` before re-initializing the current screen.

## Runtime Application Pipeline
- Every screen obtains a `ScreenCustomizationLayer` through the layer handler when initialization events fire. Layers cache the target screen identifier and subscribe to FancyMenu events.
- On `InitOrResizeScreenEvent.Pre`, the layer pulls the active layout list via `LayoutHandler.getEnabledLayoutsForScreenIdentifier()`. The handler filters by matching identifier, universal layout rules, and the screen-level enablement file.
- Layout-wide loading requirements gate application; unmet requirements are cached and the layout is skipped until they pass.
- Randomized groups (`randommode`, `randomgroup`, `randomonlyfirsttime`) enqueue layouts into `RandomLayoutContainer`, which caches selections per group and per menu session.
- After sorting by `layout_index`, `LayoutBase.stackLayoutBases()` merges background/audio/title/scroll configurations from all active layouts into a single composite.
- Forced GUI scale and autoscaling directives in the stacked base are applied immediately, resizing the screen before elements are constructed.
- When the post-initialization event fires, the layer discovers vanilla widgets, constructs element instances, and injects them into the screen's widget lists in draw-order.
- Rendering hooks draw backgrounds (respecting aspect ratio, overlays, and blur), vanilla widget wrappers, and then FancyMenu foreground elements.

## Element Instantiation
- `Layout.buildElementInstances()` deserializes each `SerializedElement` into concrete `AbstractElement` implementations, attaching them to the parent layout and routing them to background or foreground buckets.
- `ElementFactory.constructElementInstances()` merges elements from all contributing layouts, stacks vanilla button overrides so only one customization drives each widget, and generates defaults for untouched vanilla buttons.
- Vanilla overrides mirror widget geometry when anchored to `VANILLA`, ensuring replacement textures and hit boxes stay in sync with the underlying Minecraft widget.
- Background builders subclass `MenuBackground` and receive lifecycle callbacks (open, close, resize, render) from the active layer, with opacity and aspect ratio supplied by the stacked `LayoutBase`.
- Layout editor interactions reuse the same serialization pipeline: editor elements are wrapped, manipulated, and written back into `serializedElements`/`serializedVanillaButtonElements` before saving.

## Layout State Management
- Each layout keeps a `runtimeLayoutIdentifier` for in-session identification and caching. `LayoutHandler.isLayoutLoaded()` uses this to validate cached random group picks.
- Persistence delegates to `Layout.saveToFileIfPossible()` and ultimately `LayoutHandler.saveLayoutToFile()`, which simply rewrites the serialized property set back into the `.txt` file.
- Enable/disable state toggles the `enabled` flag in metadata and can force a live screen re-init. The `/fmlayout` command sends enable/disable packets to clients to flip this state.
- Legacy compatibility is handled automatically: `.disabled` directories are migrated into the main customization folder with the `enabled` flag cleared, and legacy element definitions are converted when deserialized.

## Related Configuration Hooks
- Universal layout behaviour can be customized by registering `UniversalLayoutInclusionRule` instances, which can veto applying universal layouts to specific identifiers at runtime.
- The layer only customizes screens that remain enabled in `customizablemenus.txt` and after the initial resource reload has completed. `ScreenCustomizationLayer.shouldCustomize()` enforces both conditions, plus identifier matching, before spending work on any screen.
- Users can toggle entire classes through the customization file or via API helpers; writes always use classpath identifiers to keep universal mappings predictable.

## Key Takeaways for Extenders
1. Treat layout files as authoritative state. Any tooling that edits layouts should round-trip through the same property container structure to stay compatible with `Layout.serialize()` / `Layout.deserialize()`.
2. When adding new element or background types, register builders during FancyMenu initialization so the loader can materialize them when reading existing layouts.
3. Respect runtime guards such as loading requirements and `customizablemenus.txt`; bypassing them will desynchronize FancyMenu's caches from the UI layer and may trigger forced reinitializations.
