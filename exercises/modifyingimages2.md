# Advanced modifying images.

### Part 1
Write the green screen algorithm you saw in the lecture video yourself. To make sure you really understand the code that was written in the video, you should write the code yourself without looking at the video unless you get stuck and need to refer back to it for a hint.

```javascript
var fgimage = new SimpleImage("drewRobert.png");
var bgimage = new SimpleImage("dinos.png");
var output = new SimpleImage(fgimage.getWidth(), fgimage.getHeight());

for (var pixel of fgimage.values()){
    if (pixel.getGreen() > pixel.getRed() + pixel.getBlue()){
        var x = pixel.getX();
        var y = pixel.getY();
        var bgpixel = bgimage.getPixel(x,y);
        output.setPixel(x,y,bgpixel);
    }
    else {
        var x = pixel.getX();
        var y = pixel.getY();
        output.setPixel(x,y,pixel);
    }
}

output.setSize(640,360);
print(output);
```

I had issues with this assignment, redo tomorrow and make sure I get the concepts down properly.

**Result**

![](http://i.imgur.com/tyklEtm.png)

### Part 2
Your task is to find and fix the bug. Use what you have learned about applying the scientific method to debugging: gather information, apply your knowledge about images and programming, form a hypothesis, test your hypothesis, and finally, change the code to fix the problem.

**Hypothesis**: Given that the yellow box should be red, it is safe to assume that the variables for the green sector are set incorrectly. Therefore, my idea is that I need to refine those coordinates in order to isolate that color. The only color that mixes is magenta.

*Original code*

```javascript
var img = new SimpleImage(200,200);
  for (var px of img.values()){
  var x = px.getX();
  var y = px.getY();
    if (x < img.getWidth()/2){
      px.setRed(255);
    }
    if (y>img.getHeight()/2){
      px.setBlue(255);
    }
    else {
      px.setGreen(255);
    }
  }
print (img);
```

*Corrected code*

```javascript
var img = new SimpleImage(200,200);

for (var px of img.values()){
    var x = px.getX();
    var y = px.getY();
    if ((x < img.getHeight()/2)){
        px.setRed(255);
    }
    if ((y > img.getWidth()/2)){
        px.setBlue(255);
    }
    if ((x > img.getHeight()/2)){
        px.setGreen(255);
    }
    if ((y > img.getWidth()/2)){
        px.setGreen(0);
    }
}
print(img);
```
As it is clear to see, my solution is simply setting the coordinates that were mixing with the red sector to 0 in green.

**Original & after correcting the script**

![](http://i.imgur.com/LEWZJrH.png)
![](http://i.imgur.com/y66kPQn.png)

### Part 3

Write a function named setBlack that has one parameter pixel (representing a single pixel) and returns pixel with its red, green, and blue components changed so that the pixel’s color is black.

```javascript
var img = new SimpleImage("smallpanda.png");

    function setBlack(x,y){
        if (img.getRed(x,y) > 0){
        img.setRed(0,0,0)
        }
        if (img.getBlue(x,y) > 0){
        img.setBlue(0,0,0)
        }
        if (img.getGreen(x,y) > 0){
        img.setGreen(0,0,0)
        }  
    }

print(img.getPixel(0,0))
setBlack(0,0);
print(img.getPixel(0,0))
```

Probably the worst way of doing this but hey it works.

### Part 3.1

Now you will write another function named addBorder. This function will add a black border 10px thick to the image.

*Non-function version because I don't read instructions properly*

```javascript
var img = new SimpleImage("smallpanda.png");

print(img);

for (var px of img.values()){
    var x = px.getX();
    var y = px.getY();
    if  ((x < 11) || (x > img.getWidth() - 11)){
        px.setRed(0);
        px.setGreen(0);
        px.setBlue(0);
    }
    if ((y < 11) || (y > img.getHeight() - 11)){
        px.setRed(0);
        px.setGreen(0);
        px.setBlue(0);
    }
}

print(img);
```

*Function version (probably cheating idk)*

```javascript
var image = new SimpleImage("smallpanda.png");
var img = image
print(img);

function addBorder(img){
      for (var px of img.values()){
          var x = px.getX();
          var y = px.getY();
              if  ((x < 11) || (x > img.getWidth() - 11)){
                  px.setRed(0);
                  px.setGreen(0);
                  px.setBlue(0);
              }
              if ((y < 11) || (y > img.getHeight() - 11)){
                  px.setRed(0);
                  px.setGreen(0);
                  px.setBlue(0);
              }
      }
}

addBorder(img);

print(img);
```

**Original & after running the script**

![](http://i.imgur.com/QVfEaBM.png)
![](http://i.imgur.com/EY0vjTM.png)
