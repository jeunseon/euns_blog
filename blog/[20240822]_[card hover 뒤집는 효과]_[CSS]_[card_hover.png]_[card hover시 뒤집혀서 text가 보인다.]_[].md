<p data-ke-size="size16">html</p>
<pre id="code_1724315842524" class="html xml" data-ke-language="html" data-ke-type="codeblock"><code>&lt;div class="wrap"&gt;
  &lt;div class="con1"&gt;
    &lt;div class="card1"&gt;
      &lt;img class="front" src="https://cdn.pixabay.com/photo/2023/09/04/17/48/flamingos-8233303_960_720.jpg" alt=""&gt;
      &lt;img class="back" src="https://cdn.pixabay.com/photo/2023/03/19/05/31/flower-7861942_1280.jpg" alt=""&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/div&gt;</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">css</p>
<pre id="code_1724315871813" class="css" data-ke-language="css" data-ke-type="codeblock"><code>.wrap {
  background: #282828;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.card1 {
  width: 300px;
  height: 450px;
  position: relative;
  perspective: 1100px;
/*  입체적으로 보이도록  */
}
.card1 img {
  position: absolute;
  top: 0;
  left: 0;
  transition: .5s;
  backface-visibility: hidden;
  /*  뒤집히고 안보이도록  */
}
.card1 .front {
  z-index: 1;
}
.card1 .back {
  transform: rotateY(-180deg);
}
.card1:hover .front {
  transform: rotateY(180deg);
}
.card1:hover .back {
  transform: rotateY(0);
}</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">&nbsp;</p>
<p class="codepen" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-height="500" data-default-tab="html,result" data-slug-hash="NWZYoav" data-pen-title="Untitled" data-user="jeunseon" data-ke-size="size16"><span>See the Pen <a href="https://codepen.io/jeunseon/pen/NWZYoav"> Untitled</a> by jeunseon (<a href="https://codepen.io/jeunseon">@jeunseon</a>) on <a href="https://codepen.io">CodePen</a>.</span></p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">
<script src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</p>
<p data-ke-size="size16">&nbsp;</p>
<h4 data-ke-size="size20"><span style="color: #1a5490;"><b>뒤집었을 때 text 가 있는 카드</b></span></h4>
<p data-ke-size="size16"><span style="color: #000000;">html</span></p>
<pre id="code_1724315981884" class="html xml" data-ke-language="html" data-ke-type="codeblock"><code>&lt;div class="wrap"&gt;
  &lt;div class="con2"&gt;
    &lt;div class="card2"&gt;
      &lt;div class="front"&gt;
        &lt;img src="https://cdn.pixabay.com/photo/2018/03/04/17/23/tiger-3198598_1280.jpg" alt=""&gt;
      &lt;/div&gt;
      &lt;div class="back"&gt;
        &lt;div class="text"&gt;
          &lt;h2&gt;Where doex it&lt;br /&gt; come from?&lt;/h2&gt;
          &lt;p&gt;Lorem ipsum dolor sit amet consectetur adipisicing elit. Optio tempora, totam odit temporibus iure eaque unde ut numquam aliquam ullam deserunt facere sequi consectetur reprehenderit perferendis possimus vero ea dolor.&lt;/p&gt;
        &lt;/div&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/div&gt;</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">css</p>
<pre id="code_1724316024263" class="html xml" data-ke-language="html" data-ke-type="codeblock"><code>.wrap {
  background: #282828;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* text 있는 card 뒤집기 */
.card2 {
  width: 300px;
  height: 375px;
  position: relative;
  perspective: 1000px;
  /*  입체적으로 보이도록 원근감을 준다.  */
}
.card2 &gt; div {
  position: absolute;
  top: 0;
  left: 0;
  transition: 1s;
}
.card2 .front {
  
}
.card2 .back {
  background: rgba(0, 0, 0, .5);
  height: 100%;
  padding: 50px 20px 20px 20px;
  box-sizing: border-box;
  color: #fff;
  transform: rotateY(-180deg);
  backface-visibility: hidden;
  /*  뒤집히고 안보이도록  */
}
.card2:hover .front {
  transform: rotateY(180deg);
}
.card2:hover .back {
  transform: rotateY(0);
}</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<blockquote data-ke-style="style3"><b>perspective: 1000px;</b><br /><span style="color: #1a5490;">/* front와 back의 부모에게 입체적으로 보이도록 원근감을 준다 */</span><br /><br /><b>backface-visibility: hidden;</b> <br /><span style="color: #1a5490;">/* front가 뒤집히고 안보이도록 front &gt; img 에 넣는다 */<br /><br /><span style="color: #000000;">.card1&nbsp;.<b>back&nbsp;</b>{ </span><br /><b><span style="color: #000000;">&nbsp;&nbsp;transform:&nbsp;rotateY(-180deg); </span></b><br /><span style="color: #000000;">} </span><br /><span style="color: #000000;">.card1<b>:hover&nbsp;.front</b>&nbsp;{ </span><br /><span style="color: #000000;">&nbsp;<b>&nbsp;transform:&nbsp;rotateY(180deg); </b></span><br /><span style="color: #000000;">} </span><br /><span style="color: #000000;">.card1<b>:hover&nbsp;.back</b>&nbsp;{ </span><br /><b><span style="color: #000000;">&nbsp;&nbsp;transform:&nbsp;rotateY(0); </span></b><br /><span style="color: #000000;">}</span></span><br />/* transform: rotateY() 로 뒤집히는 효과를 준다. */<br /><br /></blockquote>
<p data-ke-size="size16">&nbsp;</p>