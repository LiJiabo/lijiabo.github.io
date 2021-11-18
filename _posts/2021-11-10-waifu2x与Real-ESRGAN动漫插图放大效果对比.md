---
layout: article
title: waifu2x与Real-ESRGAN动漫插图放大效果对比
tags: 技术 图片放大
sharing: true
key: 8CFD3759-E431-4DCC-699E-3C2E37CB050D
lang: zh
permalink: 2021/11/10/waifu2xAndRealESRGANCompare.html
---
### 原图1

![IMG_1206](https://oss.ljbmedia.top/uPic/2021/11/18/IMG_1206.JPG)

### waifu2x

##### 模型：PAN 降噪等级：0 放大：4x 输出格式：JPEG 品质：90

![IMG_1206_pan_anime_fast_noise0_4x](https://oss.ljbmedia.top/uPic/2021/11/18/IMG_1206_pan_anime_fast_noise0_4x.jpg)

### Real-ESRGAN

##### 模型：realesrgan-x4plus-anime 放大：4x 输出格式：JPEG 其他默认

![IMG_1206_out](https://oss.ljbmedia.top/uPic/2021/11/18/IMG_1206_out.JPG)



### 原图2

![IMG_1208](https://oss.ljbmedia.top/uPic/2021/11/18/IMG_1208.JPG)

### waifu2x

##### 模型：PAN 降噪等级：0 放大：4x 输出格式：JPEG 品质：90

![IMG_1208_pan_anime_fast_noise0_4x](https://oss.ljbmedia.top/uPic/2021/11/18/IMG_1208_pan_anime_fast_noise0_4x.jpg)

### Real-ESRGAN

##### 模型：realesrgan-x4plus-anime 放大：4x 输出格式：JPEG 其他默认

![IMG_1208_out](https://oss.ljbmedia.top/uPic/2021/11/18/IMG_1208_out.JPG)



可见waifu2x基本就是简单的超采样，而Real-ESRGAN类似于“AI脑补”，能够真正让插图模糊的部分变得更清晰，类似一个画家把模糊的部分变得清晰之后的样子想象了出来，再画上去。不过其缺点就是文件大小会更大。

