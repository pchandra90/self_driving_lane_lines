# **Finding Lane Lines on the Road** 

## Problem statement

### Identify lane lines on the road for self driving car. For self driving car we will have video stream through camera and we have to mark lane line. In this project video is input not live stream. Obviously with minor modification can be used in live stream.

---

## Solution overview

### First we will identify lane line in a single image, then apply to series of images (video). So explaining finding lane line in single images will be sufficient.

---

[//]: # (Image References)

[original_image]: ./writeup_images/original_image.jpg
[gray_image]: ./writeup_images/gray_image.jpg
[blur_gray]: ./writeup_images/blur_gray.jpg
[edges]: ./writeup_images/edges.jpg
[mask_edges]: ./writeup_images/mask_edges.jpg
[line_image]: ./writeup_images/line_image.jpg
[final_img]: ./writeup_images/final_img.jpg


### Reflection

### 1. Solution pipeline

Pipe line consist of following steps:

- Original image

![alt text][original_image]

- Converted into grayscale

![alt text][gray_image]

- Gaussian blur of grayscale image

![alt text][blur_gray]

- Canny edge detection on gaussian blured image

![alt text][edges]

- As we can see, we are not interested in all edges. So I have used a quadrilateral to masked edges outside it. 

![alt text][mask_edges]

- This masked edges is to find hough line. We can see that right side lines are broken. 
There may be left side broken line as well. For fixing this we devide all line into two parts left and right.
Further left and right devided into two parts (further left right on the basis of slope). For all four parts we 
completed the missing part of lines. 

![alt text][line_image]

- Conbine original input image with completed line image.

![alt text][final_img]

---

### 2. Shortcomings

- In case of curved lanes, masking edges befor hough line is not sufficient. Frurther masking is done on hough line image.
Sitll need to improve it.
- Some times lane lines are very lightly or nit visible, in this case it is not working properly.
- If road is dirty by some other means, in this case unwanted lines is being detected.

### 3. Possible improvements

- Experiment more with hough line functionality of opencv to fix unwanted line. This will fix maximum shortcomings mentioned
above














