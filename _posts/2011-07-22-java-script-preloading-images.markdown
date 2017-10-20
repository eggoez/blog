---
layout: post
date: 2011-07-22 17:18:35 +0700
title: Java Script Preloading Images
categories: asal
tags: JavaScript code
---
<p>Lots of high-res images can really spruce up a Web site. Butthey can also slow it down—images are files, files use bandwidth, and bandwidthis directly related to wait times. It’s time you get yourself an education onhow to speed things up with a little trick called image preloading.</p>
<h1>Image preloading</h1>
<p>The way a browser normally works, images are loaded onlyafter an HTTP request is sent for them, either passively via an &lt;img&gt; tagor actively through a method call. So if you have JavaScript that swaps an imageon mouseover, or changes an image automatically after a timeout, you can expectto wait anywhere from a few seconds to a few minutes while the image isretrieved from the server. This is especially noticeable if you have a slowconnection to the Internet, or if the images being retrieved are verylarge…and the delay usually ruins the effect you were hoping for.<br>
<span id="more-444"></span><br>
Some browsers try to mitigate this problem by storing theimages in the local cache so that subsequent calls to the image are satisfiedimmediately…but there’s still a delay the very first time the image isneeded. Preloading is a technique where the image is downloaded to the cachebefore it’s needed. That way when the image is really needed it can beretrieved from the cache and displayed immediately.</p>
<h1>The Image() object</h1>
<p>The simplest way to preload an image is to instantiate a newImage() object in JavaScript and pass it the URL of the image you wantpreloaded. Say we have an image called heavyimagefile.jpg, which we want todisplay when the user mouses over an already-displayed image. In order topreload this image for faster response time, we simply create a new Image()object, called <em>heavyImage</em>, and loadit simultaneously to the page with the onLoad() event handler:</p>
<pre>&lt;html&gt;
&lt;head&gt;
&lt;script language = "JavaScript"&gt;
function preloader()
{
heavyImage = new Image();
heavyImage.src = "heavyimagefile.jpg";
}
&lt;/script&gt;
&lt;/head&gt;
&lt;body onLoad="javascript:preloader()"&gt;
&lt;a href="#" onMouseOver="javascript:document.img01.src='heavyimagefile.jpg'"&gt;
&lt;img name="img01" src="justanotherfile.jpg"&gt;&lt;/a&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>
<p>Note that the image tag does not itself handle onMouseOver()and onMouseOut() events, which is why the &lt;img&gt; tag in the example abovehas been enclosed in an &lt;a&gt; tag, which does include support for thoseevent types.</p>
<h1>Loading multiple images with arrays</h1>
<p>In practice, you will probably need to preload more thanjust one image; for example, in a menu bar containing multiple image rollovers,or if you’re trying to create a smooth animation effect. This is not difficult;all you need to do is make use of JavaScript’s arrays, as in the example below:</p>
<pre>&lt;script language="JavaScript"&gt;

function preloader()
{

&nbsp;&nbsp;&nbsp;&nbsp; // counter
&nbsp;&nbsp;&nbsp;&nbsp; var i = 0;

&nbsp;&nbsp;&nbsp;&nbsp; // create object
&nbsp;&nbsp;&nbsp;&nbsp; imageObj = new Image();

&nbsp;&nbsp;&nbsp;&nbsp; // set image list
&nbsp;&nbsp;&nbsp;&nbsp; images = new Array();
&nbsp;&nbsp;&nbsp;&nbsp; images[0]="image1.jpg"
&nbsp;&nbsp;&nbsp;&nbsp; images[1]="image2.jpg"
&nbsp;&nbsp;&nbsp;&nbsp; images[2]="image3.jpg"
&nbsp;&nbsp;&nbsp;&nbsp; images[3]="image4.jpg"

&nbsp;&nbsp;&nbsp;&nbsp; // start preloading
&nbsp;&nbsp;&nbsp;&nbsp; for(i=0; i&lt;=3; i++)
&nbsp;&nbsp;&nbsp;&nbsp; {
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; imageObj.src=images[i];
&nbsp;&nbsp;&nbsp;&nbsp; }

}

