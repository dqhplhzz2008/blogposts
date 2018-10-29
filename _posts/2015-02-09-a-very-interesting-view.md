---
ID: 2815
post_title: A very interesting View
post_name: a-very-interesting-view
author: 小奥
post_date: 2015-02-09 00:28:27
layout: post
link: >
  http://www.yushuai.me/2015/02/09/2815.html
published: true
tags: [ ]
categories:
  - Life Time
---
<div data-height="268" data-theme-id="0" data-slug-hash="GgOxvV" data-default-tab="js" data-user="MateiGCopot" class='codepen'><pre><code>var w = c.width = window.innerWidth,
    h = c.height = window.innerHeight,
    ctx = c.getContext(&#x27;2d&#x27;),
    
    cen = {x:w/2, y:h/2},
    radiant = 0,
    particles = [],
    particleCount = 1,
    frame = 0,
    middleCover = ctx.createRadialGradient(cen.x, cen.y, 0, cen.x, cen.y, 20);

middleCover.addColorStop(0, &#x27;rgba(0, 0, 0, .1)&#x27;);
middleCover.addColorStop(1, &#x27;rgba(0, 0, 0, 0)&#x27;);

function anim(){
  window.requestAnimationFrame(anim);
  
  update();
}
anim();

function Particle(){
  this.x = cen.x;
  this.y = cen.y;
  this.vx = Math.cos(radiant);
  this.vy = Math.sin(radiant);
  
  this.color = &#x27;hsl(rad, 80%, 50%)&#x27;
    .replace(&#x27;rad&#x27;, ((radiant/Math.PI)*180)|0);
}
Particle.prototype.update = function(){
  this.x += this.vx;
  this.y += this.vy;
  
  ctx.fillStyle = this.color;
  ctx.fillRect(this.x, this.y, 2, 2);
}
function update(){
  
  ctx.fillStyle = &#x27;rgba(0, 0, 0, .04)&#x27;;
  ctx.fillRect(0, 0, w, h);
  
  radiant += .1;
  radiant %= Math.PI*2;
  
  ++frame;
  if(frame &gt; particleCount){
    frame = 0;
    particles.push(new Particle);
  }
  
  for(var i = 0; i &lt; particles.length; ++i){
    var par = particles[i];
    par.update();
    
    if(par.x &gt; w || par.x &lt; 0 || par.y &gt; h || par.y &lt; 0){
      particles.splice(i, 1);
      --i;
    }
  }
  
  ctx.fillStyle = middleCover;
  ctx.beginPath();
  ctx.arc(cen.x, cen.y, 20, 0, Math.PI*2);
  ctx.fill();
}

document.addEventListener(&#x27;click&#x27;, function(){
  for(var i = 0; i &lt; 10; ++i) update();
})


for(var i = 0; i &lt; 100; ++i) update();</code></pre>
<p>See the Pen <a href='http://codepen.io/MateiGCopot/pen/GgOxvV/'>Spiral of rainbowy particles</a> by towc (<a href='http://codepen.io/MateiGCopot'>@MateiGCopot</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
</div><script async src="//assets.codepen.io/assets/embed/ei.js"></script>