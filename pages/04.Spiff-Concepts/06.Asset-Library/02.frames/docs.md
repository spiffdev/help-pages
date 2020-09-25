---
title: Frames
media_order: '7ff3300b1956239b03bc1763acea2e0376b439ad-screen-shot-2020-04-09-at-73456-am.png,52d13c990d202f3f847a4187f8ac3d3f8de241e4-screen-shot-2020-04-09-at-73648-am-1.png,214f2b0cec7c75906e22c77a95ee7099474e0d9c-screen-shot-2020-04-08-at-115128-am.png,c1d9b295582e7498bf22a94a489ea9c929b7b9f4-screen-shot-2020-04-09-at-72223-am.png,9b0004b012dfbcaa4d3c83454af26438ad451229-screen-shot-2020-04-09-at-72600-am.png,Screen Shot 2020-09-25 at 2.42.20 pm.png,Screen Shot 2020-09-25 at 2.54.25 pm.png,Screen Shot 2020-09-25 at 2.50.35 pm.png,Screen Shot 2020-09-25 at 3.09.49 pm.png,png-700x342.jpg,Screen Shot 2020-09-25 at 3.16.08 pm.png,d2b700ea-26e5-443d-9e64-9c067b9e7954.png,0e74a97a-0ab1-4391-8cdc-d23030f19fb1.png,752e3dde-f4c8-48b5-93c6-d368f230b509.png,Screen Shot 2020-09-25 at 3.48.33 pm.png,Screen Shot 2020-09-25 at 3.54.55 pm.png,Screen Shot 2020-09-25 at 4.07.00 pm.png'
---

### Frames

Frames render an upload button to a step allowing users to add an image from their device. Frames are a powerful and easy way to empower your consumer with the ability to create professional and artistic personalisation's without needing to have any knowledge of how to design. Without frames we would only be able to drop images into a square [region](https://help.spiff.com.au/spiff-concepts/workflows/step-details/regions) defined by a length and width. 

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/06.Asset-Library/02.frames/Screen%20Shot%202020-09-25%20at%202.50.35%20pm.png)

Like all other Spiff assets we provide you with public library so that you can start building workflows straight away. To see the library of frames simply make sure the **Show public assets** button is checked. Here are some of our existing frames.

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/06.Asset-Library/02.frames/Screen%20Shot%202020-09-25%20at%202.42.20%20pm.png)


#### Accepted File Formats

When a use is uploading to a frame their image needs to be a [JPG](https://en.wikipedia.org/wiki/JPEG), [PNG](https://en.wikipedia.org/wiki/Portable_Network_Graphics) or [SVG](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics).

#### Uploading Logos

Uploading logos to a frame works the same as uploading any other image except the image will need to have a transparent background. The file types that we reccomend to use are PNG's and SVG's because they support transaprency. JPG does not, applying a logo in a JPG will result in white space to fill the area outside of the logo.

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/06.Asset-Library/02.frames/Screen%20Shot%202020-09-25%20at%203.16.08%20pm.png)

#### How many Frames can I use?

When adding frames to a workflow step you can have as many as you like! As long as they all have the same aspect ratio. The reason they all need to be the same aspect ratio is because they will all be placed into the same [region](https://help.spiff.com.au/spiff-concepts/workflows/step-details/regions), which will stretch/squish a frame that is not the right size.

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/06.Asset-Library/02.frames/Screen%20Shot%202020-09-25%20at%202.54.25%20pm.png)

#### Placing your Frames

Placing your frames is made very simple with the use of [regions](https://help.spiff.com.au/spiff-concepts/workflows/step-details/regions). A region is an area that defines the location where the content in your step is placed on the panel. Simply find out the region in which you want your frame to appear on the panel and then add your chosen frame(s). Go here to more about placing your [regions](https://help.spiff.com.au/spiff-concepts/workflows/step-details/regions).

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/06.Asset-Library/02.frames/Screen%20Shot%202020-09-25%20at%203.09.49%20pm.png)

#### Creating a Frame

Frames are created as vectors in Adobe Illustrator and are exported as SVG’s and uploaded to the frames in the **asset gallery**. Only SVG’s in this folder will be able to be used in the upload step. See steps below for detailed instructions on how to create a frame in Adobe Illustrator.

1. Create your desired shape as a vector in Illustrator, this shape can be anything you like. We have chosen to make all of our frames grey to keep them consistant and reccomend you do the same. The hex code is #616262. 

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/06.Asset-Library/02.frames/Screen%20Shot%202020-09-25%20at%203.48.33%20pm.png)

2. After you have created your shape turn it into a compound path. Do this by going to the **Object** tab in the top menu, and down to **Compound Path** and then **Make**. Also it's important to note if your frame is made up of two or more objects, first **group** your objects and then make them a compound path.

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/06.Asset-Library/02.frames/d2b700ea-26e5-443d-9e64-9c067b9e7954.png)

3. Now your frame is ready to export as an SVG. To do this go to the **File** tab in the top menu and down to **Export** and **Export As...**.

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/06.Asset-Library/02.frames/0e74a97a-0ab1-4391-8cdc-d23030f19fb1.png)

4. This will bring up an SVG Options box. In this box ensure that the **Images** drop down is set to **Embed**. Then press **OK**.

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/06.Asset-Library/02.frames/752e3dde-f4c8-48b5-93c6-d368f230b509.png)

5. Now your frame is exported to your desired location. Now all you need to add in a small snipped of code so that our system will recognize the SVG as a frame. Open up any program where you can see html such as [Visual Studio Code](https://code.visualstudio.com/) and open your new frame. Near the top of the code you should see the word **path**. Once you find this all you need to do is paste **"id=target-path"** after it and then save. Your frame is now ready to upload.

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/06.Asset-Library/02.frames/Screen%20Shot%202020-09-25%20at%203.54.55%20pm.png)

6. Now your frame is ready sign into your account on Spiff and got to your frame tab in assets and press **Create New Asset** in the top right. And viola you have created a frame!
  
  
![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/06.Asset-Library/02.frames/Screen%20Shot%202020-09-25%20at%204.07.00%20pm.png)