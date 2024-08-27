<p data-ke-size="size16">html 영역</p>
<pre class="javascript"><code>&lt;div class="wrap"&gt;
  &lt;!-- con5 --&gt;
  &lt;section class="showImg"&gt;
    &lt;div class="inner"&gt;
      &lt;ul class="listBox"&gt;
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
      &lt;div class="imgBox box"&gt;
        &lt;img src="images/img0.jpg" alt=""&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/section&gt;  
&lt;/div&gt;</code></pre>
<p data-ke-size="size16">css 영역</p>
<pre class="css"><code>.wrap {
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
<p data-ke-size="size16">js 영역</p>
<pre class="typescript"><code>gsap .registerPlugin(ScrollTrigger);

// 07. showImg listBox li hover 시 이미지 보이는 애니
let listBox = document.querySelectorAll('.showImg .listBox &gt; li');
let imgBox = document.querySelector('.showImg .imgBox');
let img = document.querySelector('.showImg .imgBox &gt; img');

for(let i = 0; i &lt; listBox.length; i++){
  listBox[i].addEventListener('mouseover', () =&gt; {
    img.src = `images/img${i}.jpg`;
    gsap.set(imgBox, {scale: 0, opacity: 0, duration: .3}),
    gsap.to(imgBox, {scale: 1, opacity: 1, duration: .3})
  })
  listBox[i].addEventListener('mousemove', (e) =&gt; {
    let imgBoxX = e.pageX + 20;
    let imgBoxY = e.pageY - 20;
    imgBox.style.left = imgBoxX + 'px'
    imgBox.style.top = imgBoxY + 'px'
  })
  listBox[i].addEventListener('mouseout', () =&gt; {
    gsap.to(imgBox, {scale: 0, opacity: 0, duration: .3})
  })
}

// 다른쪽에 position: sticky; 가 있는 경우에 일정 부분만  overflow: hidden 을 붙여주기위해 toggleClass 를 사용한다.
gsap.timeline({
  scrollTrigger: {
    trigger: '.showImg',
    start: '0% 100%',
    end: '100% 0%',
    toggleClass:{targets: '.wrap', className:'on'}
  }
})</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="JjQEPQG" data-pen-title="j.young 클론코딩 con5 영역 showImg" data-user="jeunseon" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/jeunseon/pen/JjQEPQG">
  j.young 클론코딩 con5 영역 showImg</a> by jeunseon (<a href="https://codepen.io/jeunseon">@jeunseon</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>
<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="BagVzRm" data-pen-title="hover ShowImg gsap" data-user="jeunseon" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/jeunseon/pen/BagVzRm">
  hover ShowImg gsap</a> by jeunseon (<a href="https://codepen.io/jeunseon">@jeunseon</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>