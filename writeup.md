#**Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images/solidWhiteCurve_2.jpg
[image2]: ./test_images/solidWhiteRight_2.jpg
[image3]: ./test_images/whiteCarLaneSwitch_2.jpg
[image4]: ./test_images/solidYellowCurve_2.jpg
[image5]: ./test_images/solidYellowCurve2_2.jpg
[image6]: ./test_images/solidYellowLeft_2.jpg


---

### Reflection

###1. Describe the pipeline.

My pipeline consisted of the following steps. 

1. Convert the images to grayscale.
2. Apply Gaussian smoothing
3. Apply Canny to find egdes of the images
4. Apply mask to the images
5. Apply Hough transform to find the lines
6. Draw single lines based on hough lines

In order to draw a single line on the left and right lanes, I modified the draw_lines() function as follows:
1. Seperate line segments by their slope: the line segments are filtered and seperated by the left line (-1 < slope < -0.5) and right line (0.5 < slope < 1)  
2. Average the position of each of the lines: average all the positions of points (x1,y1,x2,y2) and average the slope of each line segments
3. Extrapolate to the top and bottom of the lane: the top will be y = 325 and bottom will be y = 540

The following are images with single lines detected after pipeline: 

![alt text][image1]
![alt text][image2]
![alt text][image3]
![alt text][image4]
![alt text][image5]
![alt text][image6]


###2. Potential shortcomings with the current pipeline


One potential shortcoming would be what would happen when the lines from the original image are not positioned correctly within the mask, such as the video from challenge.mp4



###3. Suggest possible improvements to the pipeline

A possible improvement would be to adjust the mask, tune the parameters in the pipeline and change the accept range of the slope.