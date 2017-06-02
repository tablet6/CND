# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidwhiteright.jpg
[image2]: ./test_images_output/solidWhiteCurve.jpg
[image3]: ./test_images_output/solidYellowCurve.jpg
[image4]: ./test_images_output/solidyellowcurve2.jpg
[image5]: ./test_images_output/solidYellowLeft.jpg
[image6]: ./test_images_output/whiteCarLaneSwitch.jpg

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

#### Pipeline stages:
1. Convert input image to gray scale and apply Guassian Blur.

2. Apply Canny's Edge Detection algorithm to the image at step 1.

3. Mask out the image output of Canny's with a "region-of-interest".

4. Use Hough algorithm to drawlines() using image at Step3.

5. Combine the image at step 4 with original image to overlay lines on the lanes.

#### Extended draw_lines() to draw 2 single lines for the 2 lanes.
1. Identify line segments that fall on the left lane and right lane.

2. Find mid-point of each line segment and save the mid-points in a left_list and a right_list.

3. Find max y tuple and min y tuple points in each list.

4. Based on the slope, find out a point on the bottom part of image and upper part of the "region-of-interest" for each list.

5. Draw a line with the 2 points generated at 4.


![alt text][image1]
![alt text][image2]
![alt text][image3]
![alt text][image4]
![alt text][image5]
![alt text][image6]


### 2. Identify potential shortcomings with your current pipeline

1. Right now there are some frames where the lanes cross-over and are not exactly aligned. I should identify those points in the list I generated and skip using them in identifying a lane.

2. Another issue, is this method will not work for curvy roads. So a region-of-interest needs to be adjusted as well.
Probably use Bezier curves instead of lines to handle curved lanes.


### 3. Suggest possible improvements to your pipeline

1. Being a Python amateur, I am not sure if there are better math libraries to identify lines from a set of line segments.

2. Found this on Slack: https://peteris.rocks/blog/extrapolate-lines-with-numpy-polyfit/
   Did not look into it to implement my solution, but I will after this submission.

3. Not happy with my implementation. This code doesn't scale well :-(, if the examples change. Case in point: Optional video.
