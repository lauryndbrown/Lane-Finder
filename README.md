# **Finding Lane Lines on the Road** 

This code uses Hough Transform to find highway road lane lines from the results of Canny Edge Dection.
## Running Code
1. `source activate carnd-term1`
2. `jupyter notebook P1.ipynb`
### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My image processing pipeline consists of the following steps:
1. Convert image to grayscale
2. Apply Canny edge detection
3. Apply a Region of Interest Mask
4. Use Hough Transform to Find Lines from Canny Edges
5. Find the best fit line of the endpoints of the results of the Hough Transform 
6. Draw lines on a blank image of the same size. 
7. Draw the lines onto the original image 



In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:
1. Grouping the lines into two categories (right and left) by checking if the slope was positive or negative.
As well as throwing out any lines without an "extreme" slope.
2. Using numpy's polyfit and poly1d functions I find the best fit line with the points for both the right and left sides individually.


### 2. Identify potential shortcomings with your current pipeline
One potential shortcoming would be what would happen when there is a different image format than the given
input. My algorithm is very dependent on knowing the placement of the camera and the layout of the image. 

Another shortcoming could be the dependence on clear lane lines in the image. In real road conditions the 
lane is not always perfectly marked. Old lane lines, road debree, other car and objects could obstruct the 
view of the lines and cause the program to give incorrect output.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use a more advanced technique for finding the lanes so that the placement is
not so dependent on camera placement.

Another potential improvement could be to create a more sophisticated algorithm for extrapolating the lane lines
given the photo's context. You could use previous photos seen or the placement of other cars as well as the 
width of your car compared to with width of the road to better determine where the lanes might be if they are
not visible.
