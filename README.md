<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Sunnet Berdinov</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    background: #020617;
    color: white;
    font-family: "Fira Code", monospace;
    overflow-x: hidden;
}

canvas {
    position: fixed;
    top: 0;
    left: 0;
    z-index: -1;
}

.container {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}

.content {
    padding: 40px;
}

h1 {
    font-size: 60px;
}

h2 {
    color: #60a5fa;
    margin-top: 15px;
}

p {
    margin-top: 20px;
    font-size: 20px;
    color: #cbd5e1;
}
</style>

</head>

<body>

<canvas id="stars"></canvas>


<div class="container">

<div class="content">

<h1>
Sunnet Berdinov
</h1>

<h2>
Backend Software Engineer • Python Developer • Robotics Enthusiast
</h2>

<p>
Building scalable systems, AI solutions and intelligent robots.
</p>

</div>

</div>


<script>

const canvas = document.getElementById("stars");
const ctx = canvas.getContext("2d");


let stars = [];

function resize(){
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
}

window.addEventListener("resize", resize);
resize();


class Star {

    constructor(){

        this.x = Math.random() * canvas.width;
        this.y = Math.random() * canvas.height;

        this.size = Math.random() * 2;

        this.speed = Math.random() * 0.4 + 0.1;

        this.opacity = Math.random();

    }


    update(){

        this.y += this.speed;

        if(this.y > canvas.height){
            this.y = 0;
            this.x = Math.random() * canvas.width;
        }

        this.opacity += 0.01;

        if(this.opacity > 1)
            this.opacity = 0;

    }


    draw(){

        ctx.beginPath();

        ctx.fillStyle =
        `rgba(255,255,255,${this.opacity})`;

        ctx.arc(
            this.x,
            this.y,
            this.size,
            0,
            Math.PI*2
        );

        ctx.fill();

    }

}



for(let i=0;i<250;i++){
    stars.push(new Star());
}



function animate(){

    ctx.clearRect(
        0,
        0,
        canvas.width,
        canvas.height
    );


    stars.forEach(star=>{
        star.update();
        star.draw();
    });


    requestAnimationFrame(animate);

}


animate();

</script>


</body>
</html>
