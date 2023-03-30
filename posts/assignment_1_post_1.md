---
title: Assignment 1 - Post 1
publish_date: 2023-03-28
disable_html_sanitization: true
---

# Morphing Idea

[p5 Example: Morph](https://p5js.org/examples/motion-morph.html)

<iframe width="400" height="400" src="https://editor.p5js.org/nthnphn/full/DnQ62lkCT"></iframe>

The code above was what inspired me to create the main feature of my net art. 
As I was scrolling through examples that p5 gives I came across this example of morphing shapes.

When I saw the example of a square morphing into a circle, I came up with an idea on how to incorporate it with effective complexity. And that was to create different random shapes very fast.

In the p5 morph example, they used the **lerp()** method which allows one point to interpolate to another point.

> Lerp
: Linear Interpolation. A method of curve fitting using linear polynomials to construct new data points within the range of a discrete set of known data points. 


```javascript
for (let i = 0; i < circle.length; i++) {
    let v1;
    // Are we lerping to the circle or square?
    if (state) {
      v1 = circle[i];
    } else {
      v1 = square[i];
    }
    // Get the vertex we will draw
    let v2 = morph[i];
    // Lerp to the target
    v2.lerp(v1, 0.1);
    // Check how far we are from target
    totalDistance += p5.Vector.dist(v1, v2);
}
```
---
The lerp method was used to morph the square into a circle. However, for me I wanted something more unstable and not as smooth.

Hence why I decided to make it seem as the differents vertices of the shape I created was teleporting very fast. I also decided that the shapes will have 20 vertices each in order for more crazy shapes to appear.

I believe this to be a good example of effective complexity due to how fast the random shapes are being created. However as the shapes only form inside the canvas, it makes the process seem to be controlled as well.

<iframe width="400" height="400" src="https://editor.p5js.org/nthnphn/full/UkrSdvxXw"></iframe>

```javascript
// rand_coordinate returns a variable called coordinate which contains a random (x, y) value within the canvas
function rand_coordinate () {
  return coordinate = { x: random (width), y: random (height) } 
}

function draw_shape () { 
   beginShape () // begins recording vertices for a shape

   // for loop repeats 20 times creating 20 random vertices for the shape
   for (let i = 0; i <= 20; i++) {
   const cnr = rand_coordinate ()
   vertex (cnr.x, cnr.y) // 20 vertices are given with different co-ordinates from rand_coordinate
   }
   endShape ()
}
```

The functions created above are called:
1. rand_coordinate ()
2. draw_shape ()

## rand_coordinate ()
rand_coordinate simply returns a random 'x' value within the width of the canvas, as well as a random 'y' value within the height of the canvas. These 2 values will then be later used in the function **draw_shape**

## draw_shape ()
The **draw_shape** function uses the **beginShape** method to create its shapes. A **for loop** is incorporated to create 20 vertices using the **rand_coordinate** function in which the shape will be created.
