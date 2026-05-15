---
title: 切换布局的部分内容
description: 如何根据用户输入切换布局中的部分内容。
---

# 切换布局的部分内容

有时候，能让用户自己选择是件好事！也许有些用户不喜欢一直听 Rick Astley 作为菜单音乐，或者想把菜单背景换成别的可爱动漫女孩。

没问题！你可以让用户开启/关闭布局中的某些部分，或者在这些部分的多个版本之间循环切换。

# 开启/关闭切换

例如，要通过点击按钮来切换某个元素的可见性，你只需要使用一个在按钮点击时被设置的变量，而你想切换的元素则需要在其加载条件中检查该变量是否具有正确的值。

## 变量

第一步是创建一个变量，用来存储你想切换的元素的可见性状态。

要添加新变量，请在菜单栏中进入 **Customization** 选项卡，然后点击 **Variables -> Manage Variables**，接着添加一个**唯一**名称的新变量！请务必使用一个真正**独一无二**、尚未被使用过的名称。

创建变量后，将其值设置为 `true`。

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/1e29be13-e601-4669-8fa2-d78db945b07f">

## 元素

下一步是添加你想要开启/关闭切换的元素。

<br>
<img width="270" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/317460fc-310b-4941-ab9a-b56490c5ebb9">

现在右键单击该元素，并点击 **Loading Requirements**。
这会打开 Manage Requirements 界面。点击 **Add Requirement**。

搜索 **Is Variable Value** 这一条件，选中它，然后点击 **Edit Requirement Value**。

<br>
<img width="501" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/d0d342f5-617c-415e-b6f7-05087fc204b7">

现在输入你之前创建的变量名称，并让该条件检查值是否为 `true`。

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

这部分就完成了。现在当变量值为 `true` 时，你的元素就会显示。

## 按钮

现在我们需要添加一个新的 Button 元素。

<br>
<img width="270" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/1bd1b781-0cdb-4b52-80a0-db8f44ead0db">

添加完成后，右键单击它并点击 **Edit Action Script**。
这会打开按钮的 Manage Action Script 界面。

点击 **Add IF Statement**，为其添加 **Is Variable Value** 条件，并将该条件的模式设置为 **OPPOSITE**。

<br>
<img width="520" alt="Screenshot_5" src="https://gist.github.com/assets/35544624/a024ea21-2244-4ca6-b44b-1a80f7936b8f">

现在点击 **Edit Requirement Value**，和前面给元素设置时一样，只需输入完全相同的变量名称和值进行检查。

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

因为我们把条件模式设置成了 **OPPOSITE**，所以它现在会检查变量值是否**不是** `true`，这正是我们想要的。

回到 Edit Action Script 界面后，你现在会看到刚刚添加的 IF 语句。

<br>
<img width="495" alt="Screenshot_6" src="https://gist.github.com/assets/35544624/6ac8444c-ca15-43ff-a633-df63e76e7433">

现在点击 **Add Action**，搜索 **Set Variable Value** 动作，选中它，然后点击 **Edit Action Value**。

<br>
<img width="494" alt="Screenshot_7" src="https://gist.github.com/assets/35544624/8568e539-b4d0-49bd-89c4-4659ee71754c">

作为动作值，先输入你的变量名，再输入你想设置的值。名称和值之间用 `:` 分隔。
在这里我们希望把值设为 `true`，因为这个动作之后会在值**不是** `true` 时执行。

<br>
<img width="496" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/fab440ad-b335-4751-9651-4bb0b65bc968">

现在把这个动作拖到 IF 语句上并放上去，将它附加到 IF 语句中，这样它就只会在变量值**不是** `true` 时执行。

<br>
<img width="496" alt="Screenshot_8" src="https://gist.github.com/assets/35544624/d1ac3ea9-44d7-4ad6-a4b2-455b21f6d1c4">

完成后，选中 IF 语句，然后点击 **Append ELSE Statement**。

现在再添加一个 **Set Variable Value** 动作，但这次不要把变量值设为 `true`，而是设为 `false`。

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/d05400dc-b9b7-4c1a-8657-9e34939ed599">

然后把第二个动作附加到 ELSE 语句上，这样当变量值是 `true` 时它就会执行。

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/3191a1cc-c5c2-4cf1-a620-23bdbe639bf2">

就这样！第一次做时步骤看起来很多，但一旦熟悉之后，其实非常简单也很快。

现在你可以保存布局，离开编辑器，然后按下按钮看看是否生效！

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/e9a87aca-ba0f-4ce6-a39e-1e1d3796c9e3">

你也可以把同一个变量用于其他元素，这样按下按钮时就能**一次切换多个元素**。

你甚至可以通过使用 **Layout-Wide Loading Requirements** 来切换整个布局。要配置全局布局条件，只需右键单击编辑器背景。只要确保把按钮放到另一个布局里，而不是你想要切换的那个布局里。

# 循环切换

与在两个值之间切换不同，值的循环切换需要动作脚本能够在两个以上的值之间轮转。

这个动作脚本的逻辑和切换时非常相似，所以这里我就简要说明一下。请务必也阅读前面关于切换的部分。

我添加了 3 张图片。当变量值为 `1` 时第一张图片可见，值为 `2` 时第二张可见，值为 `3` 时第三张可见。

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/731c13cf-6f81-470b-8e1b-cba264ffbe05">

然后我添加了循环按钮，让变量值按 `1` → `2` → `3` → `1` 的顺序循环。

<br>
<img width="609" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/9f2052b1-8d3d-4a35-884a-4a234e63d5e5">

就是这样。现在保存布局，离开编辑器，检查循环按钮是否正常工作。

<br>
<img width="494" alt="Screenshot_9" src="https://gist.github.com/assets/35544624/430c2369-a43f-4d0f-9203-3fdb1b9eae2c">
