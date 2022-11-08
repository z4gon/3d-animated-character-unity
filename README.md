# 3D Animated Character in Unity/Blender

Modelled, Textured and Animated in Blender, later setup in **Unity 2021.3.10f1**

## Screenshots

### References

- [How To Make A 3D Character For Your Game](https://www.youtube.com/watch?v=ogz-3r0EHKM)
- [Baking a Normal Map](https://www.youtube.com/watch?v=tndUB5b4STI)
- [Baking Normals Low/High Poly](https://www.reddit.com/r/learnblender/comments/gbgvla/does_having_the_high_poly_object_being_completely/)
- [Blender/Unity Smooth Shading Compatibility](https://www.reddit.com/r/Unity3D/comments/47lska/just_found_out_that_blenders_smooth_shading_will/)
- [3D Scifi Kit Starter Kit](https://assetstore.unity.com/packages/3d/environments/3d-scifi-kit-starter-kit-92152)
- [Ambient Occlusion in Blender](https://docs.blender.org/manual/en/2.79/render/blender_render/world/ambient_occlusion.html)
- [Adding Vertices to Vertex Groups](https://blender.stackexchange.com/questions/183463/how-do-i-fix-vertices-that-arent-following-the-armature)
- [Inverse Kinematics - Blender 2.80 Fundamentals](https://www.youtube.com/watch?v=S-2v_CKmVE8)

## Table of Content

- [3D Modelling](#3d-modelling)
- [Normal Mapping](#normal-mapping)
- [Texturing](#texturing)
- [Importing model into Unity](#importing-model-into-unity)
- [Rigging](#rigging)
- [Animation](#animation)
- [Inverse Kinematics](#inverse-kinematics)
- [Importing animations into Unity](#importing-animations-into-unity)
- [3rd Person Character Controller](#3d-person-character-controller)

## Implementation

### 3D Modelling

- Design the character in a design software like Affinity.

![Picture](./docs/1.jpg)

- Model a low poly version.

![Picture](./docs/2.jpg)
![Picture](./docs/3.jpg)

- Subdivide and add more details, to generate a high resolution version.

![Picture](./docs/4.jpg)

- UV Map the high resolution version using Seams.

![Picture](./docs/5.jpg)

- Decimate to get a low poly again, with aligned UVs.

![Picture](./docs/6.jpg)

- Use Subdivision Catmul-Clark to get an Ultra HD to bake normals.

![Picture](./docs/7.jpg)

### Normal Mapping

- Set Smooth Shading to both the low poly and high poly models.
- Modify the models as needed to minimize meshes being too close together (like shoulders).

![Picture](./docs/8.jpg)

- Be sure both models are superposed, bake the normals making sure the extrusion is set to minimum, and the max ray distance is 0.

![Picture](./docs/9.jpg)

### Texturing

- Texture the low poly model while using the normal map.

![Picture](./docs/10.jpg)

### Importing model into Unity

- Import in Unity as FBX, without calculating smoothness for normals, just import the normals interpolation from the fbx.

![Picture](./docs/11.jpg)

- Setup a scene with a skybox and tweak the lighting to emulate the looks from Blender.

![Picture](./docs/12.jpg)

- Setup an emissive texture for the glowing parts of the suit.

![Picture](./docs/13.jpg)

### Rigging

- Create an Armature, starting from the base of the spine.
- Use Subdivision to split a bone in two connected bones.
- Use extrusion to grow a branch bone.
- Parent bones with offset to make them nested but not connected.
- Name bones `Leg.L` to be able to use `Symmetrize` to obtain a mirrored `Leg.R` across the X axis.
- Turn on `X Axis Mirror` to be able to work with both sides of the bones at the same time.

![Picture](./docs/14.jpg)
![Picture](./docs/15.jpg)

- Use the Weight Paint tool to define the influence of the bones on the vertices.

![Picture](./docs/16.jpg)

- Ensure all vertex groups are correctly delimited, to avoid unwanted weird movements.
- Make all vertices belong to at least one vertex group, otherwise they will ignore the armature movement.

![Picture](./docs/17.jpg)

- Separate the shoulders bones for better control of the animation.

![Picture](./docs/18.jpg)

### Animation

- Place keyframes for the bones in the armature.
- Use the record function to record new movements for the bones.
- The graph editor allows to control the easing of the animation.

![Picture](./docs/19.jpg)

### Inverse Kinematics

- Add anchor bones to setup the Inverse Kinematics for the feet and hands.
- Add the bone constraint for inverse kinematics, pointing to these bones.
- Use IK for simplifying the complex movements in the animations.

![Picture](./docs/20.jpg)
