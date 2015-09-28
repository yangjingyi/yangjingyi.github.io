---
layout: post
title: Matlab image editing 2:The important functions
categories: [general, setup, demo]
tags: [demo, dbyll, dbtek, setup]
fullview: true
---
**Important functions**

1. **Imfinfo** 得到图片信息如 Filename, FileModeDate, FileSize, Format, FormatVersion, Width, Height, BitDepth and ColorType.

  Example:

  info = imfinfo('canoe.tif')
  
2. **imshow** 显示图片

    Example:

    clear all;
    I = imread('rice.png');
    %灰度范围[100,200]显示图像
    subplot(1,2,1);imshow(I,[100,190]);
    %灰度等级25显示图像
    subplot(1,2,2);imshow(I,25);
  
    图像经过处理值域不确定：

    imshow(I,[])
    
3. **warp** 


    clear all;
    [x,y,z] = cylinder;
    load clown;
    warp(x,y,z,map);
    colormap(map);

