---
title: Toggle Parts of Layouts
description: How to toggle parts of layouts on user input.
published: true
date: 2024-02-26T05:15:29.222Z
tags: 
editor: markdown
dateCreated: 2024-02-26T05:08:33.154Z
---

# Toggle Parts of Layouts

Sometimes it's good to have the choice! Maybe some of your users don't like constantly hearing Rick Astley as menu music or want a different cute anime girl as menu background.

Well, that's no problem! You can make it so your users can toggle on/off parts of your layouts or cycle through multiple versions of said parts.

# Toggle On/Off

To toggle, for example, the visibility of an element by clicking a button, you just need to use a variable that gets set on button click and the element you want to toggle needs to check in its loading requirements if said variable has the correct value.

## The Element

First lets add the element you want to toggle on/off.

<br>
<img width="270" alt="Screenshot_3" src="https://gist.github.com/assets/35544624/317460fc-310b-4941-ab9a-b56490c5ebb9">

Now right-click the element and click on **Loading Requirements**.
This will open the Manage Requirements screen. Click on **Add Requirement**.

Search for the **Is Variable Value** requirement, select it and click on **Edit Requirement Value**.

<br>
<img width="501" alt="Screenshot_1" src="https://gist.github.com/assets/35544624/d0d342f5-617c-415e-b6f7-05087fc204b7">

Now choose a **unique** name for your variable and let the requirement check for `true` as value.
Make sure the variable name is really **unique** and is not already used elsewhere.

<br>
<img width="500" alt="Screenshot_2" src="https://gist.github.com/assets/35544624/a1f356e9-7f96-4d8b-87b0-51f05898409a">

That's it for that part. Now your element will be visible when the variable's value is `true`.
Keep in mind that it will not show by default, because the variable value is empty at the moment. We will fix this later.

## The Button

Now we need to add a new Button element.

<br>
<img width="270" alt="Screenshot_4" src="https://gist.github.com/assets/35544624/1bd1b781-0cdb-4b52-80a0-db8f44ead0db">

After adding, right-click it and click on **Edit Action Script**.
This will open the button's Manage Action Script screen.




