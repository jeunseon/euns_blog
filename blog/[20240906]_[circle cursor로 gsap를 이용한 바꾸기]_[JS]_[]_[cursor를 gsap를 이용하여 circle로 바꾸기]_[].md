<h3 data-ke-size="size23"><span style="color: #1a5490;"><b>마우스 CURSOR GSAP를 이용한 circle custom</b></span></h3>
<p data-ke-size="size16">&nbsp;</p>
<p class="codepen" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-height="500" data-default-tab="html,result" data-slug-hash="GRbPNzG" data-pen-title="mouse cursor circle - gsap TweenMax" data-user="jeunseon" data-ke-size="size16"><span>See the Pen <a href="https://codepen.io/jeunseon/pen/GRbPNzG"> mouse cursor circle - gsap TweenMax</a> by jeunseon (<a href="https://codepen.io/jeunseon">@jeunseon</a>) on <a href="https://codepen.io">CodePen</a>.</span></p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">
<script src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</p>
<img src="https://blog.kakaocdn.net/dn/clLb1I/btsJut5h3nQ/Xe7Ewm3k3i37U1feJkz5Ek/img.png" srcset="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&amp;fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FclLb1I%2FbtsJut5h3nQ%2FXe7Ewm3k3i37U1feJkz5Ek%2Fimg.png" onerror="this.onerror=null; this.src='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png'; this.srcset='//t1.daumcdn.net/tistory_admin/static/images/no-image-v1.png';" data-origin-width="1816" data-origin-height="426" data-phocus-index="0">
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">HTML</p>
<pre id="code_1725612038519" class="html xml" data-ke-language="html" data-ke-type="codeblock"><code>&lt;div class="cursor"&gt;
    &lt;div class="cursor_ball cursor_ball_b"&gt;
      &lt;svg height="30" width="30"&gt;
      &lt;circle cx="15" cy="15" r="12" stroke-width="0"&gt;&lt;/circle&gt;
      &lt;/svg&gt;
    &lt;/div&gt;
    &lt;div class="cursor_ball cursor_ball_s"&gt;
      &lt;svg height="10" width="10"&gt;
        &lt;circle cx="5" cy="5" r="4" stroke-width="0"&gt;&lt;/circle&gt;
      &lt;/svg&gt;
    &lt;/div&gt;
&lt;/div&gt;</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">CSS</p>
<pre id="code_1725612095186" class="css" data-ke-language="css" data-ke-type="codeblock"><code>/* cursor css 부분 */
body{
  background: #141212;
  cursor: none;
}
.cursor {
  pointer-events: none;
}
.cursor_ball {
  position: fixed;
  /*  fixed 로 했을 경우 다른 css에 영향을 받아 cursor가 제대로 안될 경우 absolute 로 해도 된다.*/
  top: 0;
  left: 0;
  mix-blend-mode: difference;
  z-index: 999;
}
.cursor_ball circle {
  fill: #f7f8fa;
}</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">GSAP JS</p>
<pre id="code_1725612221541" class="javascript" data-ke-language="javascript" data-ke-type="codeblock"><code>// cursor
const bigBall = document.querySelector('.cursor_ball_b');
const smallBall = document.querySelector('.cursor_ball_s');
// hover시 바뀌는 부분
const hoverables = document.querySelectorAll('.hoverable');

document.body.addEventListener('mousemove', onMouseMove);
for(let i = 0; i &lt; hoverables.length; i++){
  hoverables[i].addEventListener('mouseenter', onMouseHover);
  hoverables[i].addEventListener('mouseleave', onMouseHoverOut);
}

// Move cursor
// gsap.to =&gt; TweenMax 로 하는 경우는 이전 버전이다.
function onMouseMove(e){
  gsap.to(bigBall, {
    duration: .4,
    x: e.pageX -15,
    y: e.pageY -15
  })
  gsap.to(smallBall, {
    duration: .1,
    x: e.pageX -5,
    y: e.pageY -7
  })
}

// Hover an element
function onMouseHover(){
  gsap.to(bigBall, {
    duration: .3,
    scale: 4
  })
  gsap.to(smallBall, {
    duration: .3,
    scale: 4
  })  
}

function onMouseHoverOut(){
  gsap.to(bigBall, {
    duration: .3,
    scale: 1
  })  
  gsap.to(smallBall, {
    duration: .3,
    scale: 1
  })
}</code></pre>