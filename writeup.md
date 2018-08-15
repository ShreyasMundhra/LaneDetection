# **Finding Lane Lines on the Road** 

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

### Reflection

### 1. Description of the pipeline

My pipeline consisted of 6 steps. First, I converted the images to grayscale, then I applied gaussian blurring to smoothen the image and remove any noise. The next step was canny edge detection to identify the pixels that form edges. The fourth step was applying a region mask using a quadrilateral to filter out the edges in the background. After this, the hough transform was applied to this edge detected grayscale image to find the endpoints of each detected edge. The final step was to extrapolate and draw a single line on the left and right lanes. In order to do this, I modified the draw_lines() function by doing two steps. The first step was to separate lines on the left lane and lines on the right lane by checking whether the slope of each of the lines is positive or negative. The next step was to find the median slope and median intercept of lines in the left lane as well as the lines in the right lane. I decided to find the median instead of the mean as I felt the mean would more easily get impacted by noisy lines. Once these values were found, the corresponding two lines were drawn from the bottom of the image to the minimum y value of the broken lane lines.

### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be if there is a sharp turn, the slope of both the lane lines might have the same sign and so, we won't be able to separate the lane lines and extrapolate them accurately.

Another shortcoming could be that if there are shadows on the road, the edges of these shadows might also be detected as lane lines.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to apply color masking or some variation of it to avoid detecting edges of shadows on the road.

Another potential improvement could be to somehow use the lines detected in the previous frame of the video to detect the lines in the current frame. This can help in eliminating noise, as the lane lines detected in consecutive frames should generally be almost coinciding with each other.
