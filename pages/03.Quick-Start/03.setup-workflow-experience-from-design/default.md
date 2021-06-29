---
title: 'Setup Workflow Experience from Design'
media_order: 'Screen Shot 2021-06-29 at 10.19.38 am.png,Screen Shot 2021-06-29 at 10.19.56 am.png,Screen Shot 2021-06-29 at 10.20.12 am.png,Screen Shot 2021-06-29 at 10.21.33 am.png,Screen Shot 2021-06-29 at 10.29.42 am.png,Screen Shot 2021-06-29 at 10.34.07 am.png,Screen Shot 2021-06-29 at 10.37.28 am.png,Screen Shot 2021-06-29 at 10.41.37 am.png,Screen Shot 2021-06-29 at 10.44.51 am.png,Screen Shot 2021-06-29 at 10.46.51 am.png,Screen Shot 2021-06-29 at 10.50.18 am.png'
---

## Setup Workflow Experince from your Design

You are able to set up any design you like in Spiff from any Photoshop or Illustrator design. No matter how many colors, text steps of photo uploads you need. We can do it!

### Example

This exmaple will show you how to set up a simple design from a PSD (Photoshop) file.

1. Open your PSD file 

![](https://help.spiff.com.au/user/pages/03.Quick-Start/03.setup-workflow-experience-from-design/Screen%20Shot%202021-06-29%20at%2010.21.33%20am.png)

2. Turn off the visibilty on any layers you don't want to export

![](https://help.spiff.com.au/user/pages/03.Quick-Start/03.setup-workflow-experience-from-design/Screen%20Shot%202021-06-29%20at%2010.19.38%20am.png)

3. Go to File > Export As > and export your design

![](https://help.spiff.com.au/user/pages/03.Quick-Start/03.setup-workflow-experience-from-design/Screen%20Shot%202021-06-29%20at%2010.19.56%20am.png)

4. Make sure your png/jpg is not super large. Try to keep everything under 1mb otherwise things can load slowly. 

![](https://help.spiff.com.au/user/pages/03.Quick-Start/03.setup-workflow-experience-from-design/Screen%20Shot%202021-06-29%20at%2010.20.12%20am.png)

5. Open your newly exported png/jpg in Illustrator and ensure it is the correct size you want it. When doing this make sure your point is set to the top left and your x and y is set to 0, 0. This needs to be on 0, 0 because our editor reads from the top left point.

![](https://help.spiff.com.au/user/pages/03.Quick-Start/03.setup-workflow-experience-from-design/Screen%20Shot%202021-06-29%20at%2010.29.42%20am.png)

6. Now you have your design in Illustrator you can draw a box around the areas you want to add text. This will be your [regions](https://help.spiff.com.au/spiff-concepts/workflows/step-details/regions). Select one of the boxes you have drawn and in the Properties tab you can see the measurements you will need to put in your region. Make sure these meaurements are in pixels.

![](https://help.spiff.com.au/user/pages/03.Quick-Start/03.setup-workflow-experience-from-design/Screen%20Shot%202021-06-29%20at%2010.34.07%20am.png)

7. Now, go to [Spiff Asstes](https://help.spiff.com.au/spiff-concepts/asset-library) and upload your png/jpg you exported from PSD into the [Images](https://help.spiff.com.au/spiff-concepts/asset-library/images) tab.

![](https://help.spiff.com.au/user/pages/03.Quick-Start/03.setup-workflow-experience-from-design/Screen%20Shot%202021-06-29%20at%2010.44.51%20am.png)

8. Create your workflow. Select the model you want to use.

9. Enter in the workflow details, and [panel](https://help.spiff.com.au/spiff-concepts/workflows/workflow-details/panels) size.

10. Start by creating a [Silent Illustration](https://help.spiff.com.au/spiff-concepts/step-types/silent-step) step to put your jpg/png on. Select your asset and put in your [regions](https://help.spiff.com.au/spiff-concepts/workflows/step-details/regions) and keep your layer low as possible because you want this image to sit behind the text. 0 works best.

9. Now go into your workflow and add a [Text](https://help.spiff.com.au/spiff-concepts/step-types/add-text) step. Fill in your desired information and in the bottom tab enter in your regions from Illustrator. We round up the pixels to make the process cleaner.

![](https://help.spiff.com.au/user/pages/03.Quick-Start/03.setup-workflow-experience-from-design/Screen%20Shot%202021-06-29%20at%2010.37.28%20am.png)

8. Do the same with your second text step. 

![](https://help.spiff.com.au/user/pages/03.Quick-Start/03.setup-workflow-experience-from-design/Screen%20Shot%202021-06-29%20at%2010.41.37%20am.png)

9. Now your workflow should be set up.