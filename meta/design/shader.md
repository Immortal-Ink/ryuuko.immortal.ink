---
title: Shader Design Initial Planning
description: 
published: true
date: 2024-04-17T15:13:28.016Z
tags: 
editor: markdown
dateCreated: 2024-04-13T14:17:20.020Z
---

Ideally the shader is integrated into the self lighting utility:

![image-43.png](/meta/design/shader/image-43.png =900x)

where every object we want to light and shade, we slap on the shader network and configure lighting direction and detaisl, customize the settings as detailed below for style, and then the object is lit and shaded for the scene and camera angle of the stills we intend to render.

the shader overall intends to make 3d models have a drawn 2d appearance similar to the art below.

Desired Setings:
Light Source
This setting lets your light source settings either keey their set orientation in relation to the world, or always are offset by their configured amount from the camera view. This is useful for example if I want backlight to always be behind the characters being looked at, even if the camera moves around a little. While not realistic, this has use in designing stills for impact, and speed of use in those scenarios.

Light Sources
Each of the three can be enabled or disabled, and their orientation, color, and strength can be set. The orientation can default to a triangle around the subject, and even might not need orientiation configuration on an individual source basis, and instead only the orientation fo the triangle of lights is configurable.
- Key
- Fill
- Back

Style Shaders
Each of these options enable or disable the way textures are applied to the model based on the directions of the light sources
When any of these layers are enabled, their strength, fall off, and texture type should be customizeable.

- Highlights
Thin strips where the underlying color of the model is lightened and one of two textures applied where light creates sheen, such as direct high strength fill light, and back light.
- Soft Shadow
Soft shadows are large, and fall off slowly
- Hard Shadow
Hard shadows are more exact, and fall off quickly or immediatly.
- Cell shading
cell shading and some configuration for that such as weight and intensity.

Possible Textures as options:
- Solid
Creates the shadow as a flat mask that darkens the color it overlays, and can gradient alpha to 100% for fall off at some level
- Screenspace
A texture is overlayed the mask, the texture is repeated and aligns with the camera view. one or two textures are desired, dot grid, and diagonal lines.

Perhaps a possibility of coloring the shadow based on the color of the light source configuration.

## Examples of Solid Texture:
In these examples, there is different levels of falloff and amount in which the shadow darkens the underlying color, which could be an inverse? of the brightness of the light source setting casting the shadow.

![solid1.webp](/meta/design/shader/solid1.webp =900x)
![solid2.webp](/meta/design/shader/solid2.webp =900x)

---

## Examples of Screenspace Texture:
In these examples there is a variety of textures used, but all align with the camera view.

![screenspace1.webp](/meta/design/shader/screenspace1.webp =900x)
![screenspace2.webp](/meta/design/shader/screenspace2.webp =900x)
![screenspace3.webp](/meta/design/shader/screenspace3.webp =900x)
![screenspace4.webp](/meta/design/shader/screenspace4.webp =900x)
![screenspace5.webp](/meta/design/shader/screenspace5.webp =900x)