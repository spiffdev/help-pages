---
title: Regions
media_order: 'Screen Shot 2020-09-23 at 3.32.37 pm.png,Screen Shot 2020-09-23 at 3.45.33 pm.png,Screen Shot 2020-09-23 at 4.11.49 pm.png,Screen Shot 2020-09-23 at 4.20.56 pm.png,Screen Shot 2020-09-24 at 9.47.00 am.png,Screen Shot 2020-09-24 at 10.16.11 am.png,Screen Shot 2020-09-24 at 10.17.35 am.png'
---

### What is a Region?

A region is an area that defines the location where the content in your step is placed on the panel.

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/03.workflows/03.step-details/02.regions/Screen%20Shot%202020-09-23%20at%203.32.37%20pm.png)

A region can be **any rectangular shape**, and sit anywhere on the panel.
You can also have multiple regions per step. To add more regions simply use the **+ ADD REGION** button and enter in your measurements.

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/03.workflows/03.step-details/02.regions/Screen%20Shot%202020-09-23%20at%203.45.33%20pm.png)

### Placing your Regions

Regions are defined in pixels, so to find out where to place them make sure your design file is in this measurement.

To find out what your coordinates are find the:

1.  **(x)** Distance from the left edge  
3. **(y)**  Distance from the top edge
4. **(w)** Width of the area
5. **(h)**  Height of the area



![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/03.workflows/03.step-details/02.regions/Screen%20Shot%202020-09-23%20at%204.11.49%20pm.png)

These are the values you would see allocated to an object (e.g. text box) in Adobe Illustrator or Photoshop or any other design program.
For example in Adobe Illustrator your regions would look something like this -

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/03.workflows/03.step-details/02.regions/Screen%20Shot%202020-09-23%20at%204.20.56%20pm.png)

When in Spiff these regions would look like this (these have been rounded up) -

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/03.workflows/03.step-details/02.regions/Screen%20Shot%202020-09-24%20at%209.47.00%20am.png)

### Completing your Regions

Regions are very powerful and require a little more than just adding your coordinates. You also need to set a **layer index**, add **rotation** (if required), and choose your **[panel](https://help.spiff.com.au/spiff-concepts/workflows/workflow-details/panels)**.
The layer index refers to which layer this step will be on, you can have as many layers as you like.

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/03.workflows/03.step-details/02.regions/Screen%20Shot%202020-09-24%20at%2010.16.11%20am.png)

It's important to keep your layers structured neatly or you may not be able to see everything you've added to your panel. For exmaple:

- **Layer 0** is a color step where someone can choose the color of their background
- **Layer 1** is an upload step where someone can upload an image
- **Layer 2** is a text step

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/03.workflows/03.step-details/02.regions/Screen%20Shot%202020-09-24%20at%2010.17.35%20am.png)

We also set a rotation from 0° to 360°.

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/03.workflows/03.step-details/02.regions/Screen%20Shot%202020-09-24%20at%2010.36.32%20am.png)

To complete your region you need to assign it a panel. The panel you assign it to will be the one it appears on.

The last thing you can configure in regions is the **immutable** checkbox. This setting will make it so that the object is locked when in the **advanced editor**.