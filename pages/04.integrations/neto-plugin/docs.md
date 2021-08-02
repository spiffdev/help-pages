---
title: 'Neto Plugin'
---

Install Setup Instructions

For Neto customers, components of the setup will need to be created by the spiff3D integrations team.

Installation Process
The merchant will install the spiff plugin app from the Neto add-on store which will redirect them to a page asking them to sign into their store account for verification. Image reference  below.
 
Once the user enters their details they will then be redirected to the Spiff hub front page with a new integration and partner.
You can now explore the hub as you wish! To edit your account details simply head to Partner → My Account and you will be greeted with an array of options.
Setting up the Webhook
To make sure your Neto store is connected to the Spiff webhook you need to navigate back to your Neto store. Once in the store on your left side panel navigate to All Settings & Tools.
You will be greeted with a search bar where you will enter API Settings. Click on it and that will redirect you to a page where we can enable the webhook and enter a custom url that will notify Spiff when an order has been placed.
You want to toggle the Enable Neto API Webhook option and you then want to add in the custom webhook url into the Neto API webhook URL. That custom webhook will be https://hub.spiff.com.au/shadow/neto/webhook/{integrationId}. The integration id is to ensure that Spiff understands what store has hit the url on our side so that we can process the order correctly. After you have added in all details remember to press Save changes.
Setting up Design Products
To set up a design product on Neto we first need to create a parent container product that will hold all the different variants your customers will create. The parent products will be displayed on your store in which customers will use to initialise the workflow experience. To do this we need to navigate to the Products section inside the Neto c-panel.
If its your first time adding a new product you want to click that big green button in the middle of the screen to begin the process of adding a parent container for your design products.
If you have products already created in your store you want to then click the Add new product button on the top right hand side of the page to start creating our parent container product.
You want to then toggle Product with Variations under New Product section
Toggle Webstore under Sales Channels
Toggle Active under Product status
Add a name for your product under New Parent Product (eg. Shoe, t-shirt)
Add a price for your product (This price must be the same price of the spiff product created in hub under Base price) under Pricing
Add a Image(s) for the product under Images
Add a SKU for your product under Inventory (eg. spiff3d)
Any other details that need to be added feel free to do so. To set up the design products this is all the information we are gonna need. Proceed to click Continue setup button on the bottom right hand side of the page.
Setting up Custom Script
At this point we have successfully created a new parent product but how do we get the spiff button to render on our page so we can click on it and initialise the experience? To do this we need to add some custom code in our Neto Custom Script section. But before we proceed to add our custom code we need to navigate to the Webstore Templates section in our Neto c-panel via the Settings & Tools.
Upon clicking into this section we are greeted with the stores template code. We specifically want to edit the product templates. Navigate to Web Themes → storefront → templates → products → includes → buying_options.template.html. If successful you should see this page down below.
Press onto any line in the code so we can start editing. If you are on a Mac press Command + F and if you are on Windows press Ctrl + F to bring up a search bar in the top right hand side of the code. Enter into the search bar add to cart to direct you to the correct area of the code we want to edit.
Add the block of code below to create a space where we can place our spiff button via the custom script.
1<div id='spiff-product'></div>
We then want to add the next block of code onto the add to cart button so we can hide the button once our spiff button renders.
1data-spiff-hide data-product-id="[@SKU@]"
You code should look something like this:
Once we have finished editing this template we want to save and navigate back to the template page we were on before. This time navigate to Web Themes → storefront → templates → products → includes → child_products.template.html. If successful you should see this page down below.
You want to then add this block of code on line 2.
1 <div id='spiff-product'></div>
Remember to save and quit once you have edited the code.
Your code should look something like this.
We have finished editing the template files. Now we need to navigate to the Custom Scripts section via Settings & Tools from the left side bar. Then search for Custom scripts and click onto it. If successful you should see the page below.
Press on the Add New button to add a new custom script into our store.
Name the custom script something like Spiff-Button-Design-Product.
At the bottom of the page press on Product page (under description)
Add this block of code in the field and press Save in the bottom right hand side of the page (Follow instructions by Neto to save the script and always double check to see if your changes have been saved)

