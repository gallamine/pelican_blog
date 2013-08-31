---
layout: post
title: "Show a Colormap Image of a 3D Histogram in MATLAB"
date: 2012-01-19 06:12
comments: true
categories: 
---

This 3d histogram function in matlab, “hist3” sometimes makes visualization difficult, especially if you need to remap the axis or want to view the histogram from the top, down. The easy solution is to convert the histogram to a colormapped image. The code below will do this. It takes 2 arrays, X and Y and takes a histogram of them and maps the histogram values to an image:

```matlab
cnt = hist3([Y X],’Edges’,{edgeXMin:binXSize:edgeXMax edgeYMin:binYSize:edgeYMax});

finalPdf = cnt./max(max(cnt)); % normalize histogram to highest value

imshow(finalPdf,[0 1]) % Show image with min and max values of 0 & 1

colormap(jet); % Change the colormap to make it fancy
```