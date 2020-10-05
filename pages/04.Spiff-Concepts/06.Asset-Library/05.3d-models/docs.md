---
title: '3D Models'
---

### 3D Models

3D models are used in workflows to create a memorable experience for users; where they can see a realistic replica of their chosen product update in real time.

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/06.Asset-Library/05.3d-models/Screen%20Shot%202020-10-05%20at%202.02.06%20pm.png)

When building 3D content for spiff the following workflow must be used.

Build content in Blender including meshes, animations and materials
Export to GLB
Test GLB file by uploading to the Bablyon Sandbox
Submit both the GLB exported file as well as the .blend file
All Models must be built in Blender. Deliverables are:

A .blend file
A .glb file.
Models
Please follow best practices when building models. Ensure that:

Models have no NGons
Models have a low poly count as we target mobile devices
Models have their normals calculated correctly and facing out.
Models have no doubles
Models have their scale, position and rotation all applied. Ensure doing this before UV unwrapping
Models have any unnecessary faces removed
When exporting a model you will also need to tell us how to frame the model in the scene. This will allow our camera to correctly point at the model. In order to do this you must add a _t after the name of any model that should be framed in the centre of the scene. Doing this on the mesh in blender will ensure that the name will be correctly set in the exported GLB file.

Materials and Textures
Models must include materials applied to all of their faces. GLB supports multipule materials per mesh so assigning materials to different faces is valid. Depending on the content different materials will need to be used. All materials should use PBR rendering. It is recommended to use the principled BSDF node however the custom nodes provided by the KhronosGroup are also valid. See the glTF blender exporter documentation for more details on using these nodes.

Models can contain a mixture of both static and dynamic textures. In this use case a static texture is defined as any texture that is exported with the GLB file. Avoid using too many of these as they make the GLB export bigger. A dynamic texture is a texture that is created in realtime as the user updates their design. The spiff software will build up a PNG image texture that will be updated based on a user controlled design. In order for the spiff software to be able to replace this realtime texture the software needs to be able to resolve the material within the scene in order to work. Because of this limitation materials must be named after the panels they represent. Spiff will provide these panel names as they will depend on what is being modelled.

UV Maps
As mentioned above the spiff software will provide textures that are built dynamically and updated on the model in real time. These textures will be created based on a prebuilt paper form. This paper form describes where different parts of a paper product are cut and folded, think origami instructions. For a user to see their final product in real time all UV Maps will need to be set up based on this predefined form.

Camera
Please ensure that no cameras are exported in the GLB. It would be best to remove the camera from the scene in blender as rendering form blender is not required.

Animation
Please ensure that all animation clips exported run for the same length as the spiff engine will play everything as one long animation.

Exporting
To export in blender 2.8 select "File" > "Export" > "glTF 2.0". In this screen ensure you have the following settings configured in the bottom left corner

General: "+Y Up" Checked
Meshes: Ensure that "UVs", "Normals" and "Vertex Colours" are selected.
Objects: Nothing should be checked
Materials: Ensure that "Materials" is selected
Animations: Ensure the following is selected "Animations", "Limit To Playback Range", "Always Sample Animations", "Skinning", "Shape Keys", "Shape Key Normals". Also ensure that keyframes start at 0 is unchecked