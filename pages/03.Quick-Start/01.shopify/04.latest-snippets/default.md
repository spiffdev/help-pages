---
title: 'Latest Snippets'
---

If your snippets are outdated, you can update them by overwriting them with the versions listed here.

# snippets/spiff-button-design-product.liquid

```liquid
 {% assign product_object = all_products[product_handle] %}
   <style>
     .spiff-spinner-outer {
       animation: rotator 1s linear infinite;
     }
     .spiff-spinner-inner {
       stroke-dasharray: 45 180;
     }
     @keyframes rotator {
       0% { transform: rotate(0deg); }
       100% { transform: rotate(360deg); }
     }
   </style>
   <script>
     var openDisplayProductWorkflowForProduct{{product_object.id}};
     window.addEventListener('SpiffApiReady', function() {
     var pageSessionId;
       const product = new window.Spiff.Product({
           integrationId: '{{shop.permanent_domain}}',
           productId: '{{product_object.id}}'
       });
       const hideElements = () => {
           const elements = document.querySelectorAll('[data-spiff-hide]');
           elements.forEach(el => {
               const externalProductId = el.getAttribute('data-product-id');
               if (externalProductId === '{{product_object.id}}') {
                   el.style.display = 'none';
               }
           });
       }
       product.on('ready', () => {
             hideElements();
             const buttons = document.querySelectorAll('.spiff-api-button[data-product-id="{{product_object.id}}"]');
             pageSessionId = window.Spiff.Analytics.createPageSession();
             for (button of buttons) {
                 button.style.display = 'block';
             }
       });
       product.confirmActive();
       openDisplayProductWorkflowForProduct{{product_object.id}} = (event) => {
           event.target.disabled = true;
           event.preventDefault();
           event.stopPropagation();

           const spinnerSvg = document.createElementNS('http://www.w3.org/2000/svg', 'svg');
           spinnerSvg.setAttribute('class', 'spiff-spinner-outer');
           spinnerSvg.setAttribute('height', event.target.clientHeight);
           spinnerSvg.setAttribute('width', event.target.clientHeight);
           spinnerSvg.setAttribute('viewBox', '0 0 66 66');
           const spinnerCircle = document.createElementNS('http://www.w3.org/2000/svg', 'circle');
           spinnerCircle.setAttribute('class', 'spiff-spinner-inner');
           spinnerCircle.setAttribute('cx', 33);
           spinnerCircle.setAttribute('cy', 33);
           spinnerCircle.setAttribute('fill', 'none');
           spinnerCircle.setAttribute('r', 30);
           spinnerCircle.setAttribute('stroke', 'black');
           spinnerCircle.setAttribute('stroke-width', 6);
           spinnerSvg.appendChild(spinnerCircle);
           event.target.appendChild(spinnerSvg);

           const transactionOptions = {
               presentmentCurrency: '{{cart.currency.iso_code}}',
               product: product,
               shouldCreateDesignProduct: true,
               pageSessionId
           };
           const transaction = new window.Spiff.Transaction(transactionOptions);
           transaction.on('quit', () => {
               event.target.removeChild(spinnerSvg);
               event.target.disabled = false;
               console.log("The user exited before completing their design");
           });
           transaction.on('complete', async (result) => {
             const lineItemProperties = {
                 spiffTransactionId: result.transactionId,
                 previewImage: result.previewImage
             };
             const keys = Object.keys(result.exportedData);
             for (const key of keys) {
                 lineItemProperties[key] = result.exportedData[key].value;
             }
             const addToCartRequestBody = JSON.stringify({
               quantity: 1,
               id: result.designProductVariantId,
               properties: lineItemProperties
             });
             await fetch('/cart/add.js', {
               method: 'POST',
               body: addToCartRequestBody,
               headers: { 'Content-Type': 'application/json' }
             });
             event.target.removeChild(spinnerSvg);
             event.target.disabled = false;
             {% if redirect_to_cart %}window.top.location.href = '/cart';{% endif %}
           });
           transaction.execute();
       };
     });
   </script>
 <button
     class='spiff-api-button'
     data-product-id='{{product_object.id}}'
     onclick="openDisplayProductWorkflowForProduct{{product_object.id}}(event)"
     style="
            display:none;
            color:{% if label_colour %}
              {{label_colour}}
            {% else %}
              #FFFFFF
            {% endif %};
            background-color:{% if background_colour %}
              {{background_colour}}
            {% else %}
              rgb(214, 27, 92)
            {% endif %};
            {% if height %}height:{{height}};{% endif %}
            {% if width %}width:{{width}};{% endif %}
            "
 >{% if label_text %}{{label_text}}{% else %}Customise now on #spiff{% endif %}</button>
```

# snippets/spiff-button-standard.liquid

