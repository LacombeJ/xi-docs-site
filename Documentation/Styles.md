---
title: Styles
layout: page
parent: Documentation
---

# Styles

## Stylesheets

### Themes
A good practice to follow is to separate theme specific values in separate `.uss` files. I found this preferable than using `.tss` files only because it seems that `.tss` files do not reload in editor upon saving. The benefit of using `.tss` files is
that you can preview documents in UI Builder under different themes.

For example:

DarkTheme.uss
```css
:root {
    --theme-color: white;
    --theme-background: black;
}
```

LightTheme.uss
```css
:root {
    --theme-color: black;
    --theme-background: white;
}
```

Page.uss
```css
.app {
    color: var(--theme-color);
    background-color: var(--theme-background);
}
```

With this you can dynamically add DarkTheme or LightTheme to the XIDocument stylesheets list depending on which theme is selected.

## Properties

### XI Depth
Value (in pixels) that determines how much an element is "pushed" in. To "pop" an element out in front of its parent, assign a negative depth value.
```css
--xi-depth: -4;
```

### XI Z Index
Similar to html/css index. Determines rendering order (only for elements of the same depth).
```css
--xi-z-index: 10;
```

### XI Emissions
Emission values that can be applied to individual colors for emissive glow effect. Value of `0.0` applies no change to color, while a value of `1.0` will multiply the color by 2. Bloom needs to be enabled in project / scene for this to work.
```css
--xi-color-emission: 1.0;
--xi-background-emission: 0.5;
--xi-border-emission: 1.5;
--xi-background-image-emission: 0;
```

### XI Image Rotation and Scale
Rotation and scale values for background images. 
```css
--xi-background-image-rotation: 30;
--xi-background-image-scale: 0.5;
```

### XI Font Weight
Similar to html/css font-weight properties. This range from 100 (thinner fonts) to 900 (bolder) fonts.  This only works when font-weights are set on the active TMP font asset. See [Fonts](docs/Documentation/Fonts) for more.
```css
--xi-font-weight: 100;
```

### XI Text Decoration
Similar to html/css text-decoration-line. Used to render underline and strike-through / line-through text.
```css
--xi-text-decoration: line-through;
--xi-text-decoration: underline;
```

### XI Font Family
Similar to html/css font-family. Used to set fonts based on names. This property takes a list of names in order of fallback precedence. The first font will be preferred if it exists.
```css
--xi-font-family: 'Noto Sans', 'Liberation Sans';
```

### XI Background
You can find really nice web gradients with the following site:
- https://cssgradient.io/gradient-backgrounds/

Similar to html/css background-image. This value can be used to render gradients with an optional rotational parameter and color space paramter.

```css
--xi-background: linear-gradient(red, blue);
--xi-background: linear-gradient(149deg, #00DBDE 0%, #FC00FF 100%);
--xi-background: linear-gradient(149deg, #00DBDE 0%, red 50%, #FC00FF 100%);
--xi-background: linear-gradient(30deg in hsl, red, blue); /* This interpolates in HSL space*/
```

### XI Coloring
This is used to set color targets for different sources. For example, instead of coloring background images with `-unity-background-image-tint-color`, you can define this property to use the text/font `color` property instead.
```css
--xi-coloring: background-image color;
```

### XI Cursor Pass
This is used to pass classes from hovered elements to cursor/pointer display. The display must be enabled under XIManager and after you can style like so:
```css
Button {
    --xi-cursor-pass: cursor-hovering-button; /* choose any class name */
}

.xi-cursor {
    transition: 0.3s border-color, 0.15s width, 0.15s height, 0.15s translate, 0.15s border-width;
}

/* use the chosen class name here */
.xi-cursor.cursor-hovering-button {
    border-color: rgba(0, 128, 255, 1.0);
    width: 4px;
    height: 4px;
    translate: -2px -2px;
    border-width: 2px;
}
```
In the example above, the class name `cursor-hovering-button` is chosen to be applied to the cursor when it is hovering over a button. 

### XI Transition
The `--xi-transition` uss property is a custom property used to animate custom xi properties. By default, Unity UITK does not animate custom properties so this needs to be handled within XI.

__Note:__ The value is a string surronded by quotes although it follows the same syntax as the normal `transition` property
```css
--xi-transition: "0.3s --xi-depth, 0.3s --xi-color-emission, 0.3s --xi-border-emission";
```

### Other
- Border radius percentages is not supported (ATM, unable to determine if float value is percentage or pixels with UITK api)


## Custom Code-Only / Non-USS Properties
These properties can only be set and modified via code (not available with uss).

- BackgroundFilter: Texture that applies a masking/filter over the rendered rect background color (or gradient)
- Visual: A collection of properties used for custom rendering

## Pseudo States

Support for pseudo states in XI:
- [x] `:hover` - for elements with cursor hovering
- [x] `:active` - for active (pushed) elements
- [x] `:focus` - for focused elements
- [x] `:disabled` - for disabled elements
- [x] `:checked` - for checkable elements that are 'checked' (toggle, radiobutton)
- [ ] `:root` - *not yet supported in XI*[^1]
- [ ] `:not` - *not supported by UITK*[^2]

[^1]: The `:root` pseudo class applies to top level documents but for some reason this value isn't being applied in UITK when set in XI.
[^2]: Because UITK does not support the `:not` pseudostate in USS, it cannot be used in XI. This state is commonly used in HTML/CSS web applications and is useful for styling the negation of other classes or pseudo classes.
