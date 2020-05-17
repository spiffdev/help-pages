---
title: 'Installing Snippets'
---

Install the spiff-connect app. Follow the installation process to sync your products.

In the spiff-connect app, select the Products tab. For each product:

Click Edit.
Click New and upload the product's 3D model.
Click Workflows and select each workflow to add.
Clik Save.
In the liquid files of your theme, you will need to either:

Add a new button that opens the customiser when clicked, or;
Modify an existing button to open the customiser when clicked.
To add a new button
The easiest way to do this is to find the line that creates the product form, which will look like this:

{% form 'product' ... %}

Below that line, add this:

{% render 'spiff-button', product_handle: product.handle %}

If you wish to customise the look of the button, you can supply arguments for text and colour.

{% render 'spiff-button', product_handle: product.handle, label_text: 'Customise me!', label_colour: '#000000', background_colour: '#FFFFFF' %}

The spiff-button snippet must take the following mandatory argument:

product_handle: The handle of the product. The product handle is the same string that appears as the slug in the URL of that product's page.
The spiff-button snippet additionally may take the following optional arguments:

background_colour: The background colour of the button. Defaults to Spiff Pink.
label_colour: The colour of the text on the button. Defaults to white.
label_text: The text to display on the button. Defaults to "Customise now on #spiff".
To modify an existing button
Find your add to cart button, which will look something like this:

<button>Add To Cart</button>

Augment the button like so:

<button
    data-spiff-personalise-button
    data-product-handle="{{product.handle}}"
    data-product-id="{{product.id}}"
    data-external-integration-id="{{shop.permanent_domain}}"
>
Add To Cart
</button>
Optional Steps
Additional Products
If you want to add a second, nonpersonalised product in addition to your customers' personalised product upon completion of a workflow, first make sure you're using a button augmented with the "data-spiff-personalise-button" like so:

<button
    data-spiff-personalise-button
>
Add To Cart
</button>
Then in your Shopify admin section, add a tag to the nonpersonalisable product pointing to the personalisable product. The tag will look like:

spiff-personalisable-product-handle-(your product handle)

For example, if your personalisable product has the handle "fancy-widget" then add the tag "spiff-personalisable-product-handle-fancy-widget".

Disabling Redirection
If you don't want your users to be redirected after their design is placed in the cart upon completion of their workflow, then add this tag to your Shopify product:

spiff-no-redirect-product-handle-(your product handle)

For example, if your product has the handle "fancy-widget" then add the tag "spiff-no-redirect-product-handle-fancy-widget".

Preview Images
If you want preview images of your customers' designs to appear on the cart page, find the line in your liquid files which currently creates the image for a cart item. The line will look similar to this (but proabably more complex):

<img src="{{ item | img_url: 'x190' }}" />

Replace that line with this one:

{% render 'spiff-line-item-image', line_item: item %}

Note that the argument provided as line_item should be the name of the variable used by your original line to refer to the line item (in this case, "item").

WooCommerce
Instructions for integrating with WooCommerce can be found in the readme for the WooCommerce plugin.

3D Content
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