---
title: Assignment 2 - Stage 3
publish_date: 2023-05-11
disable_html_sanitization: true
---

# Changing Squares Idea

As stated in the previous blog post, I wanted to purposely 
implement the idea of changing the squares with my net art.
After searching for ideas I came across the example below.

<canvas id="c" ></canvas>

<script type=module>
    window.onload = setInterval(draw, 500); 

    function draw() {
    var canvas = document.getElementById('c');
  
    canvas.width = canvas.parentNode.scrollWidth
    canvas.height = canvas.width * 9 / 16

    if (canvas.getContext) {
        var ctx = canvas.getContext('2d');

    for (var i = 0; i < 10; i++) {
        for (var j = 0; j < 12; j++) {
            var r = Math.floor(Math.random() * 255);
            var g = Math.floor(Math.random() * 255);
            var b = Math.floor(Math.random() * 255);

            ctx.fillStyle = 'rgb(' + r + ',' + g + ',' + b + ')';
            ctx.fillRect(r*j, g*j, 50, 50);
        }
    }

    }; 
    } 
</script>

The example above I thought was similar to my current net art allowing me 
to be able to implement it. I thought that constant change of squares added 
to the idea of "effective complexity" as it seem to make the art a little more
"spicier."

---

## My Code

<canvas id=net_art></canvas>

<script type=module>

    const cnv = document.getElementById ("net_art")
    console.dir (cnv)
    
    cnv.width = cnv.parentNode.scrollWidth
    cnv.height = cnv.width * 9 / 16

    // resizeCanvas ()
    // window.onresize = resizeCanvas

    // function resizeCanvas () {
    //     cnv.width = innerWidth
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

        ctx.fillStyle = "#2B2D42"
        ctx.fillRect (0, 0, cnv.width, cnv.height)

        ctx.globalAlpha = 0.8

        coordinates.forEach (p => {

            var r = 0 + 255 * Math.random();         
            var b = 0 + 255 * Math.random();
            var g = 0 + 255 * Math.random();

            let w = 300 * Math.random ();
            let h = 300 * Math.random ();

            let x_pos = p.x - w / 2;
            let y_pos = p.y - h / 2;

            ctx.fillStyle = "rgb(" + r + ", " + g + ", " + b + ")";     

            ctx.fillRect (x_pos, y_pos, w, h);
        })

        setTimeout(draw_frame, 1000)
    }
</script>
