---
layout: post
title:  "Drawing outline for any kind of HTML Canvas objects"
author: "Shalitha Suranga"
---

Creating an outline for single basic HTML canvas object is very simple since we are able to use `lineWidth` property on canvas context. 
Where as if we need to draw outline for complex object such as combination of basic elements or png image with some transparent portions 
we have to use another approach.

Pixel level manipulation can be used with [`context.getImageData()`](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/getImageData) method which gives pixel data (`r g b a`) of entire canvas

## How Masking method Works


<img src="http://doi.ieeecomputersociety.org/cms/Computer.org/dl/trans/tc/2013/04/figures/ttc20130406311.gif" width="200"/>

Very first I am saving the transparent and non-transparent details to 2D array `A`. 

Thereafter I am using `3x3` mask to detect edges. Mask is sliding over each pixel and if it detects transparent pixel (`a = 255`) it colors every transparent pixel and also the middle pixel. Then the 2D array `B` will be constructed with outline details.

Eventually result will be rendered in the HTML canvas.


Source Code : [https://github.com/shalithasuranga/Canvas-Outlines-Drawing](https://github.com/shalithasuranga/Canvas-Outlines-Drawing)
Working Demo : [http://shalithasuranga.me/Canvas-Outlines-Drawing/](http://shalithasuranga.me/Canvas-Outlines-Drawing/)

Happy Coding!!





















