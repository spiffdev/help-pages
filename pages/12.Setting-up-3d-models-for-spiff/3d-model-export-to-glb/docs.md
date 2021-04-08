---
title: '3D Model export to glb'
published: true
visible: true
---

The spiff platform accepts glb format for 3D models. glb is ......

For novices who have purchased a 3D model to be used on spiff make sure you purchase a model that has: 
- File format which is one of: FBX, OBJ, .Blend, GLB, GLTF, DAE as this will natively import into blender (you can start with an STL or X3D but you will need to do more with the file not covered in this section)
- Unwrapped Non Overlapping UV maps are preferred (to be explain later in the document), Overlapping and mixed can be used but can be more tricky (not covered in this section)
- UV Mapping
- <60,000 vertices


The following instructions assume:
* you have downloaded blender 2.8 or above to your desktop and that you have basic knowledge on how to navigate a 3D model
* You are importing a model with the above mentioned qualities
* You are using a desktop computer with a keyboard and mouse

**Opening your 3D model in Blender**

Importing to blender is as simple as opening a file in any other program, via File>Import>(Given File Format):

**Zoom in/Zoom out to your see your model. **  
On a non-apple mouse use the scroll wheel. 
On an apple mouse use the + and - on your keyboard

**Delete unwanted objects **  
Delete any unwanted models (sometimes there is a cube on load) so that you can see the object you have imported. This is also important because everthing in the scene is exported. 

**Orbitting (scrolling) around the model**

On a non-apple mouse, click hold and move the mouse wheel around 
On an apple mouse scroll along the mouse in any direction

**Scene/camera target setup**
Currently in order for a specified model, section of model, or collection of models to be targeted by our viewer, the line "_t" (keeping the 't' lowercase) must be added to the end of any given name/object name for a 3D model. 

You will find the name in the top right hand box under Scene Selection =>Collection => _objectname_

For example, if a model/object's name is "Shirt", you would then add the target, and so it would be renamed to "Shirt_t". If this target accent is **not** added to the name of the model/object, the camera will target the centre of the scene with a random zoom level depending on the size of the whole combination of objects. 

Note: Checking the size of your object. 3D space is infinite so in some cases 3D modellers will create objects that are either unecessarily large or small which can play havoc later in the spiff platform when you are trying to set zoom levels. Make sure your model is rougly its actual size or smaller.  Since changing sizes is an advanced feature, we would advise going back to the modeller to reset the size for you if it is too big. 

Material setup
Panels/sections of materials on a model that are to be used, modified, personalised, or altered in the workflow, should have context based material names. For example, if shoelaces are going to be altered on a shoe, the panel/material name should be something like "Laces".
a bottle, that has a personalised label should have a panel name of "Label" for instance. in any instance that multiple panels are called for of the same variety, (etc. Panel1, Panel2, Panel3) the first of them should include a number, for indexing sake. (Instead of 'Panel', then Panel2 etc, Start with 'Panel1', then so on)

How to Set up a material 
On the right hand bottom menu bar, navigate to the material properties icon that is shaped like a sphere and is usually red.

Click on the relevant part of the model and then go to the material as shown below and click on it to rename it

Model UV Mapping setup
For our platform there are two simple options to choose from when it comes to mapping a model.
If the model can share a single texture map for the whole object, and have sections edited via specified regions in the editor, a typical non overlapping  UV Map can be used. This is what we are covering in these intstructions. 

For products that require a PDF or a print file that has each personalised/customised section individual to one another (Like the front of a hoodie, and the back of a hoodie), single/Individual uv maps can be used for each panel/material/section. This will require seperate materials for each section. A more advanced user is required to complete this section. If this is what you are after, contact your 3D modeller or contact spiff and we can set this up for you. 

How to check the UV Map
Navigate to the top left corner of the screen until you see the plus (+) sign and drag outwards to the right.
Then click the TAB key on your keyboard- this will put you in edit mode
Then click the UV editing menu along the top menu bar
then click on the model side (left) 
whilst in edit mode click the letter 'a' to select all 

Now you can visually see the form or pattern (layout) the object has been unwrapped to. Thinmk of it as the 2D representation of your model
You can export this form/pattern for the purpose of laying out your customization panels by selecting all of the UV layout (a) clicking on the UV button and selecting the last option export UV Layout

Model Export to .GLB Format
Our 3D platform and viewer currently requires the format of GLB. However, some key file formats can be imported to Blender, then exported in the correct format for use with the spiff editor.
These models/assets need to be tested in the Babylon Sandbox to ensure they are working correctly and as expected before being uploaded to the spiff platform, this is one of our methods of quality control.
Blender supports various export settings for the .GLB and .GTLF File formats, we currently support the .GLB format on our platform.