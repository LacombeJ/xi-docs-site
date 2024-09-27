---
title: FAQs & Issues
layout: page
nav_order: 9
---

# FAQs & Issues

## Nothing Rendering
- If using URP, make sure XI_URP preprocessor define has been added
- Try adding "XI Render Feature" to URP asset
- Make sure the XIDocument has the Manager field set to a Manager in scene
- If using Shapes adding "Shapes Render Feature" to URP asset

## Background Rect is not rendering
- If the background color / border is not rendering but text and icons are, check the XI Standard Renderer component to see if the "Rect Material" is applied 

## Overflow is not being clipped
- Check if the "Use Clip" flag in the standard renderer config is enabled and if a functioning clip material is assigned

## Incorrect height / layout sizes
- Try adding UnityDefaultRuntimeTheme to panel settings

## Text is not visible
- Check if the text meshes are being rendered by viewing the scene in wireframe mode or looking at the "Frame Debugger" for the draw calls
- If the proper draw calls are being made: Try making sure TMP font asset being used is rendering properly. If the asset has been accidently modified it might not display properly. Reimport the TMP essentials if necessary. 
- If this issue is happening only with the Shapes renderer, try following setup for Shapes Renderer involving modifying Shapes source (IMDrawer.cs)

## Text Layout is not Accurate
- If "\n" is typed under text field in UI builder, this may render as new line in UI Builder but in XI it will be displayed as a literal. This can result in a string that is clipped starting from the first "\n"
  - Solution: Convert "\n" characters to actual newlines in UI Builder. Or in the UXML, convert the "\n" strings to `&#10;`

## Unresponsiveness after Style Reload while in Editor Play Mode 
- Known Issue: Stylesheet reload can cause a loss of interactibility when stylesheet is modified during editor play mode. Unknown cause

## Missing References to Demo Icon Textures
- Make sure Unity VectorGraphics package is installed
  - Version used in development:
    ```json
    {
      "com.unity.vectorgraphics": "2.0.0-preview.24"
    }
    ```

## Invalid Image Specified Warning
- This warning message can be seen with Vector Images in UI Builder even if they have the proper references. Not sure if this is a Unity bug but after some combination of reassigning images in UI builder, saving, closing, and reopening again, this error went away.

## Textures are blurry
- Try to enable "Anisotropic Textures" by setting `Project Settings > Quality > Rendering > Textures > Anisotropic Textures` to `Forced On`
