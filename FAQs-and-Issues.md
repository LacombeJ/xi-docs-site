---
title: FAQs & Issues
layout: page
nav_order: 8
---

# FAQs & Issues

## Nothing Rendering
- Try adding "XI Render Feature" to URP asset
- If using Shapes adding "Shapes Render Feature" to URP asset

## Incorrect height / layout sizes
- Try adding UnityDefaultRuntimeTheme to panel settings

## Text is not visible
- Check if the text meshes are being rendered by viewing the scene in wireframe mode or looking at the "Frame Debugger" for the draw calls
- If the proper draw calls are being made: Try making sure TMP font asset being used is rendering properly. If the asset has been accidently modified it might not display properly. Reimport the TMP essentials if necessary. 
- If this issue is happening only with the Shapes renderer, try following setup for Shapes Renderer involving modifying Shapes source (IMDrawer.cs)

## Text Layout is not Accurate
- Known Issue: TMP text rendering in XI does not exactly match UITK and because of inaccurate size calculations, some text may be clipped
- If "\n" is typed under text field in UI builder, this may render as new line in UI Builder but in XI it will be displayed as a literal. This can result in a string that is clipped starting from the first "\n"
  - Solution: Convert "\n" characters to actual newlines in UI Builder. Or in the UXML, convert the "\n" strings to `&#10;`
