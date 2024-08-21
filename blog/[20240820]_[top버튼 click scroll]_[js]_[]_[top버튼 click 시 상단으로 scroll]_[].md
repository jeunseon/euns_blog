<p data-ke-size="size16">HTML</p>
<pre id="code_1724133404439" class="html xml" data-ke-language="html" data-ke-type="codeblock"><code>&lt;div class="wrap"&gt;
  &lt;section class="con1"&gt;section1&lt;/section&gt;
  &lt;section class="con2"&gt;section2&lt;/section&gt;
  &lt;section class="con3"&gt;section3&lt;/section&gt;
  &lt;section class="con4"&gt;section4&lt;/section&gt;
  
  &lt;div class="top"&gt;top&lt;/div&gt;
&lt;/div&gt;</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">CSS</p>
<pre id="code_1724133427296" class="css" data-ke-language="css" data-ke-type="codeblock"><code>.wrap {
  position: relative;
}
.top {
  position: fixed;
  bottom: 10px;
  right: 10px;
  
  padding: 20px;
  background: #fff;
  border-radius: 20px;
  cursor: pointer;
}</code></pre>
<p data-ke-size="size16">스크롤이 스무스하게 되지 않는다면 아래의 CSS를 body에 붙인다.</p>
<div style="background-color: #1f1f1f; color: #cccccc;">
<div>&nbsp;</div>
<div><span style="color: #cccccc;">&nbsp; &nbsp; </span><span style="color: #9cdcfe;">scroll-behavior</span><span style="color: #cccccc;">: </span><span style="color: #ce9178;">smooth</span><span style="color: #cccccc;">; </span></div>
<div>&nbsp;</div>
</div>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">JS</p>
<pre id="code_1724133442914" class="javascript" data-ke-language="javascript" data-ke-type="codeblock"><code>// top 버튼
const topBtn = document.querySelector('.top');
topBtn.addEventListener('click', () =&gt; {
  $('body, html').animate({scrollTop:0}, 400);
  return false;
});</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>
<p class="codepen" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-height="300" data-default-tab="html,result" data-slug-hash="xxoYBLg" data-pen-title="top 버튼 scroll" data-user="jeunseon" data-ke-size="size16"><span>See the Pen <a href="https://codepen.io/jeunseon/pen/xxoYBLg"> top 버튼 scroll</a> by jeunseon (<a href="https://codepen.io/jeunseon">@jeunseon</a>) on <a href="https://codepen.io">CodePen</a>.</span></p>
<p data-ke-size="size16">
<script src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</p>