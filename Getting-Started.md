---
title: Getting Started
layout: page
nav_order: 1
---

# Getting Started

## Requirements
- Shader Graph
- "com.unity.render-pipelines.core": "14.0.9"

### Optional / Recommended
- "com.unity.vectorgraphics": "2.0.0-preview.24" (some samples use SVG icons)

## Setup

- Import TextMeshPro essentials
  - `Window > TextMeshPro > Import TMP Essential Resources`

### Rendering Pipelines

{: .note }
> URP & HDRP require scripting define symbols to be added.
  You can find the configuration here: `Project Settings > Player > Other Settings > Script Compilation`

#### Built-In
- No setup required

#### URP
- Add `XI_URP` scripting define symbol
- Configure URP asset to include `XI Render Feature`
- Configure URP to enable Depth and Opaque textures

#### HDRP
- Add `XI_HDRP` scripting define symbol

### Scene Preparation

#### Quick Start
- Import the `Demo` sample found in `Package Manager > XI Framework > Samples > Demo`
- Open `Assets > Samples > XI Framework > X.X.X > Demo > Demo Scene.unity`
- 3D UI should be rendered and interactible on play if the above steps were followed

#### Manual Setup
- Add XI Manager to the scene
- Add XI Standard Renderer to the scene's XI Manager
- Add UI Document for any document you want in the scene
- Add the `XI Pixel Panel` panel settings to each added UI Document
- Attach UXML documents under "Source Asset" in each UI Document component
- Add XI Document component to each UI Document gameobject and set the Manager to the scenes XI Manager

{: .note }
> You can also create your own panel asset and set the following:
  - Scale Mode = Constant Pixel Size
  - Theme Style Sheet = `XI DefaultRuntimeTheme` (preferred)

### Optional Configuration

{: .note }
> As of version 1.3.0, configuration assets are optional. Default settings will be used when configurations are not provided.

- `Create > XI > XI Configuration` asset and add the asset to the `XI Manager` in the scene
- `Create > XI > XI Render Config` asset and add the asset to the `XI Standard Renderer` in the scene

### Setup (XI Shapes Renderer)

If using Shapes renderer alternative instead of Standard XI renderer:
- Add "Shapes Render Feature" to Universal Renderer Data
- Make the following changes to IMDrawer.cs (Shapes Asset)
  - Uncomment this line
    ```cs
    ApplyGlobalPropertiesTMP( sourceMat ); // I can't really edit this because *groans*
    ```
  - Add this line in the beggining of ApplyGlobalPropertiesTMP
    ```cs
    m.SetFloat( ShapesMaterialUtils.propZTest, (float)Draw.ZTest );
    ```
- (Optional) Enable `HDR color pickers` in Shape Settings
- Add XI Shapes Renderer to the scene's XI Manager

### Setup (Scripting and Assembly)

- If using assembly (.asmdef), add Tobia.XI reference to the reference list to access the XI namespace.
- The namespace XI.Renderer should not need to be used, but this can be included by adding Tobia.XI.Renderer.

{: .note }
> If looking at the JSON source for Tobia.XI.Renderer.asmdef, you may notice I include
  the names for RenderPipeline references instead of the GUID. This is because these
  assemblies may be missing depending on which render pipeline is chosen. So having
  names makes it readable in the inspector (since names will appear instead as GUIDs
  for missing asmdefs)
