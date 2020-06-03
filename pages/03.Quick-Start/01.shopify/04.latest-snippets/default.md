---
title: 'Latest Snippets'
---

If your snippets are outdated, you can update them by overwriting them with the versions listed here.

# snippets/spiff-button-design-product.liquid

```liquid
{% assign product_object = all_products[product_handle] %}
  <script>
    var openDisplayProductWorkflowForProduct{{product_object.id}};
    window.addEventListener('SpiffApiReady', function() {
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
            for (button of buttons) {
                button.style.display = 'block';
              }
      });
      product.confirmActive();
      openDisplayProductWorkflowForProduct{{product_object.id}} = (event) => {
          event.preventDefault();
          event.stopPropagation();
          const transactionOptions = {
              presentmentCurrency: '{{cart.currency.iso_code}}',
              product: product,
              shouldCreateDesignProduct: true
          };
          const transaction = new window.Spiff.Transaction(transactionOptions);
          transaction.on('quit', () => {
              console.log("The user exited before completing their design");
          });
          transaction.on('complete', async (result) => {
            const lineItemProperties = {
              ...result.designMetaData.metadata
            };
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
    style="display:none;color:{% if label_colour %}{{label_colour}}{% else %}#FFFFFF{% endif %};background-color:{% if background_colour %}{{background_colour}}{% else %}rgb(214, 27, 92){% endif %};"
>
  {% if label_text %}{{label_text}}{% else %}Customise now on #spiff{% endif %}
</button>
```

# snippets/spiff-button-standard.liquid

```liquid
{% assign product_object = all_products[product_handle] %}
  <script>
    var openStandardWorkflowForProduct{{product_object.id}};
    window.addEventListener('SpiffApiReady', function() {
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
            for (button of buttons) {
                button.style.display = 'block';
              }
      });
      product.confirmActive();
      openStandardWorkflowForProduct{{product_object.id}} = (event) => {
          event.preventDefault();
          event.stopPropagation();
          const transactionOptions = {
              presentmentCurrency: '{{cart.currency.iso_code}}',
              product: product,
              shouldCreateDesignProduct: false
          };
          const transaction = new window.Spiff.Transaction(transactionOptions);
          transaction.on('quit', () => {
              console.log("The user exited before completing their design");
          });
          transaction.on('complete', async (result) => {
            const lineItemProperties = {
              ...result.designMetaData.metadata
            };
            lineItemProperties.spiffTransactionId = result.transactionId;
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
    style="display:none;color:{% if label_colour %}{{label_colour}}{% else %}#FFFFFF{% endif %};background-color:{% if background_colour %}{{background_colour}}{% else %}rgb(214, 27, 92){% endif %};"
>
  {% if label_text %}{{label_text}}{% else %}Customise now on #spiff{% endif %}
</button>
```