```liquid
{% assign product_object = all_products[product_handle] %}
   <style>
     .spiff-spinner-outer {
       animation: rotator 1s linear infinite;
     }
     .spiff-spinner-inner {
       stroke-dasharray: 45 180;
     }
     @keyframes rotator {
       0% { transform: rotate(0deg); }
       100% { transform: rotate(360deg); }
     }
   </style>
   <script>
     var openStandardWorkflowForProduct{{product_object.id}};
     window.addEventListener('SpiffApiReady', function() {
     var pageSessionId;
       const product = new window.Spiff.Product({
           integrationId: '{{shop.permanent_domain}}',
           productId: '{{product_object.id}}'
       });
       const hideElements = () => {
           const elements = document.querySelectorAll('[data-spiff-hide]');
           elements.forEach(el => {
               const externalProductId = el.getAttribute('data-product-id');
               if (externalProductId === '{{product_object.id}}') {
                   el.style.display = 'none';
               }
           });
       }
       product.on('ready', () => {
             hideElements();
             pageSessionId = window.Spiff.Analytics.createPageSession();
             const buttons = document.querySelectorAll('.spiff-api-button[data-product-id="{{product_object.id}}"]');
             for (button of buttons) {
                 button.style.display = 'block';
             }
       });
       product.confirmActive();
       openStandardWorkflowForProduct{{product_object.id}} = (event) => {
           event.target.disabled = true;
           event.preventDefault();
           event.stopPropagation();

           const spinnerSvg = document.createElementNS('http://www.w3.org/2000/svg', 'svg');
           spinnerSvg.setAttribute('class', 'spiff-spinner-outer');
           spinnerSvg.setAttribute('height', event.target.clientHeight);
           spinnerSvg.setAttribute('width', event.target.clientHeight);
           spinnerSvg.setAttribute('viewBox', '0 0 66 66');
           const spinnerCircle = document.createElementNS('http://www.w3.org/2000/svg', 'circle');
           spinnerCircle.setAttribute('class', 'spiff-spinner-inner');
           spinnerCircle.setAttribute('cx', 33);
           spinnerCircle.setAttribute('cy', 33);
           spinnerCircle.setAttribute('fill', 'none');
           spinnerCircle.setAttribute('r', 30);
           spinnerCircle.setAttribute('stroke', 'black');
           spinnerCircle.setAttribute('stroke-width', 6);
           spinnerSvg.appendChild(spinnerCircle);
           event.target.appendChild(spinnerSvg);

           const transactionOptions = {
               presentmentCurrency: '{{cart.currency.iso_code}}',
               product: product,
               shouldCreateDesignProduct: false,
               pageSessionId
           };
           const transaction = new window.Spiff.Transaction(transactionOptions);
           transaction.on('quit', () => {
               event.target.removeChild(spinnerSvg);
               event.target.disabled = false;
               console.log("The user exited before completing their design");
           });
           transaction.on('complete', async (result) => {
             const lineItemProperties = {
                 spiffTransactionId: result.transactionId,
                 previewImage: result.previewImage
             };
             const keys = Object.keys(result.exportedData);
             for (const key of keys) {
                 lineItemProperties[key] = result.exportedData[key].value;
             }
             const firstVariantId = '{{product_object.variants[0].id}}';
             const addToCartRequestBody = JSON.stringify({
               quantity: 1,
               id: firstVariantId,
               properties: lineItemProperties
             });
             await fetch('/cart/add.js', {
               method: 'POST',
               body: addToCartRequestBody,
               headers: { 'Content-Type': 'application/json' }
             });
             event.target.removeChild(spinnerSvg);
             event.target.disabled = false;
             {% if redirect_to_cart %}window.top.location.href = '/cart';{% endif %}
           });
           transaction.execute();
       };
     });
   </script>
 <button
     class='spiff-api-button'
     data-product-id='{{product_object.id}}'
     onclick="openStandardWorkflowForProduct{{product_object.id}}(event)"
     style="
            display:none;
            color:{% if label_colour %}
              {{label_colour}}
            {% else %}
              #FFFFFF
            {% endif %};
            background-color:{% if background_colour %}
              {{background_colour}}
            {% else %}
              rgb(214, 27, 92)
            {% endif %};
            {% if height %}height:{{height}};{% endif %}
            {% if width %}width:{{width}};{% endif %}
            "
 >{% if label_text %}{{label_text}}{% else %}Customise now on #spiff{% endif %}</button>
```

# snippets/spiff-line-item-image.liquid

```liquid
					{% for property in line_item.properties %}
                        {% if property.first == "spiffTransactionId" %}
                            <span class='spiff-line-item-image-container' data-spiff-transaction-id="{{ property.last }}">
                            </span>
                            {% assign hasTransactionId = true %}
                        {% endif %}
                        {% if property.first == "previewImage" %}
                            <img src="{{ property.last }}" alt="{{ line_item.title }}" />
                        {% endif %}
                    {% endfor %}
                    {% unless hasTransactionId %}
                        <img class="cart__image{% if line_item.image == null %} hide{% endif %}" src="{{ line_item | img_url: 'x190' }}" alt="{{ line_item.image.alt | escape }}" data-cart-item-image>
                    {% endunless %}
```