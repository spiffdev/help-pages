---
title: 'Spiff Glossary'
---

### Spiff Terms

**Products** - Items which a merchant wants to sell with personalization or customization.  
**Product Display** - The 3D (or 2D) display that customers interact with during a customization experience. Typically shown in conjuction with a workflow when a consumer clicks the customize now on a merchant site.  
**Workflows** - The set of steps that a consumer uses to customize, personalize a merchant product. Eg Add Text, Choose Material, Upload image etc. Workflows are created in the spiff hub by merchants and can be attached to one or many products or 3Dmodels.  
**Options** - A list of Assets that are grouped together by their type (Fonts, Illustrations, Images, Models, Patchworks, Materials) to be displayed in a coresponding step. For example, an 'Add text' step which allows the consumer to type a message on a product could an an option that lists a number of font options for the user to choose from.  
**Assets** - Digital content that merchants maintain within the Spiff Hub. Used to populate Options to be displayed for use in a workflow. The list of assets the spiff hub allows merchants to store are fonts, frames, illustrations (svg's), Images (pngs or jpg), patchworks and 3D models (glb)  
**Steps** - The actions that a merchant can configure to provide a customization experience to their customers. A workflow is made up of a set of steps. Steps have types (Add text, Upload image, Question etc) and each step type has a specific function that it delivers. Steps are used to display an Option.  
**Regions** - This is the specific location on a product that a step will render to. Defined by **x** (distance from left of canvas), **y** (distance from top of canvas), **h** (height of the box) and **w** (Width of the box) . A region needs to be set for any object that is to be rendered onto a product. The defined regions are also used to build the pdf that is ultimately used to fulfil the print component of a product. 

### File Types
SVG - Scalable Vector Graphics (SVG) is an Extensible Markup Language (XML)-based **vector image** format for two-dimensional graphics with support for interactivity and animation. The SVG specification is an open standard developed by the World Wide Web Consortium (W3C) since 1999. Basically it is a digital object drawn in code (using a desgin program like Adobe illustrator) that as a result can be re-sized without loosing quality. It is because all pixels and lines are re-calculated and redrawn (in code) as the object is resized.  
TTF - True type fonts - the only font types accepted by the spiff hub asset repository. TrueType is an outline font standard developed by Apple in the late 1980s as a competitor to Adobe's Type 1 fonts used in PostScript. It has become the most common format for fonts on the classic Mac OS, macOS, and Microsoft Windows operating systems.  
PNG - Portable Network Graphics - is a raster-graphics file format that supports lossless data compression. PNG was developed as an improved, non-patented replacement for Graphics Interchange Format (GIF). Used in spiff to upload raster images with transparent backgrounds like company logos.   
JPG - Joint Photographic Expert Group (JPEG) - is a commonly used method of compression for digital images, particularly for those images produced by digital photography. It is the most common file type that a user will upload from their device and is supported by spiff. When a user uploads a JPG the object is always set on a rect (4 sided) canvas. This means that if the image doesnt fill the rect you will see a white background instead of it being transparent.   
PDF - The Portable Document Format (PDF) is a file format developed by Adobe in the 1990s to present documents, including text formatting and images, in a manner independent of application software, hardware, and operating systems. Basically it is the standard understood by most hardware and software programs allowing for a file to be layed out in a particular manner to be presented to others to view or print. 


### Shopify Terms
**Liquid Templates** - This is code base language used internally by shopify to allow merchants to make custom changes to their site. In summary, it is the backend of shopify that app developers (website look and feel) use to deliver addtional capabilities. On installation of the spiff plugin, we insert some code into the liquid template of the merchants active theme that allows us to render the button required to open design experiences within the merchant site. 