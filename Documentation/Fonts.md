---
title: Fonts
layout: page
parent: Documentation
---

# Fonts

For Open source fonts free to use in commerical sites, visit the collection at [https://developers.google.com/fonts](https://developers.google.com/fonts/faq).

It is recommended to download fonts externally instead of using TextMeshPro provided fonts to get a wider variety of font-weights.

Here are some of my favorite fonts (found in Google Fonts):
- Noto Sans
- Noto Sans Mono
- Roboto
- Open Sans
- Urbanist

## Adding Fonts to Unity Project

{: .note}
> Special thanks to "Christina Creates Games" for the youtube tutorial here: "https://www.youtube.com/watch?v=Xa7kcapGRDI&t=1s"

At the time of writing this, TMP does not seem to support "Variable" fonts. Variable fonts are font files under one ttf which can have axes (variables) that can be modified to adjust font weight and other styling. So you have to add each TTF for each font weight. From what I've seen, this is included in the download under the "static/" folder. In other cases, it may be possible to use some other software to create static fonts from variable fonts.

1. Find the fonts that you wish to include

2. Add .ttf files to assets and include any required licenses
    - Optional: Organize using the following structure as an example:
        - Assets/Fonts/Noto
            - NotoSans-Regular.ttf
            - NotoSans-Italic.ttf
            - NotoSans-Thin.ttf
            - NotoSans-ThinItalic
            - NotoSans-Black.ttf
            - NotoSans-BlackItalic.ttf
            - ... (others to include up to 9 weight variants, see below)
            - LICENSE.txt (if required)

3. Use [Font Asset Creator](https://docs.unity3d.com/Packages/com.unity.textmeshpro@4.0/manual/FontAssetsCreator.html) under `Windows > TextMeshPro > Font Asset Creator` to create an asset for each ttf
    - after each generation, remember to click __Save as...__
    - Use recommended settings (mostly copied from TMP provided LiberationSans):
        - Sampling Point Size: Custom Size (86)
        - Padding: 9
        - Packing Method: Optimum
        - Atlas Resolution: 1024 x 1024
        - Character Set: ASCII
        - Render Mode: "SDFAA_HINTED"

4. Navigate to the "regular" font asset variant (ex: NotoSans-Regular.asset) and add in all of the font weights made (for both regular and italics typeface).

{: .note }
> When using "Extended ASCII" as character set option, I noticed some characters missing, So I switched option to use ASCII. However, I've read you may be able to also set character set to manual and add manually.

## Font Weights

Although UITK does not yet[^1] support font weights, you can set font-weights in USS with the XI custom style: `--xi-font-weight`.

Example:
```css
.prop {
    --xi-font-weight: 200; /* ExtraLight */
}
```

If UITK ever decides to support the `font-weight`, this value will probably be deprecated.

### Font Weight Table

| Name | Weight |
| ------------- |
| Thin | 100 |
| Extra-Light | 200 | 
| Light | 300 |
| __Regular__ | __400__ |
| Medium | 500 |
| Semi-Bold | 600 |
| Bold | 700 |
| Heavy | 800 |
| Black | 900 |


## TextMeshPro Rich Text

You can render text with inline styles using tags.

```
This sentence has a <font-weight=100>thin</font-weight> word embedded within.
```

Read more about [rich text tags](https://docs.unity3d.com/Packages/com.unity.textmeshpro@4.0/manual/RichText.html) in the TMP documentation.

---

[^1]: I am not sure if Unity UI Toolkit plans to include this feature or not