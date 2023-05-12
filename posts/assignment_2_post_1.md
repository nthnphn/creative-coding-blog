---
title: Assignment 2 - Stage 1
publish_date: 2023-05-09
disable_html_sanitization: true
---

# Interaction Onlick Idea

<canvas id=onclick_example></canvas>

<script type=module>

    // getting and formatting the canvas element
    const cnv = document.getElementById (`onclick_example`)
    cnv.width = cnv.parentNode.scrollWidth
    cnv.height = cnv.width * 9 / 16

    // this array will store the coordinates
    // of the click events
    const coordinates = []

    // this function will take the
    // pointerEvent as an argument
    // and assign it to parameter 'e'
    function add_coordinate (e) {

        // adding to the coordinates array 
        // an object with x & y properties
        // storing the values associated 
        // with the .offsetX and .offsetY
        // properties of the pointerEvent
        // object assigned to parameter 'e' 
        coordinates.push ({
            x : e.offsetX,
            y : e.offsetY
        })
    }

    // adding the function to the 
    // .onclick property of the canvas
    // add_coordinate
    cnv.onclick = add_coordinate

    // getting a 2d context
    const ctx = cnv.getContext ('2d')    

    // function to draw animation frames
    function draw_frame () {

        // turquoise background
        ctx.fillStyle = `turquoise`
        ctx.fillRect (0, 0, cnv.width, cnv.height)

        // hotpink squares
        ctx.fillStyle = `hotpink`

        // go through the coordinates array
        coordinates.forEach (p => {

            // use the values on the x & y properties
            // of each object to draw a square
            ctx.fillRect (p.x - 10, p.y - 10, 20, 20)
        })

        // call itself recursively
        requestAnimationFrame (draw_frame)
    }

    // call the first frame
    requestAnimationFrame (draw_frame)
</script>

Above is the an interaction example by Thomas Capogreco. The interaction example he created utilizes the 
**mouseclick** function on canvas. As the assignment required the use of an audio or interaction feature, I found 
the **mouseclick** function to be interesting as I began coming up with my ideas on what I could create. The example
above help me come up with my idea as I wanted to have objects appearing where my mouse was when I clicked down. This 
inspired me to create a net art where the user can interact with the page to create small objects, which in return 
when combined create a larger piece of art.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xbdJf9MRL7A" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

The video above also further helped me improve my understanding on the **onclick** mouse function which was I was able to apply
in the beginning of my code.

---
## My Code


<canvas id=example1></canvas>

<script type=module>
const cnv = document.getElementById ("example1")
console.dir (cnv)

cnv.width = cnv.parentNode.scrollWidth
cnv.height = cnv.width * 9 / 16

// Resize the canvas based on page
// resizeCanvas ()
// window.onresize = resizeCanvas

// // Changes the canvas size to the same size as the page
// function resizeCanvas () {
//     cnv.width = innerWidth560
//     cnv.height = innerHeight
// }

const coordinates = [];
function add_coordinate (e) {
    coordinates.push ({x : e.offsetX, y: e.offsetY})
}
cnv.onclick = add_coordinate

const ctx = cnv.getContext ('2d')

requestAnimationFrame (draw_frame)

function draw_frame () {

    ctx.fillStyle = `#2B2D42`
    ctx.fillRect (0, 0, cnv.width, cnv.height)

    ctx.fillStyle = `#e63946`

    coordinates.forEach (p => {

        ctx.fillRect (p.x - 10, p.y - 10, 20, 20)
    })

    requestAnimationFrame (draw_frame)
}

requestAnimationFrame (draw_frame)
</script>