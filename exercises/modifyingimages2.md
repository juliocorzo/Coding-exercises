# Advanced modifying images.

### Part 1
Write the green screen algorithm you saw in the lecture video yourself. To make sure you really understand the code that was written in the video, you should write the code yourself without looking at the video unless you get stuck and need to refer back to it for a hint.

```javascript
//Specifies which image goes in front.
var front = new SimpleImage("drewRobert.png");
//Specifies background image.
var background = new SimpleImage("dinos.png");
//Creates output image, using the height and the width of the background image.
var output = new SimpleImage(background.getWidth(), background.getHeight());

//for loop that calls on all pixels of the front image.
for (var pixel of front.values()){
    //sets the if condition, if the sum of red and blue is less than green...
    if (pixel.getGreen() > pixel.getRed() + pixel.getBlue()) {
        //Specifies that we are going to use the X pixel.
        var xb = pixel.getX();
        //Specifies that we are going to use the Y pixel.
        var yb = pixel.getY();
        //Takes pixels from the background image.
        var backgroundpixel = background.getPixel(xb,yb);
        //Outputs said pixels.
        output.setPixel(xb, yb, backgroundpixel);
    }
    //if the value of red + blue is larger than green then...
    else {
        //set the pixels from the front image.
        output.setPixel(pixel.getX(), pixel.getY(), pixel);
    }
}

//resizes the image in the same aspect ratio.
output.setSize(640,360);
//outputs image.
print(output);
```

I had issues with this assignment, redo tomorrow and make sure I get the concepts down properly.

**Result**

![](http://i.imgur.com/tyklEtm.png)
