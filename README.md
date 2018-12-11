# CarND-LaneLines-P1
Project 1 for Udacity's Self-Driving Car Engineer Nanodegree Program

### Finding Lane Lines on the Road

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

| Orginal | Original w/ lane lines |
| --- | --- |
| ![Original](https://github.com/sal-git/CarND-LaneLines-P1/blob/master/images/solidWhiteCurve.jpg?raw=true) | ![New](https://github.com/sal-git/CarND-LaneLines-P1/blob/master/images_output/after-solidWhiteCurve.jpg?raw=true) |

# Reflections

### The pipeline

The pipeline went through a series of steps:
1. OpenCV gray scale
2. OpenCV Gaussian Blur
3. OpenCV Canny function
4. Create a masked area to focus on 
5. Hough lines and modify `draw_lines()` to draw one straight line

  >Modifying `draw_lines()` was done by finding which points belonged to which line through their slope. 
  >
  > * Left lane: x increases, while y decreases 
  >
  > * Right lane: x increases, while y increases
  >
  >Once we separate the line into either or, we can then find the average of their points to create an average lane line from 
  >all the lines. Arbitrary y1 and y2 for the lines are given by the image's shape to look consistent. 
  
6. Apply the new averaged lines to original image


### Shortcomings with current pipeline

* Being dynamic. A road consists of much more than straight paths, so a cruve will most definitely show this pipeline's weaknesses. 
* Shadows. I tried my implementation with the `challenge.mp4` and the shadows would trip up the lines.
* The values for kernel, rho, and etc. I feel like they're arbitrary. They only look good for a certain image quality. I feel like given another video or image of a different format, size, quality, and etc would make me change values of the region of interest and other varibles.   

### Improvements

Trying to find a way to curve with the lane lines and when an image changes with a shadow. The next lesson goes into `HSV` and `HSL` so I believe applying those effects might help. 