```1<script type="text/javascript" async src="https://hub.spiff.com.au/cdn/api.js"></script>
2
3<script>
4var pageSessionId;
5var openDisplayProductWorkflowForProduct[@SKU@];
6window.addEventListener('SpiffApiReady', function() {
7const product = new window.Spiff.Product({
8  integrationId: '[@config:host_name@]',
9  productId: '[@sku@]'
10});
11
12const hideElements = () => {
13           const elements = document.querySelectorAll('[data-spiff-hide]');
14           elements.forEach(el => {
15               const externalProductId = el.getAttribute('data-product-id');
16               if (externalProductId === '[@sku@]') {
17                   el.style.display = 'none';
18               }
19           });
20       }
21
22 product.on('ready', () => {
23             hideElements();
24             const buttons = document.querySelectorAll('.spiff-api-button[data-product-id="[@sku@]"]');
25console.log(buttons);
26             if (pageSessionId === undefined){
27                pageSessionId = window.Spiff.Analytics.createPageSession();
28             }
29             for (button of buttons) {
30                 button.style.display = 'block';
31             }
32       });
33       product.confirmActive();
34
35openDisplayProductWorkflowForProduct[@sku@] = (event) => {
36           event.target.disabled = true;
37           event.preventDefault();
38           event.stopPropagation();
39
40            const spinnerSvg = document.createElementNS('http://www.w3.org/2000/svg', 'svg');
41            spinnerSvg.setAttribute('height', event.target.clientHeight * 0.4);
42            spinnerSvg.setAttribute('width', event.target.clientHeight * 0.4);
43            spinnerSvg.setAttribute('viewBox', '0 0 66 66');
44            spinnerSvg.animate([{transform: 'rotate(0deg)'},{transform: 'rotate(360deg)'}], {duration: 1000, iterations: Infinity});
45            const spinnerCircle = document.createElementNS('http://www.w3.org/2000/svg', 'circle');
46            spinnerCircle.setAttribute('cx', 33);
47            spinnerCircle.setAttribute('cy', 33);
48            spinnerCircle.setAttribute('fill', 'none');
49            spinnerCircle.setAttribute('r', 30);
50            spinnerCircle.setAttribute('stroke', 'black');
51            spinnerCircle.setAttribute('stroke-width', 6);
52            spinnerCircle.style = 'stroke-dasharray:45 180;';
53            spinnerSvg.appendChild(spinnerCircle);
54            event.target.appendChild(spinnerSvg);
55
56           const transactionOptions = {
57               presentmentCurrency: '[@config:defaultcurrency@]',
58               product: product,
59               shouldCreateDesignProduct: true,
60               pageSessionId
61           };
62           const transaction = new window.Spiff.Transaction(transactionOptions);
63           transaction.on('quit', () => {
64               event.target.removeChild(spinnerSvg);
65               event.target.disabled = false;
66               console.log("The user exited before completing their design");
67           });
68           transaction.on('complete', async (result) => {
69           document.getElementById("spiff-product").innerHTML = `
70                    <input type="hidden" id="spiff_sku" value='${result.designProductId}' />
71                     <input type="hidden" id="spiff_qty" value='1' />
72              `;
73             $.addCartItem('spiff_sku','spiff_qty');
74             event.target.removeChild(spinnerSvg);
75             event.target.disabled = false;
76           });
77           transaction.execute();
78       };
79});
80</script>
81    <script>
82        document.getElementById("spiff-product").innerHTML = `
83            <button
84                    class='spiff-api-button'
85                    id='spiff-product'
86                    data-product-id='[@sku@]'
87                    onclick="openDisplayProductWorkflowForProduct[@sku@](event)"
88                    style="display: none;color:#ffffff;background-color:#e12929;border-radius:4px;height:46px;width:100%;font-size:16px;font-family:Barlow,Arial,Helvetica;font-weight:600;"
89                >
90                Customise Now
91               </button>
92        `;
93    </script>
 ```
Syncing Spiff Product with Neto Product
The last step to this long journey is to now sync the spiff product created in Hub with your new parent container product. This syncing will allow the button to render on the correct page with the correct workflow it has been assigned.
To do this we need to navigate back to hub by pressing on the Configure button on the Spiff add-on in the add-on store. Once in Hub navigate to Store → Products via the nav bar and you will either see a list of created products or no products.
Click on a product you wish to sync to Neto and scroll down to Product Integrations.
Add a product integration (which will be the new integration that has been created for you) and press on the 3 dots next to your integration to edit your External Product Id. This Id will be the SKU you have given to your parent container product in Neto. Press Save changes and you should now see your button rendered on the product page in Neto.
