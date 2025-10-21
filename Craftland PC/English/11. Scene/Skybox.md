# Skybox

# Introduction

In the game's Hierarchy menu, you will find a Skybox object.

![image-20250106145115975](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/42-Skybox/image-20250106145115975.png)

It is the default skybox visible in the scene, and you cannot delete or rename this object. However, through its Inspector, you can modify settings related to the skybox template, lighting, and fog effects.

![image-20250106145447868](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/42-Skybox/image-20250106145447868.png)

> Skybox Inspector

# Skybox

## Skybox Template

![image-20250106150927792](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/42-Skybox/image-20250106150927792.png)

We have provided several skybox templates for you, and you can make further adjustments based on the parameters of these templates. However, the parameters of the templates are fixed, and if you modify any configuration, the skybox type will automatically change to "Custom."

![image-20250106163715369](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/42-Skybox/image-20250106163715369.png)

## Configuration Details

| Configuration Item | Description                                                |
| ------------------ | ---------------------------------------------------------- |
| **Lighting Color**  | The color of the directional light source.                 |
| **Lighting Intensity** | The intensity of the directional light source, with a range of (0,4], where a higher value means stronger lighting. |
| **Darkness**        | The darkness of surfaces directly illuminated by the directional light source, with a range of [0,1], where a higher value means the surface is darker. |
| **Shadow Intensity** | The darkness of the shadows cast on other surfaces after being blocked by the directional light source, with a range of [0,1]. A higher value means the shadow is darker, and a value of 0 means no shadow is visible. |
| **Ground Wetness**  | The highlight effect on the ground; higher values result in stronger highlights. This effect is not currently supported. |
| **Lens Flare**      | The lens effect when looking directly at the sun (directional light source). A higher value results in a stronger lens flare effect. This effect is not currently supported. |
| **Ambient Light Color** | Ambient light is a type of non-directional light that simulates the basic light amount received by scene objects when no direct light source is illuminating them. This parameter adjusts the color of ambient light. |

The skybox is also a global module property, and you can dynamically modify these parameters by accessing the global skybox.

![image-20250107191709360](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/42-Skybox/image-20250107191709360.png)

## Modifying the Directional Light Source Rotation

Double-click the Skybox in the Hierarchy to locate the scene object used to simulate the directional light source. You can also view its Transform component in the Inspector.

![image-20250106181621443](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/42-Skybox/image-20250106181621443.png)

The directional light source illuminates the scene in a way similar to how the sun illuminates the Earth. The directional light source is infinitely far from the scene, and modifying its Transform rotation is equivalent to adjusting the angle at which the light hits the scene. This scene object is only used for conveniently adjusting the directional light source's rotation, and modifying its position will have no actual effect.

# Fog Effects

Fog effects add color to objects based on their distance from the **camera**. This effect is similar to real-world fog, and you can use it to simulate fog or hide objects beyond the camera's far clipping plane.

![image-20250106183514572](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/42-Skybox/image-20250106183514572.png)

## Fog Effect Settings

| Configuration Item    | Description                                                |
| --------------------- | ---------------------------------------------------------- |
| **Fog Color**          | The color of the fog, including transparency.              |
| **Fog Start Distance** | Objects within the "Fog Start Distance" from the camera will be covered with fog at a transparency of 0, which gradually increases to the configured transparency as the distance from the camera increases. |
| **Fog End Distance**   | Objects at the "Fog End Distance" or further from the camera will be fully covered in fog, with transparency equal to the configured fog color transparency. |

## Fog Effect Example

We place three cubes in the scene, spaced 5m apart along the X-axis.

![image-20250106184039329](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/42-Skybox/image-20250106184039329.png)

We set the fog effect to start at 5m and reach its thickest at 10m, with the default color.

![image-20250106184212648](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/42-Skybox/image-20250106184212648.png)

This means that at 5m from the camera, the fog starts to take effect and becomes thicker as the distance increases, reaching its thickest at 10m.

Assuming the first cube is at (0,0,0) and a camera is placed at (-5,1,0), you will see:

![image-20250106184940077](https://dl.dir.freefiremobile.com/common/OB46/CSH/OfficialWeb/42-Skybox/image-20250106184940077.png)

You will see fog starting to appear at the first cube and becoming the thickest at the second cube.
