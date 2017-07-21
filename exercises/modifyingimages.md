# Part 1
Write a JavaScript program that modifies an image by putting three vertical stripes on it - a red stripe on the left one third, a green stripe in the middle, and a blue stripe on the right one third.

```javascript
var img = new SimpleImage("smallpanda.png");

for (var pixel of img.values()){
    if (pixel.getX() <= img.getWidth()/3){
        pixel.setRed(pixel.getRed() + 255);
    }
    if (pixel.getX() > img.getWidth()/3){
        pixel.setGreen(pixel.getGreen() + 255);
    }
    if (pixel.getX() > img.getWidth()/3 + img.getWidth()/3){
        pixel.setBlue(pixel.getBlue() + 255);
        pixel.setGreen(pixel.getGreen() - 255);
    }
}

print(img);
```
I did this by separating the image into three vertical sectors and figuring out how to point to them without dividing by 3 then comparing it to a specific number. By using `getWidth` I managed to make the script work on all images.

**Original & after running the script**

![](http://i.imgur.com/RcqaGnX.png) ![](http://i.imgur.com/1L4iIN5.png)

# Part 2
Write a JavaScript function named swapRedGreen with one parameter pixel (representing a single pixel). This function should swap the red and green values of the pixel.

```javascript
var img = new SimpleImage("smallhands.png");

print("The original values are: " + img.getPixel(60,70));

function swapRedGreen(x,y){
    var pixel = img.getPixel(x,y);
    var red = pixel.getRed();
    var green = pixel. getGreen();
    pixel.setRed(green);
    pixel.setGreen(red);
    return pixel;
}

swapRedGreen(60,70);
print("The swapped values are: " + img.getPixel(60,70));
```
This was done to verify that the colors had indeed switched.

# Part 2.1
To test your function, you should choose an image and apply the swapRedGreen function to every pixel in the image.

```javascript
var img = new SimpleImage("smallhands.png");

print(img);
print(img.getPixel(60,70));

for (var pixel of img.values()){
    var red = pixel.getRed();
    var green = pixel.getGreen();
    pixel.setGreen(red);
    pixel.setRed(green);
}

print(img);
print(img.getPixel(60,70));
```
I could not get it to work with a function, so I decided to do a loop and use `values()`. Not sure if this was the way it was inteded to be done.

**Original & after running the script**

![](http://i.imgur.com/pH89SnI.png) ![](http://i.imgur.com/JCrZJVL.png)
