---
title: 'Spiff displays user login in shopify admin'
media_order: 'Screen Shot 2021-03-01 at 11.06.15 am.png,Screen Shot 2021-03-01 at 11.16.19 am.png,Screen Shot 2021-03-01 at 11.21.13 am.png,Screen Shot 2021-03-01 at 11.23.48 am.png'
visible: true
---

When a user logs in to Spiff through their shopify admin panel on rare occasions you will be displayed with a usr login screen.  
![](https://help.spiff.com.au/user/pages/08.troubleshooting/spiff-displays-user-login-in-shopify-admin/Screen%20Shot%202021-03-01%20at%2011.16.19%20am.png)
This shouldnt happen as the shopfiy store name (yourstore.myshopify.com) should always be the logged in user when you view spiff through the admin panel.

To Fix this issue, whilst you are on the login screen

1. Right click on the grey area of the spiff screen and a menu will open  
2. Select Inspect from the menu 
![](https://help.spiff.com.au/user/pages/08.troubleshooting/spiff-displays-user-login-in-shopify-admin/Screen%20Shot%202021-03-01%20at%2011.24.55%20am.png)  
3. On the right hand side of the screen select Applications 
![](https://help.spiff.com.au/user/pages/08.troubleshooting/spiff-displays-user-login-in-shopify-admin/Screen%20Shot%202021-03-01%20at%2011.21.13%20am.png)
4. Click on the local storage drop down, select the 'app.spiff.com.au' line then click the clear icon as highlighted below. Repeat this process for the session storage  
![](https://help.spiff.com.au/user/pages/08.troubleshooting/spiff-displays-user-login-in-shopify-admin/Screen%20Shot%202021-03-01%20at%2011.23.48%20am.png)
5. Close the inspector and reload the page and you will now be logged in correctly 
![](https://help.spiff.com.au/user/pages/08.troubleshooting/spiff-displays-user-login-in-shopify-admin/Screen%20Shot%202021-03-01%20at%2011.06.15%20am.png)

To watch a video on how this is done click below 
[plugin:youtube](https://youtu.be/L4UNyWmcycU)
If this does not solve your problem please contact support on the following link spiff3d.com/contact-us 





