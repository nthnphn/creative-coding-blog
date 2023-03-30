---
title: Assignment 1 - Post 3
publish_date: 2023-03-30
disable_html_sanitization: true
---

# Addition of a Slider

[p5 Slider Example](https://p5js.org/examples/hello-p5-interactivity-2.html)

<iframe width="400" height="400" src="https://editor.p5js.org/nthnphn/full/00ZT10IV9"></iframe>

```javascript 
// A HTML range slider
let slider;

function setup() {
  createCanvas(720, 400);
  // hue, saturation, and brightness
  colorMode(HSB, 255);
  // slider has a range between 0 and 255 with a starting value of 127
  slider = createSlider(0, 255, 127);
}

function draw() {
  background(127);
  strokeWeight(2);

  // Set the hue according to the slider
  stroke(slider.value(), 255, 255);
  fill(slider.value(), 255, 255, 127);
  ellipse(360, 200, 200, 200);
}
```

In the p5 example above, a slider function was implemented to to change the colour of the circle. I believe that this was a good idea to implement into my own code in order to give the viewers more sense of control.

---

<iframe width="400" height="400" src="https://editor.p5js.org/nthnphn/full/HhJEpVbaD"></iframe>

```javascript

let counter = 0  // Used to count the number of frames
let myColour // To keep track of the random color

let slider //creates a slider variable

function setup () {
   createCanvas (576, 324) // Creates a canvas 
   myColour = color (random(255), random(255), random(255)) // "myColour" is given a random colour
   frameRate (30) // displays 30 frames in a second


   // create a slider at the bottom of the page that has a minimum value of 4 and a maximum value of 50
   slider = createSlider(4, 50, 25) 
   slider.position (10, 300)
}

function draw () {
   background ("black") // Black background is drawn 

   change_colour () // change_color function is called
   fill (myColour) // the draw_shape function is coloured with a random colour
   noStroke () // gives the shapes no strokes
   draw_shape () // draw shape function is called

   counter = counter + 1 // keeps track of the frames
}

// rand_coordinate returns a variable called coordinate which contains a random (x, y) value within the canvas
function rand_coordinate () {
  return coordinate = { x: random (width), y: random (height) } 
}

// the function draw_shape is used to create my shapes
function draw_shape () { 
   beginShape () // begins recording vertices for a shape

   // for loop repeats the amount of times the slider value is set to 
   for (let i = 0; i <= slider.value(); i++) {
   const cnr = rand_coordinate ()
   vertex (cnr.x, cnr.y) // vertices are given with different co-ordinates from rand_coordinate
   }
   endShape ()
}

// Function used to change colour of the shapes every 50 frames
function change_colour () {

   // when the amount of frames increase over 50 then myColour changes into a different random colour and the counter resets to 0
   if (counter > 50) {
      myColour = color (random(255), random(255), random(255))
      counter = 0
   }
}

```

By creating a new variable called **slider** I am able to use the **createSlider()** method to give the audience a choice of how many vertices they want in the shapes. The slider has a minimum value of 4 and a maximum value of 50, meaning that shapes with 4 vertices to 50 vertices can be made. 

In order to change this in the ***draw_shape** function, the number 20 is replaced with **slider.value()**