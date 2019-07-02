# WEEK-3 Enhancing vision with CNN

## Take Away

Convolution is a technique to isolate features in images to enhance image recognition.

Pooling is a technique to reduce the information in an image while maintaining the features.

After passing a 3*3 filter over an image 28*28, the output will be 26*26.

After max pooling a 26*26 image with an 2*2 filter, the output will be 13*13.

## What Does Convolution do?
>In short, you take an array (usually 3x3 or 5x5) and pass it over the image. By changing the underlying pixels based on the formula within that matrix, you can do things like `edge detection`. So, for example, if you look at the above link, you'll see a 3x3 that is defined for edge detection where the middle cell is 8, and all of its neighbors are -1. In this case, for each pixel, you would multiply its value by 8, then subtract the value of each neighbor. Do this for every pixel, and you'll end up with a new image that has the edges enhanced.

>This is perfect for computer vision, because often it's features that can get highlighted like this that distinguish one item for another, and the amount of information needed is then much less...because you'll just train on the highlighted features.

>That's the concept of Convolutional Neural Networks. Add some layers to do convolution before you have the dense layers, and then the information going to the dense layers is more focused, and possibly more accurate. 

>From Coursera