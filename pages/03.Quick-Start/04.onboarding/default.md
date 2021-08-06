---
title: Onboarding
---

### Assumptions 
- You have already installed the desired spiff plugin on your ecommerce store.
- You have your 3D models already setup to spiff [3D model Specifications](https://help.spiff.com.au/spiff-concepts/product-displays/3d-model-asset-request)
- You have any design assets ready for upload. E.g fonts, illustrations (SVG's) and images (PNG's and JPG's) 
- You have products already installed on your ecommerce site. 

**Note: If your store is live and you want to test without affecting live products set up a test theme by duplicating your live theme. Then re-name the copy of your live theme to spiff_yourstorename and install the snippet explained below on this theme and not on your live site. **

### Key Concepts 
Spiff Architecture - It doesnt matter in which order you start, but in order to get your first product up and running you need to do three things:
- Create a product 
- Create a worklfow - This includes uploading assets and setting up option lists
- Link a 3D model  

### Create your product

#### **Shopify and BigCommerce**
- Click on the create products button on the home page in the spiff hub accessable through the app button in your ecommerce store
- Your products will begin to load from your store. Depending on how many products you have in your store, this could take up to 1 minute
- Search for your product in the search bar at the top of the page
- Click the select product button in the top right corner of the page

#### **Neto and WooCommerce**
- Click on the create products button on the home page in the spiff hub accessable through the app button in your ecommerce store. 
- Fill in the required information to create your new product such as **name**, **price** etc.
- Click **create product** in the top right hand side of the page once you are done

Your product is now available for you to customise on spiff and should now appear in the products list page. 

### Create a workflow
Whilst you can create a workflow without options and assets to begin with it is advisable to have them ready and uploaded to be used in the relevant steps. 

#### Uploading assets
- Click on the **Assets **Tab in spiff 
- Click on the relevant asset type you wish to upload. click on the little blue question marks for explanations of what each asset type represents
- Click on the **Create Product**
- Find your asset on your desktop and click open (make sure you name your assets properly so that you can search for them easily later e.g. alien_face.svg will be searchable by alien and face) 
- Your asset should now apppear with an image in the **assets folder**

#### Create an option list
This is only required where you want to display a list of options for your consumers to choose from. Eg. Choose from these Fonts, Colours or Illustrations  
- Click on the **options** tab in spiff
- Click on **create option** in the top right corner of that page
- Name your Option (Eg. T-shirt Illustrations) 
- Select your option type. (for the example above you would select illustrations) 
- Start adding your variants/assets. When you click on the **upload asset** button it will refer to the assets you uploaded (and the public assets we give you by default)
- Select your asset and name it accordingly. This is the name that will appear in the consumers order summary so it needs to be user friendly. 
- Select a default asset if you would like one of the variants to automatically appear on the model when the conusmer reaches that step. If you dont select a default asset the user will need to make a selection before any asset appears on the model. 
- Save Option

#### Create a workflow

Workflows are the steps you take your consumers through in their customisation journey and is the glue that brings the experience together. 

- Click on the **workflows** tab in spiff
- Click **create new workflow**
- Name your workflow 
- Add your first step (See little blue question marks next to each step type for help on each step capabilities) 
- All steps require you to add a Step Title and Step Help Text
- Complete configuration of attributes for the step 
- Add an **option** by searching for it in the options search bar. Note: Only options relevant to that step type will display
- Add a condition if required
- Click **create step **
- Add further steps as required 
- Save the workflow in the top hand corner when you have completed the workflow

Creating Step Groups 
Step groups are the ability to display more than one step on the same page for the consumer experience
- In the workflow details section of a workflow
- Click **create Step Group** 
- Name the Step Group 
- Once complete go to the relevant steps and you will see a new drop down box that will allow you to link a step to the step group
- You will see a chip appear in the step group with the name of the step you added. 
- Steps will play in order that they appear and can be moved around by selecting the step and moving it to your preferred position in the workflow. 
- Click **Save Workflow**

### Complete Product Setup

#### **Shopify and BigCommerce**
- Click on the relevant product in the products tab in the spiff toolbar
- Open the product
- Click **edit**
- Click **exisiting** next to the 3D model upload
- Link the relevant uploaded 3D model
- Below the save button click on **workflows**
- Type in the name of the workflow you created and select it
- **Save product**

#### **Neto and WooCommerce**
 Click on the relevant product in the products tab in the spiff toolbar
- Open the product
- Click **edit**
- Click **exisiting** next to the 3D model upload
- Link the relevant uploaded 3D model
- Below the save button click on **workflows**
- Type in the name of the workflow you created and select it
- Scroll down to the **add a integration** section and add your current integration you wish to sync this spiff product too
- Press on the three dots on the right and click **edit**
- Add the **SKU** of the neto product you wish to sync this spiff product too
- **Save product**

Next step:

#### Shopify
### [Installing the snippet](https://help.spiff.com.au/integrations/shopify/installing-snippets)
