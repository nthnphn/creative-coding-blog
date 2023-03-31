---
title: Assignment 1 - Stage 2
publish_date: 2023-03-29
disable_html_sanitization: true
---

# Colour Changing

[Colour Changing Example](https://editor.p5js.org/hosken/sketches/I_4VSTotf)

<iframe width="400" height="400" src="https://editor.p5js.org/hosken/full/I_4VSTotf"></iframe>

```javascript

let counter = 0; // Variable to count number of frames

let myColour; //Keep track of our random colour.

function setup() {
  createCanvas(400, 400);

  //Set myColour to be a random colour:
  myColour = color(random(255), random(255), random(255));
  
  //If you want more control, set the framerate 
  //to a specific amount of frames per second
  frameRate(30);
}

function draw() {
  background(myColour);

  //when the counter reaches 30,  
  if (counter > 19) {
    //switch the colour to a new random colour:
    myColour = color(random(255), random(255), random(255));

    //and reset the counter to zero:
    counter = 0;
  }


  //At the end of each frame increase the counter
  counter = counter + 1;
}

```
The code above was what inspired me to implement changing colours to the shapes that were being created.
By using multiple variables such as "myColour" and "counter," different random colours appear after a set period of time. The "myColour" variable contains 3 objects that give random values from 1 to 255 (these are considered the rgb values representing the colour). 

An **if statement** is used to change the colour of "myColour after a certain amount of frames has passed. The code knows how many frames has passed through the variable "counter" which starts at 0, and then has 1 added to it after every frame.

---

While creating my sketch, I wanted to incorporate something more than just white shapes forming on a black canvas. So I decided to implement this colour changing function. I believe by adding this, my code is gives a lot more variety then constantly seeing the same thing over and over again. It also becomes more pleasing to watch despite looking very unstable. Which again I think shows a strong demonstration of effective complexity.

<iframe width="400" height="400" src="https://editor.p5js.org/nthnphn/full/wefBvrx2G"></iframe>

```javascript 

let counter = 0  // Used to count the number of frames
let myColour // To keep track of the random color

function setup () {
   createCanvas (576, 324) // Creates a canvas 
   myColour = color (random(255), random(255), random(255)) // "myColour" is given a random colour
   frameRate (20) // displays 20 frames in a second
}

function draw () {
   background ("black") // Black background is drawn 

   change_colour () // change_color function is called
   fill (myColour) // the draw_shape function is coloured with a random colour
   noStroke ()
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

   // for loop repeats 20 times creating 20 random vertices for the shape
   for (let i = 0; i <= 20; i++) {
   const cnr = rand_coordinate ()
   vertex (cnr.x, cnr.y) // 20 vertices are given with different co-ordinates from rand_coordinate
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

I used the code created by *hosken* as a base for my own. By creating the variable **myColour** and the function **change_colour** I am able to change the colours of the shapes I am forming every 50 frames. 

# change_colour
Similar to the example code, **change_colour** uses an if statement to give the variable **myColour** random "rgb" values after every 50 frames. 
