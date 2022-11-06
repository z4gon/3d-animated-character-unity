# 3D Animated Character

Modelled, Textured and Animated in Blender, later setup in **Unity 2021.3.10f1**

### References

- [How To Make A 3D Character For Your Game](https://www.youtube.com/watch?v=ogz-3r0EHKM)
- [Baking a Normal Map](https://www.youtube.com/watch?v=tndUB5b4STI)
- [Baking Normals Low/High Poly](https://www.reddit.com/r/learnblender/comments/gbgvla/does_having_the_high_poly_object_being_completely/)
- [Blender/Unity Smooth Shading Compatibility](https://www.reddit.com/r/Unity3D/comments/47lska/just_found_out_that_blenders_smooth_shading_will/)

## Implementation

1. Model a low poly version.
1. Subdivide and add more details, to generate a high resolution version.
1. UV Map and texture the high resolution version.
1. Decimate to get a low poly again, with aligned UVs.
1. Use Subdivision Catmul-Clark to get an Ultra HD to bake normals.
1. Deflate the low poly to make it contained within the Ultra HD, to bake the normals.
