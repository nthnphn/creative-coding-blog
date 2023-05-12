---
title: Assignment 2 - Stage 3
publish_date: 2023-05-12
disable_html_sanitization: true
---

# Multiple Squares Appearing Idea

<canvas id="c" ></canvas>

<script type=module>
    window.onload = setInterval(draw, 500); 

    function draw() {
    var canvas = document.getElementById('c'); 
        canvas.width = 560;
            canvas.height = 315;
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