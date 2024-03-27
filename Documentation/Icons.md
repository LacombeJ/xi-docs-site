---
title: Icons
layout: page
parent: Documentation
---

# Icons

For free and open source SVG icons visit my favorite icon collection at [https://tabler.io/icons](https://tabler.io/icons).

The procedure of importing an SVG an including it in an XI document is straightforward.

1. If not added already, add the Unity VectorGraphics package to your project.

2. Save an SVG icon in your assets.

3. Modify the SVG source to change any stroke (color) property from currentColor to "white". And (optionally) change the stroke-width to something you prefer.

```properties
stroke="white"
stroke-width="1"
```

4. Update SVG import settings and set:
   - __Generated Asset Type:__ Texture2D
   - __Wrap Mode:__ Clamp

5. In a custom script referencing a document with the element you want to render the SVG in, add a serialized property field, query the element, and apply the SVG like below:

```cs
public Texture MyIconTexture;

void OnEnable()
{
    var document = GetComponent<XIDocument>();
    var iconElement = document.Root.Q<XIElement>("icon-element-name");
    iconElement.Style.BackgroundImage.Texture = MyIconTexture;
}
```

6. Set the texture property value in the inspector with the SVG asset
