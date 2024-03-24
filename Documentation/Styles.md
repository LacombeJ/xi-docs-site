---
title: Styles
layout: page
parent: Documentation
---

# Styles

The `--xi-transition` uss property is a custom property used to animate custom xi properties. By default, Unity UITK does not animate custom properties so this needs to be handled within XI.

__Note:__ The value is a string surronded by quotes although it follows the same syntax as the normal `transition` property
```css
--xi-transition: "0.3s --xi-depth, 0.3s --xi-color-emission, 0.3s --xi-border-emission";
```

Other:
- Border radius percentages is not supported (unable to determine if float value is percentage or pixels with UITK api)
