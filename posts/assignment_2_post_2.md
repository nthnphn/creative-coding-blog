---
title: Assignment 2 - Stage 2
publish_date: 2023-05-10
disable_html_sanitization: true
---

# Squares Appearing on Click Idea

<canvas id=canvas_random_squares></canvas>

<script type=module>
    var canvas = document.getElementById("canvas_random_squares");

    canvas.width = canvas.parentNode.scrollWidth
    canvas.height = canvas.width * 9 / 16

if (canvas.getContext) {


  var ctx = canvas.getContext("2d");

  var j = Math.floor(4 + 10 * Math.random());  

  ctx.globalAlpha = 0.8;                      

  for (var i = 0; i < j; i += 1) {            
    var r = 0 + 255 * Math.random();          
    var b = 0 + 255 * Math.random();
    var g = 0 + 255 * Math.random();

    var x = 0 + 400 * Math.random();         
    var y = 0 + 400 * Math.random();
    
    var w = 50 + 500 * Math.random();       
    var h = 50 + 500 * Math.random();

    ctx.fillRect(y, x, w, h);             
    ctx.fillStyle = "rgb(" + r + ", " + g + ", " + b + ")";    
  }
}
</script>
> refresh page to get different results above

The example above coded by Daniel Nugent gave me inspiration on what would appear 
when my net art is interacted with. The reason I really liked this idea of having 
multiple squares appear on click is because I believe I can use it showcase a 
great representation of effective complexity. The squares created are completely random: 
the amount of squares, the size, the position, and the colour are all chosen at random. 
However, when viewed together as a whole, each square complements each other to give 
an entire piece of art. Having the opacity of all squares be decreased also elevate the
art when the squares are viewed together. Being able to see each square despite the 
possibility of them being on top of each other in my opinion adds to the idea of 
effective complexity.

---
## My Code

<canvas id="example2"></canvas>

<script type=module>

    const cnv = document.getElementById ("example2")
    console.dir (cnv)

    cnv.width = cnv.parentNode.scrollWidth
    cnv.height = cnv.width * 9 / 16

    // resizeCanvas ()
    // window.onresize = resizeCanvas

    // function resizeCanvas () {
    //     cnv.width = innerWidth
    //     cnv.height = innerHeight
    // }

    requestAnimationFrame (draw_frame)

    function draw_frame () {
        ctx.fillStyle = "#2B2D42"
        ctx.fillRect (0, 0, cnv.width, cnv.height)
    }

    const coordinates = [];

    function add_coordinate (e) {
        
        coordinates.push ({x : e.offsetX, y: e.offsetY})

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

    }
    cnv.onclick = add_coordinate

    const ctx = cnv.getContext ('2d')
</script>

Above is my code after implementing my onclick function. As showcased, when clicked on
the background a random square appears. However the squares change after every click 
when a new square is added. This was done accidentally but I really liked the idea as
it introduced more variety into my net art.
