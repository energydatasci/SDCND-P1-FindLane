# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/crossing.png "Crossing"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I used canny edge detection to detect the lanes. Thirdly, based on a region of interest defined by a polygon, the edges/lanes are further filtered. In the fourth step, I applied Hough transform on these filtered edges to get the lines with similar gradients/directions. Lastly, I overlay the detected lane edges onto the original image. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by seperating left lanes from right lanes. Since the camera sits in the center of the road, the left lanes will have negative gradient while right lanes will have positive gradients. Then I interploated additional points for both left lanes and right lanes since there are gaps between the lanes. Finally I removed the points after right lane and left lane cross over (those points are not of our interest) and plotted the line . 


![example showing the unnecessary lines after right lane and left lane cross over][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there are objects with similar colors as the lane mark on the pavements. Since current pipeline can not filter that out, and that objects could be very likely joined with the lane mark. 

Another shortcoming could be the hard coded region of interested, in situations with big turns, the area of interest could change dramatically. 

A big shortcoming with current pipeline is that it is highly likely to fail during night time.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to combine the color selector as the yellow curve is distinctive from pavement colors. 

Another potential improvement could be to train the right thresholds and other parameters under different weather and lights.
