---
title: Getting Started
layout: page
nav_order: 1
---

# Getting Started

## Requirements
- Universal Render Pipeline (URP)
- Shader Graph

## Setup
- Add XI asset package to project
- Add TextMeshPro package and import essentials
  - `Window > TextMeshPro > Import TMP Essential Resources`
- Add URP and ShaderGraph packages
- Configre URP asset to include `XI Render Feature`
- Add XI Manager to the scene
- Add XI Standard Renderer to the Scene
- Add UI Document for any document you want in the scene
- Add the `XI Pixel Panel` panel settings to each added UI Document
  - Or you could create your own panel settings with:
    - Scale Mode = Constant Pixel Size
    - Theme Style Sheet = UnityDefaultRuntimeTheme
- Add XI Document component to each UI Document gameobject

{: .note }
> You can create your own pixel panel as long as you set the following:
  - Scale Mode = Constant Pixel Size
  - Theme Style Sheet = UnityDefaultRuntimeTheme

## Setup (XI Shapes Renderer)

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
