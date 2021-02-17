# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 7 asteps. But to find those 7 steps I have to build my own Python class toolkit so I can solve the problem using OOP.

1. I converted the image to HSL
2. I created 2 masks filtered by yellow and white color based on my own tools to find the appropriate cv.inrange() parameters 
3. Then I combined both masks into one image using bitwise_or()
4. The next step would be to mask the resulting image with the viewport mask image
5. After that I ran the canny algorithm to detect the boundaries. It should be easy to find boundaries because the remaining pixels should contains only the lane lines
6. Once I got the boundaries I can pass it to houglines() to produce the lines
7. I filtered out the incorrect lines and produce the straight line using the y = ax + b equation and simple statistic to choose the lines that grouped most as the winner. Then I make sure I store the last drawn lines and use it if the next frame I fail to recognize the lines.


### 2. Identify potential shortcomings with your current pipeline

My pipeline works for all the challenge videos. The current drawback is I only draw straight lines while the real lanes is a curve lines.

### 3. Suggest possible improvements to your pipeline

To draw curve lines to make it as real as the real lanes

