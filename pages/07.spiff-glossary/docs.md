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


### Shopify Terms
**Liquid Templates** - This is code base language used internally by shopify to allow merchants to make custom changes to their site. In summary, it is the backend of shopify that app developers (website look and feel) use to deliver addtional capabilities. On installation of the spiff plugin, we insert some code into the liquid template of the merchants active theme that allows us to render the button required to open design experiences within the merchant site. 