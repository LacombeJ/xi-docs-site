---
title: Changelog
layout: page
nav_order: 7
---

# Changelog

## [1.1.0] - 2024-05-07

### Added

- XIMonitor window for debugging and monitoring
- Support for masked password fields
- Slider progress indicator
- XI Default Runtime Theme reference to XI Pixel Panel
- Updating of styles when adding / changing stylesheets of XI documents
- New demo examples
- XIHeading and XIParagraph elements
- Font asset cache
- Cascading / inheritable custom styles
- Support for unity font-style uss property (normal, bold, italic)
- Custom styles:
  - `--xi-text-decoration` for rendering underline and strike-through text
  - `--xi-font-family` for taking in a list of font names in order of fallback precendence
  - `--xi-background-image-emission` for applying emissions to background images
- Namespaces for all code in samples

### Fixed

- Performance issues with text rendering
- Performance issues with stencil clipping implementation
- Improve performance with reducing matrix calculations
- Null exception when disabling XI documents
- Gradient shader bug when changing the number of stops in the gradient of an element
- Rect material config reference is now valid
- HDRP shadergraph missing image filter
- Text layout/rendering stretching issues, text now renders accurately with UI Builder
- Text clipping issue with decorative text and alternate typefaces
- Concurrent modification error in XIRender when switching scenes/cameras

### Changed

- Improved demo sample
- Rename XI.hlsl to Rect.hlsl
- Renderer file organization
- Shader fill/solid shrink epsilon calculation
- XI Standard Renderer now expects user-created renderer config instead of the old individual properties
- Renderer config now takes a list of available font assets instead of one
- images using `-unity-background-image-tint-color` now use added style `--xi-background-image-emission` instead of `--xi-color-emission`
- Certain custom styles now cascade down to child elements
- XI Keyboard prefab now has "Stretch" document scale mode

### Removed

- Default render configuration from XI resources folder
- Old Demo sample

## [1.0.0] - 2024-04-28

### Added

- First release
