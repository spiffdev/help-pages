---
title: Assets
media_order: 'Screen Shot 2020-05-03 at 10.19.54 pm.png,ladybug.svg,bee 1.svg,dragon fly.svg,firework 8.svg,Happy Birthday 8.svg,Screen Shot 2020-03-25 at 4.27.57 pm.png,Screen Shot 2020-05-05 at 7.33.32 am.png,Screen Shot 2020-05-05 at 7.35.55 am.png,Screen Shot 2020-03-25 at 4.50.21 pm.png,Screen Shot 2020-03-25 at 4.50.55 pm.png,Screen Shot 2020-05-06 at 7.24.09 am.png,Screen Shot 2020-04-08 at 11.51.28 am.png,Screen Shot 2020-04-09 at 7.22.23 am.png,Screen Shot 2020-04-09 at 7.26.00 am.png,Screen Shot 2020-04-09 at 7.34.56 am.png,Screen Shot 2020-04-09 at 7.36.23 am.png,Screen Shot 2020-04-09 at 7.36.48 am (1).png'
---

Spiff provides its Merchants with a Digital Asset Mangement Repository. This repository is used to store all assets required to execute a personalization  
or customization workflow for the merchants customers. 

Assets types available for storage on spiff are: 
- [Fonts](#fonts)
- [Frames](#frames)
- [Illustrations](#illustrations)
- [Images](#images)
- [3D Models](#3d-models)
- [Patchworks](#patchworks)  

Assets are located in the spiff hub from within your ecommerce store. Log in to your store and click on apps. This will open the spiff hub. 
Click on the assets button in the left hand Navigation bar and you be presented with the Repository. The default page is the fonts page.
![](Screen%20Shot%202020-05-03%20at%2010.19.54%20pm.png)
>>>> You must click on the relevant Asset type before you click the create asset button. The create asset button will only allow you to upload file types of the relevant asset type.

### <a name="fonts"></a>Fonts
Fonts are used in the Fonts Step Type in workflows which allows the merchant to set 1 or more regions on a canvas where the user can type in a personalized message. 

The spiff editor accepts True Type (.ttf) fonts. They are uploaded to the spiff platform via the spiff hub in the assets folder. Spiff provides the merchant with a host of public fonts that merchants can use for free in their respective workflows. 

Click on the assets folder and select the fonts tab
Then click the create asset button and upload your fonts
http://help.spiff.com.au/user/pages/03.Spiff-Concepts/05.Asset-Library/Screen%20Shot%202020-05-06%20at%207.24.09%20am.png
They will then appear as they do in the image above. You will see an automatically generated preview of this font. If the preview image is broken, there may be a corruption with that font so it is best to delete it and try again. If the problem persists and you need that particular font please email spiff support using the live chat button on the right side of the screen.   

#### Attributes
The merchant can set a default font for a text step. In this case the merchant dictates that the consumer must use the font provided and no list options are shown to the user. The user is just presented with a Text field with a (configurable) color picker. This is displayed in the left hand imnage below 
<table><tr>
<td>  <img src="http://help.spiff.com.au/user/pages/03.Spiff-Concepts/05.Asset-Library/Screen%20Shot%202020-03-25%20at%204.50.21%20pm.png" width="450" /></td>
<td> <img src="http://help.spiff.com.au/user/pages/03.Spiff-Concepts/05.Asset-Library/Screen%20Shot%202020-03-25%20at%204.50.55%20pm.png" width="450" />  </td>
</tr></table>

You can also create an option with a list of font variants which will display like the right hand above image. 


Other controls the merchant can configure into the workflow are: 

- Text alignment - centred, justified, left, right
- Text Size - Select a required font size or range
- Text Colour - colours displayed are customisable
- Font Lists - build an option using the font option type 
- Character Limits - Control your users results by setting character limits if the design you provide requires it. 
- Constrain text to a fixed region and re-size smaller or larger depending on character length
- Profanity filter - Spiff Moderation 
- Case sensitivity - Set all text the user types to appear in Uppercase, Lowercase or Titlecase
- Vertical text - This allows text to print vertically from top to bottom 
- Rotate text - Rotate 

Fonts are also vectors like SVG’s and so can be re-sized to any size necessary size without compromising print quality. 

### <a name="frames"></a>Frames
This step renders an Upload button allowing the user to add an image from their device. 

Accepted File Types = JPG, PNG and SVG

Uploading Frames to fill a defined area 

Images uploaded to spiff are defined by regions. A region is space defined with the panel area. A region has an x and y coordinate value to position the image (top Right corner) on the model and pdf as well as a height and width. These coordinates are also used to build the pdf upon execution of the order. 

Generally merchants will require a standard square frame but it is important to note that this can be any shape or combination of shapes. 
![](Screen%20Shot%202020-04-08%20at%2011.51.28%20am.png)

Frames are created as grey vectors in illustrator and are exported as SVG’s and uploaded to the Frames TAB in the asset gallery. Only SVG’s in this folder will be able to be used in the upload step. 

A user can either use one frame or many. If an Option is added (list of variants) to the step to display many frames, the user can choose from a range of shapes. 


Note: Frames are vectors and so are sized to be in proportion to the length and width defined by the merchant as the area the frame takes up on the object. This means that a shape uploaded to assets will be distorted to fit within those parameters. 

Eg. In a region defined as a square, a rectangle will be resized into a square to fit.  In the example below you have a region on the bottle defined as almost a square 448x408.


You Can see that the uploaded frame shape is rectangular in shape


When it is placed onto the object it is resized and is no longer a rectangle. 


 

See example below for a standard square frame on a workflow. 


Note that when the user uploads an image they can click on the image in the step and zoom in or zoom out and pan the image into their desired spot. 

Uploading Logos
To apply an image like a logo the user must upload PNG or SVG as they are transparent when inserted onto the product, whilst JPG files are not. 

Applying a logo in a JPG will result in white space to fill the area outside of the logo. Below is an example of how a Transparent PNG will place in the model. Notice that the white background in the file on the right does not show on the object. If this were a JPG the white background would show on the model as a square around the logo just like it does on the right. 


 

### <a name="illustrations"></a>Illustrations

Illustrations are vector art usually drawn in illustrator or a program like it. The spiff editor accepts illustrations in the form of SVG (scaleable vector graphic). 
Example SVGS

<table><tr>
<td>  <img src="http://help.spiff.com.au/user/pages/03.Spiff-Concepts/05.Asset-Library/ladybug.svg" width="150" /></td>
<td> <img src="http://help.spiff.com.au/user/pages/03.Spiff-Concepts/05.Asset-Library/bee%201.svg" width="150" />  </td>
<td>  <img src="http://help.spiff.com.au/user/pages/03.Spiff-Concepts/05.Asset-Library/dragon%20fly.svg" width="150" /></td>
<td> <img src="http://help.spiff.com.au/user/pages/03.Spiff-Concepts/05.Asset-Library/firework%208.svg" width="150" /> </td>
<td> <img src="http://help.spiff.com.au/user/pages/03.Spiff-Concepts/05.Asset-Library/Happy%20Birthday%208.svg" width="150" /></td>
</tr></table>


The advantage of using SVG’s in our editor is that colours that exist within the SVG are easily modified using the spiff UI. The other obvious advantage is that for the purposes of print, SVG’s can be scaled to any size without loosing print quality.
![](Screen%20Shot%202020-03-25%20at%204.27.57%20pm.png)
Spiff provides all new merchants with a library of illustrations that can be found in their asset gallery by checking the public assets check box. The user can store their illustrations in the spiff asset gallery. 
![](Screen%20Shot%202020-05-05%20at%207.33.32%20am.png)
The illustrations are linked to merchant workflows by creating a new [option](http://help.spiff.com.au/spiff-20concepts/options) and selecting illustration as the option type and then building a list of variants (illustrations) to be displayed in a step on a merchant workflow. 
![](Screen%20Shot%202020-05-05%20at%207.35.55%20am.png)
The ability to set colours on the step is a configurable option

SVG Set Up 
How to set up in illustrator

Unusable SVG's 
Any that have gradients. It there is too much detail

