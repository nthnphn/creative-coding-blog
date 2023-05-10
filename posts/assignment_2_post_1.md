---
title: Assignment 2 - Stage 1
publish_date: 2023-05-10
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