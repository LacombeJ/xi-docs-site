---
title: Getting Started
layout: page
nav_order: 1
---

# Getting Started

## Requirements
- Shader Graph
- "com.unity.render-pipelines.core": "14.0.9"

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
- Configre URP asset to include `XI Render Feature`

#### HDRP
- Add `XI_HDRP` scripting define symbol

### Scene Preparation
- Add XI Manager to the scene
- Add XI Standard Renderer to the scene's XI Manager
- Add UI Document for any document you want in the scene
- Add the `XI Pixel Panel` panel settings to each added UI Document
  - Or you could create your own panel settings with:
    - Scale Mode = Constant Pixel Size
    - Theme Style Sheet = UnityDefaultRuntimeTheme
- Attach UXML documents under "Source Asset" in each UI Document component
- Add XI Document component to each UI Document gameobject and set the Manager to the scenes XI Manager

{: .note }
> You can create your own panel asset and set the following:
  - Scale Mode = Constant Pixel Size
  - Theme Style Sheet = UnityDefaultRuntimeTheme

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
