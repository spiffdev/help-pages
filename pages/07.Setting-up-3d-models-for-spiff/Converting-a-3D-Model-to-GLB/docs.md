---
title: 'Converting a 3D Model to GLB (Simplified)'
media_order: 'bf783ba4-d348-47f2-a4cf-62e7d1a5b47c.png,d31557dc-6b2c-42e8-b71e-3d58814a7db5.png,9bcf8ab5-7109-4f70-851c-68fa189d6aac.jpg,7e4fca5f-b0d7-46db-8a01-22cd9cf95bc3.jpg,c0222420-13ef-4806-9671-b768a6188c5c.jpg'
published: true
visible: true
---

When converting your 3D model to work with the #SPIFF editor, we use the Blender 3d Toolset. Since the models used on our editor are going to appear across various devices, including mobile, there are some steps we need to take to ensure it all works as it should.  Understanding the Blender program; where everything is, can daunting without context, we’ll guide your through it. (See attached) 

![](bf783ba4-d348-47f2-a4cf-62e7d1a5b47c.png)

## Getting to the right format
note: sometimes a fresh blender file can include a cube object in the scene. removing this is as simple as left clicking it, and deleting it with the delete key.

For #SPIFF, the file format “.glb” is required, this format is quickly becoming the industry standard for online & mobile experiences for its efficiency and speed. Although .glb is the only acceptable format to the #SPIFF editor itself, we can convert to it from more conventional formats with ease. 

In order to import your model to Blender, to further convert, it's as simple as opening Blender, and then navigating to File>Import>, and then searching for your model file. This works like most other softwares' import feature. For this example we will import a .FBX file. 

![](d31557dc-6b2c-42e8-b71e-3d58814a7db5.png)

![](f5f9a286-1b67-4f69-9ad6-bef572e497bb%20%281%29.png)

## Collect for Export
note: it’s really helpful at this point to save this blender file for later use. through File>Save> 

Now that you’ve imported your model, we can easily get an overview on the imported model and continue to export it in the .GLB Format. 
All we need to do is select all of the objects we would like to include in our GLB. (The object itself, lights etc.) and then proceed to export it. That simple! 

![](9bcf8ab5-7109-4f70-851c-68fa189d6aac.jpg)

![](7e4fca5f-b0d7-46db-8a01-22cd9cf95bc3.jpg)

## Check it out!
Now that we have exported our model to the .GLB Format, we can quickly and easily view it in an 
to make sure it all works correctly before uploading to spiff.  We use the [Babylon.js](https://sandbox.babylonjs.com/) Viewer.

![](c0222420-13ef-4806-9671-b768a6188c5c.jpg)

## Finalisation
Now that we’re all converted we are ready to upload to #SPIFF and gain some serious traction on our personalisation adventure! Of course there are a variety of other things to look through with our 3D Model before exporting, but this is basic first step to set things up. [**Next we will cover how to attach textures & setup materials for the GLB platform.**](https://help.spiff.com.au/)