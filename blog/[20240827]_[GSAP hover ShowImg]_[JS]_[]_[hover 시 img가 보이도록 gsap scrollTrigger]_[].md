<p>html 영역</p>
<pre><code class="language-html">&lt;div class=&quot;wrap&quot;&gt;
  &lt;!-- con5 --&gt;
  &lt;section class=&quot;showImg&quot;&gt;
    &lt;div class=&quot;inner&quot;&gt;
      &lt;ul class=&quot;listBox&quot;&gt;
        &lt;li&gt;
          &lt;h3&gt;Daebang&lt;/h3&gt;
          &lt;p&gt;Undustry&lt;/p&gt;
          &lt;p&gt;2024&lt;/p&gt;
        &lt;/li&gt;
        &lt;li&gt;
          &lt;h3&gt;THE Dopda&lt;/h3&gt;
          &lt;p&gt;Platform&lt;/p&gt;
          &lt;p&gt;2024&lt;/p&gt;
        &lt;/li&gt;
        &lt;li&gt;
          &lt;h3&gt;Musign&lt;/h3&gt;
          &lt;p&gt;Agency&lt;/p&gt;
          &lt;p&gt;2024&lt;/p&gt;
        &lt;/li&gt;
        &lt;li&gt;
          &lt;h3&gt;Hanhwa&lt;/h3&gt;
          &lt;p&gt;Chemical&lt;/p&gt;
          &lt;p&gt;2024&lt;/p&gt;
        &lt;/li&gt;
      &lt;/ul&gt;
      &lt;div class=&quot;imgBox box&quot;&gt;
        &lt;img src=&quot;images/img0.jpg&quot; alt=&quot;&quot;&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/section&gt;  
&lt;/div&gt;</code></pre>
<p>css 영역</p>
<pre><code class="language-css">.wrap {
    position: relative;
}

/* showImg */
.showImg .listBox li {
    display: grid;
    grid-template-columns: 2fr 1fr auto;
    border-bottom: 1px solid #000;
}
.showImg .imgBox {
    position: absolute; 
    /*  relative 안주면 브라우저의 뷰포트를 기준으로 잡는다.  */
    transform: scale(0);
    /*  이미지 안보이도록  */
    opacity: 0;
   /*  이미지 안보이도록  */
    z-index: 100;
}

/* toggleClass */
/*  다른 section에 position:sticky; 가 있을 수 있으므로  */
.wrap.on {
  overflow: hidden
  /*  이미지로 인해 스크롤이 생기지 않도록  */
}</code></pre>
<p>js 영역</p>
<pre><code class="language-js">gsap .registerPlugin(ScrollTrigger);

// 07. showImg listBox li hover 시 이미지 보이는 애니
let listBox = document.querySelectorAll(&#39;.showImg .listBox &gt; li&#39;);
let imgBox = document.querySelector(&#39;.showImg .imgBox&#39;);
let img = document.querySelector(&#39;.showImg .imgBox &gt; img&#39;);

for(let i = 0; i &lt; listBox.length; i++){
  listBox[i].addEventListener(&#39;mouseover&#39;, () =&gt; {
    img.src = `images/img${i}.jpg`;
    gsap.set(imgBox, {scale: 0, opacity: 0, duration: .3}),
    gsap.to(imgBox, {scale: 1, opacity: 1, duration: .3})
  })
  listBox[i].addEventListener(&#39;mousemove&#39;, (e) =&gt; {
    let imgBoxX = e.pageX + 20;
    let imgBoxY = e.pageY - 20;
    imgBox.style.left = imgBoxX + &#39;px&#39;
    imgBox.style.top = imgBoxY + &#39;px&#39;
  })
  listBox[i].addEventListener(&#39;mouseout&#39;, () =&gt; {
    gsap.to(imgBox, {scale: 0, opacity: 0, duration: .3})
  })
}

// 다른쪽에 position: sticky; 가 있는 경우에 일정 부분만  overflow: hidden 을 붙여주기위해 toggleClass 를 사용한다.
gsap.timeline({
  scrollTrigger: {
    trigger: &#39;.showImg&#39;,
    start: &#39;0% 100%&#39;,
    end: &#39;100% 0%&#39;,
    toggleClass:{targets: &#39;.wrap&#39;, className:&#39;on&#39;}
  }
})</code></pre>


<p>See the Pen <a href="https://codepen.io/jeunseon/pen/JjQEPQG">j.young con5 영역</a> by jeunseon (<a href="https://codepen.io/jeunseon">@jeunseon</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>




<p>See the Pen <a href="https://codepen.io/jeunseon/pen/BagVzRm">showImg</a> by jeunseon (<a href="https://codepen.io/jeunseon">@jeunseon</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>