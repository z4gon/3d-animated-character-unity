# 3D Animated Character

Modelled, Textured and Animated in Blender, later setup in **Unity 2021.3.10f1**

### References

- [How To Make A 3D Character For Your Game](https://www.youtube.com/watch?v=ogz-3r0EHKM)
- [Baking a Normal Map](https://www.youtube.com/watch?v=tndUB5b4STI)
- [Baking Normals Low/High Poly](https://www.reddit.com/r/learnblender/comments/gbgvla/does_having_the_high_poly_object_being_completely/)
- [Blender/Unity Smooth Shading Compatibility](https://www.reddit.com/r/Unity3D/comments/47lska/just_found_out_that_blenders_smooth_shading_will/)
- [3D Scifi Kit Starter Kit](https://assetstore.unity.com/packages/3d/environments/3d-scifi-kit-starter-kit-92152)

## Implementation

### 3D Modelling

- Design the character in a design software like Affinity.

![Picture](./docs/1.jpg)

- Model a low poly version.

![Picture](./docs/2.jpg)

- Subdivide and add more details, to generate a high resolution version.
- UV Map the high resolution version.
- Decimate to get a low poly again, with aligned UVs.
- Use Subdivision Catmul-Clark to get an Ultra HD to bake normals.

### Normal Mapping

- Set Smooth Shading to both the low poly and high poly models.
- Modify the models as needed to minimize meshes being too close together (like shoulders).
- Be sure both models are superposed, bake the normals making sure the extrusion is set to minimum, and the max ray distance is 0.

### Texturing

- Texture the low poly model while using the normal map.

### Import into Unity

- Import in Unity as FBX, without calculating smoothness for normals, just import the normals interpolation from the fbx.
