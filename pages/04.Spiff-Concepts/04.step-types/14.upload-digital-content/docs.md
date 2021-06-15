---
title: 'Upload Digital Content'
media_order: 'Screen Shot 2021-06-15 at 11.27.22 am.png'
---

## Digital Content Step

This step gives your customers the option to embed **QR codes** that play videos on a web page of your choosing couldn't be easier.

![](https://help.spiff.com.au/user/pages/04.Spiff-Concepts/04.step-types/14.upload-digital-content/Screen%20Shot%202021-06-15%20at%2011.27.22%20am.png)

### How To Create

#Web Page
First, let's prepare the web page that'll have the embedded video.

##HTML
On the HTML side of things, you only need a HTML video tag with the id 'spiffEmbeddedVideo'.
```
<video controls id="spiffEmbeddedVideo" >
  Sorry, your browser doesn't support embedded videos.
</video>
```
In our example, we added a little message for browsers that don't support this feature. Most do, so this is just a message for the few people of very small number of devices.

##JavaScript
The last thing to do is add our JavaScript snippet either to the page or as a reference JS file.

Here's what the JavaScript looks like:
```
window.addEventListener('load', (event) => {
  const urlParams = new URLSearchParams(window.location.search);
  const myParam = urlParams.get('video');

  const decoded = atob(myParam);

  const video = document.getElementById("spiffEmbeddedVideo");

  try{
    new URL(decoded);
    video.src = decoded;
  } catch (_) {
    const links = JSON.parse(decoded);
    links.forEach(function (item){

      const source = document.createElement('source');
      source.src = item.href;

      video.appendChild(source)
    })
  }

  video.onended = function() {
    if (document['exitFullscreen']) {
      document['exitFullscreen']();
    } else if (document['webkitExitFullscreen']) {
      document['webkitExitFullscreen']();
    } else if (document['mozCancelFullScreen']) {
      document['mozCancelFullScreen']();
    } else if (document['msExitFullscreen']) {
      document['msExitFullscreen']();
    }
    document.getElementById("overlay").style.zIndex = "2";
  }
});

function replaySpiffEmbeddedVideo(){
  document.getElementById("overlay").style.zIndex = "-1";
  document.getElementById("video").play();
}
```

One tidy approach is to create a new JavaScript file, calling it what you like, and pasting the above code into it.

Lets say we call it `spiffEmbeddedVideo.js`.

Then in your HTML page where you have the video tag, add a reference to this new file:
```
<!doctype html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="">
    <script type="text/javascript" src="spiffEmbeddedVideo.js"></script>
</head>
<body>

    <video controls id="spiffEmbeddedVideo" >
        Sorry, your browser doesn't support embedded videos.
    </video>

</body>
</html>
```

**Done!** Now the web page is ready, we'll set things up on Spiff's side.

#Digital Content Step
In the Experience Builder, add a Digital Content Step to a Scene.

Select the Config tab.

In the Base URL box, type in the URL of the page that will play the video content.

Done!

#Fin
Once you're done building your Experience, your customers will be able to upload video, which will then create a QR code.

When scanned, this QR code will link to the the URL you provided and play the video.