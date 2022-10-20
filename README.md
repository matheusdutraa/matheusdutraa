<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <style>
    html {
  min-height: 100vh;
  background: #111;
  overflow: hidden;
  --part-size: 50px;
}
.fire_shaft {
  position: absolute;
  bottom: 0;
}
.particle {
  width: var(--part-size);
  aspect-ratio: 1/1;
  border-radius: 50%;
  opacity: .75;
  background: darkorange;
  position: absolute;
  top: 100%;
  filter: blur(5px);
  animation: burn 1s linear forwards;
}
@keyframes burn {
  100% { 
    transform: scale(.5);
    top: 0; 
    opacity: 0;
/*     background: gray; */
  }
}
  </style>
  <script>
    const colors = ['orange','orangered','darkorange', 'gold', 'tomato', 'goldenrod','yellow'],
      fire_spread = 15 // best range 10-20

function addParticle() {
  var fs = document.createElement('div'),
      skew = Math.random() < .5 ? Math.random()*fire_spread : -Math.random()*fire_spread
  fs.className = 'fire_shaft'
  fs.style.height = Math.random()*50 + 25 + 'vh'
  fs.style.transform = 'skew('+skew+'deg)'
  fs.style.left = Math.random()*100 + '%'
  var p = document.createElement('div')
  p.className = 'particle'
  p.style.background = colors[Math.floor(Math.random()*colors.length)]
  p.onanimationend = function() { this.remove() }  
  document.body.appendChild(fs).appendChild(p)
}

setInterval(addParticle,1000/60)
  </script>
</body>
</html>
