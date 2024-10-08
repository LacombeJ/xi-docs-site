---
title: Icons
layout: page
parent: Documentation
---

# Icons

For free and open source SVG icons visit my favorite icon collection at [https://tabler.io/icons](https://tabler.io/icons).

The procedure of importing an SVG an including it in an XI document is straightforward.

1. Save an SVG icon in your assets.

2. Modify the SVG source to change any stroke (color) property from currentColor to "white". And (optionally) change the stroke-width to something you prefer.

```properties
stroke="white"
stroke-width="1"
```

3. Update SVG import settings and set:
   - __Generated Asset Type:__ Texture2D
   - __Wrap Mode:__ Clamp
   - __Texture Size:__ 512 (optional, better quality for large icons)

4. In a custom script referencing a document with the element you want to render the SVG in, add a serialized property field, query the element, and apply the SVG like below:

    ```cs
    public Texture MyIconTexture;

    void OnEnable()
    {
        var document = GetComponent<XIDocument>();
        var iconElement = document.Root.Q<XIElement>("icon-element-name");
        iconElement.Style.BackgroundImage.Texture = MyIconTexture;
    }
    ```

5. Set the texture property value in the inspector with the SVG asset

6. Enable "Anisotropic Textures" by setting `Project Settings > Quality > Rendering > Textures > Anisotropic Textures` to `Forced On`

{: .note }
> The VectorGraphics package apparently does not generate mipmaps for SVG images. I believe it is because these images are meant to be used in screen space where viewed at one distance. Because XI is intended to be used in 3D/VR, images can be viewed at various distances and perspectives. XI internally generates mipmaps for images that do not have mipmaps which can result in higher quality image rendering.
