---
title: '3D Model export to glb'
published: true
visible: true
---

The spiff platform accepts glb format for 3D models. glb is ......


Opening your 3D model in Blender

Importing to blender is as simple as opening a file in any other program, via File>Import>(Given File Format):

**Zoom in/Zoom out to your see your model. **  
On a non-apple mouse use the scroll wheel. 
On an apple mouse use the + and - on your keyboard

**Delete unwanted objects **
Delete any unwanted models (sometimes there is a cube on load) so that you can see the object you have imported. This is also important because everthing in the scene is exported. 




Import your FBX to open it in blender

Scene/camera target setup
Currently in order for a specified model, section of model, or collection of models to be targeted by our viewer, the line "_t" (keeping the 't' lowercase) must be added to the end of any given name/ object name for a 3D model. For example, if a model/object's name is "Shirt", you would then add the *target, and so it would be renamed to "Shirt_t". If this target accent is added to the name of the model/object, the camera of the scene will just target the centre of the scene with a random zoom level depending on the size of the whole combination of objects. 

Material setup
Panels/sections of materials on a model that are to be used, modified, personalised, or altered in the workflow, should have context based material names. For example, if shoelaces are going to be altered on a shoe, the panel/material name should be something like "Laces".
a bottle, that has a personalised label should have a panel name of "Label" for instance. in any instance that multiple panels are called for of the same variety, (etc. Panel1, Panel2, Panel3) the first of them should include a number, for indexing sake. (Instead of 'Panel', then Panel2 etc, Start with 'Panel1', then so on)

Model UV Mapping setup
For out platform there are two simple options to choose from when it comes to mapping a model.
If the model can share a single texture map for the whole object, and have sections edited via specified regions in the editor, a typical non overlapping  UV Map can be used.
for products that require a PDF Or a print file that has each personalised/customised section individual to one another (Like the front of a hoodie, and the back of a hoodie, be different print files or pages, Single/Individual uv maps can be used for each panel/material/section.

Model Export to .GLB Format
Our 3D platform and viewer currently requires the format of GLB. However, some key file formats can be imported to Blender, then exported in the correct format for use with the spiff editor.
These models/assets need to be tested in the Babylon Sandbox to ensure they are working correctly and as expected before being uploaded to the spiff platform, this is one of our methods of quality control.
Blender supports various export settings for the .GLB and .GTLF File formats, we currently support the .GLB format on our platform.