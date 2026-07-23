---
title: Fix Audio Files
description: Troubleshoot audio files that FancyMenu cannot play.
published: true
date: 2025-04-14T20:14:47.283Z
tags: wav, ogg, audio
editor: markdown
dateCreated: 2025-04-14T20:14:44.259Z
---

# Fixing Audio Files

If an audio file plays elsewhere but not in FancyMenu, re-encode it as OGG or PCM WAV. For WAV, try 48 kHz, 16-bit audio.

You can use FFmpeg or another trusted audio converter. Re-encoding is useful even when the current file extension and reported settings already look correct.

# Checks

- Confirm that the re-encoded file plays in another audio player.
- Keep very large audio files out of memory-sensitive screens.
- Verify the sound channel selected by the [Audio element](./elements#audio) or action.
- Check Minecraft's Master volume and the selected channel's volume.
- If audio still fails, test without other mods that replace or process Minecraft audio.
