# Unity URP Mixed Lighting Example

This quick lighting example was made using assets purchased from the Unity Asset Store. 

* Created Universal Render Pipeline Project.
* Converted materials to URP.
* Setup basic scene lighting using Unity's mixed lighting for real time controller/hand shadows and fully baked environment lighting.
* Corrected UV issues.
* Distributed texels/lightmap scaling focusing on scene focal point.
* Set up project for Oculus Quest 2 deployment.
* Built and tested the example at a steady 72 FPS.
* Total lightmap file size: 14.3 MB.
* Please note I was limited on time for the baking itself and medium quality settings were used.

You can find the APK included in the repo to test on your own device! (Note size of APK itself is not optimized)

![alt text](https://github.com/RyanMurdoch1/Lighting_Example/blob/main/Assets/Editor_Captures/MainImageSliced.png)

Low triangle and setpass calls were achieved while having realtime shadows cast by utilizing Unity's mixed lighting mode.

* Focal point with highest triangle density/detail: 117.7k.
* SetPass calls: 29.
* Realtime shadows cast from animated hands.

![alt_text](https://github.com/RyanMurdoch1/Lighting_Example/blob/main/Assets/Editor_Captures/RuntimeStats.png)

Mesh lightmap distibution optimized.

* Focus on allocating texels to objects at the scene's focal point. (Stool underneath player could have used a bit more space in the atlas considering it often receives realtime shadows...)
* More texels were allocated to objects receiving shadows from the bake. (Shown in the example below)
* Large floor and wall meshes proved problematic sizing for baking into atlases. Would recommend the splitting of these larger meshes to allow more individual texel allocation depending on proximity to focal point and likelihood to recieve shadows. (And a negligible drop in tris from frustrum culling)

![alt_text](https://github.com/RyanMurdoch1/Lighting_Example/blob/main/Assets/Editor_Captures/TexelAllocation.png)

Used the UVs from the store assets, with the exception of the room's walls. The wall's UVs were poorly done and displayed obvious artefacts while baking. I corrected this by manually generating the UVs in unity.

Worked to correct UV overlap in the cases of the most noticeable artefacts by allocating more space where needed in the lightmaps.

![alt_text](https://github.com/RyanMurdoch1/Lighting_Example/blob/main/Assets/Editor_Captures/MainUVs.png)