&lt;/script&gt;</pre>
<p>In the above example, you define a variable i and an Image() object cleverly named imageObj. You then define a new arraycalled images[], where each arrayelement stores the source of the image to be preloaded. Finally, you create afor() loop to cycle through the array and assign each one of them to theImage() object, thus preloading it into the cache.<br>
The onLoad() event handler</p>
<p>Like many other objects in JavaScript, the Image() objectalso comes with some event handlers. The most useful of these is undoubtedlythe onLoad() handler, which is invoked when the image has completed loading.This handler can be hooked up with a custom function to perform specific tasksafter the image has completed loading. The following example illustrates thisby displaying a “please wait” screen while the image loads, and thensending the browser to a new URL once it’s finished loading.</p>
<pre>&lt;html&gt;
&lt;head&gt;
&lt;script language="JavaScript"&gt;

// create an image object
objImage = new Image();

// set what happens once the image has loaded objImage.onLoad=imagesLoaded();

// preload the image file
objImage.src='images/image1n.gif';

// function invoked on image load
function imagesLoaded()
{&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp; document.location.href='index2.html';
}

&lt;/script&gt;
&lt;/head&gt;

&lt;body&gt;

Please wait, loading images...

&lt;/body&gt;
&lt;/html&gt;</pre>
<p>Of course, you can also create an array of images and loopover it, preloading each one and keeping track of the number of images loadedat each stage. Once all the images are loaded, the event handler can beprogrammed to take the browser to the next page (or do any other task).</p>
<h1>Preloading and Multi-State Menus</h1>
<p>Now, how about using all the theory you just learned in anactual application? This next one is a little piece of code I recently hadoccasion to write – a menu bar consisting of buttons (image links), each ofwhich can be in any one of three states: normal, hover and click. Since thebuttons have multiple states, it is necessary to use image preloading to ensurethat the menu responds quickly to changes in its state. The code in <strong>Listing A</strong> illustrates this.</p>
<p>The HTML code in Listing A sets up a menu bar consisting offour buttons, each of which has thee states: normal, hover, and click. Therequirements are as follows:</p>
<ul type="disc">
<li>On mouse move over a button in normal state, it changes to hover state. On mouse out, it goes back to normal state.</li>
<li>On mouse click on a button, it changes to its click state. It remains in this state until another button is clicked.</li>
<li>If a button is clicked, no other button may be in click state. Other buttons can only be in their hover or normal states.</li>
<li>Only one button may be clicked at a time.</li>
<li>Only one button can be in hover state at a time.</li>
</ul>
<p>The first task is to set up arrays holding the images foreach state of the menu. The &lt;img&gt; elements corresponding to these arrayelements are also created in the HTML document body, and named sequentially.Note that array values are indexed starting from 0, while the corresponding&lt;img&gt; elements are named starting from 1—this gives rise to certaincalculation adjustments in the latter half of the script.</p>
<p>The preloadImages() function takes care of loading all theimages into the cache, so that response time on mouse movement is minimal. Afor() loop is used to iterate over the images created in the first step andpreload each one.</p>
<p>The resetAll() function is a convenient way to reset all theimages to their normal state. This is necessary because, when an item of themenu is clicked, all other items in the menu must revert to their normal statebefore the clicked item can change to its click state.</p>
<p>The setNormal(), setHover() and setClick() functions takecare of changing the source of a particular image (image number passed asfunction argument) to its normal, hover, or click state respectively. Sinceimages which are clicked must remain in that state until another image isclicked (see rule #2), they are temporarily immune to mouse movements; thus,the setNormal() and setHover() functions include code to only change a button’sstate if it is not already in its click state.</p>
<p>The above is just one of the many ways in which preloadingcan help you speed up the response time of your JavaScript effects. Use thetechniques outlined above in your site, and alter them where needed to fit yourrequirements. Good luck!</p>
<p><a>source</a></p>
