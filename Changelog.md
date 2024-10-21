---
title: Changelog
layout: page
nav_order: 8
---

# Changelog

## [1.4.0] - 2024-10-21

### Added
- Image and Video elements
- Additional properties to XISlider
- Remove element function
- Click dragging from tracker for XISlider
- XIVisual and XIBuilder to add additional visuals to document
- Border/corner sharp cut sdf shader

### Fixed
- Texture layout calculations
- Demo slider progress tracker
- Hierarchy mapping issues
- TextField value updating
- Border rendering visual artifact at certain angles

### Changed
- Refactor standard renderer
- Alignment property in XIDocument
- XI Render Feature asset guid

## [1.3.0] - 2024-09-26

### Added

- Mipmap texture generation, for smooth texture/SVG rendering at different 3D perspectives
- XIConsole element (experimental / in development)
- XIDropdown "Value" property getter/setter
- XILabel string text constructor
- XIElement `Remove` element method

### Fixed

- Performance optimizations with DepthSort
- Performance optimizations with standard renderer
  - Using structs instead of per-frame object allocations
  - Update caching and memory pooling
- Performance optimizations in animation updater
- ComputeTextDimensions issue introduced in Unity 6
- HDRP render feature
- TMP submesh / text rendering
- Font weight rendering
- Clip/stencil texture causing faded UI elements in VR/stereo

### Changed

- fwidth aliased factor, for smoother border rect rendering
- XIStyleSheet split into multiple different USS modules
- XI no longer requires configuration assets, will use default resource values if not provided
- XIManager now takes an optional XIConfiguration
- URP default RenderPassEvent changed to BeforeRenderingTransparents (for common VR use case)

## [1.2.1] - 2024-05-22

### Added

- Cursor display element
- Custom style:
  - `--xi-cursor-pass` for passing class from hovered elements to cursor/pointer display

### Fixed

- Asset is now installed as a package
- XIDocument modals are applied with the UXML embedded stylesheets from document root

### Changed

- Asset installation has been moved to "Packages"

## [1.2.0] - 2024-05-21

### Added

- XIDropdown additional constructor that accepts choice list
- Layout property getter for XIElement
- XIPanel to manage document attachment in XIManager
- Custom style:
  - `--xi-coloring` for choosing different color targets for source properties
- Stereo support macros in xi shaders
- Ability to change render pass event in config
- OnPointerMiss callback, useful for detecing when a pointer input hasn't hit a document

### Fixed

- Performance issues resolved with reducing GC allocations
- Performance issues with clipping update
- Performance issues with hierarchy update
- XIHeading and XIParagraph elements addeded to registry
- Stylesheet updater and inherited style propagation
  - This fixes weird text issues / glitches found when hovering over text fields (font seemed to change during hover)
- XIDocument updates when UIDocument visual tree asset is modified
- Null exception by checking for null materials on draw mesh calls
- UXML style source paths now point to local paths
- Issues with rendering XI document in VR/Quest/stereo environment
- Issues found in build
  - calling DirtyStyleSheets while not in editor
  - Profiler usage while non in editor

### Changed

- uint keys are used for style property logic, internally
- Structs are used in places of classes where reasonable
- Hierarchy update logic is more efficient
- XIDocument attachment logic with XIManager and XIPanel
- Background images are now handled with unity property 'background-image'
- Demo icons are no longer serialized properties in document manager but are set within uss

### Removed

- XIImage and foreground image property
- Keyboard SVG vector icons (Keyboard now contains Texture2D icons only)
- StencilScope class usage / allocations in render pass calls

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
