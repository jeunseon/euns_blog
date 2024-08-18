<p data-ke-size="size16">menu click 시 스무스하게 스크롤되도록.</p>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">CSS 영역</p>
<pre id="code_1723961858476" class="css" data-ke-language="css" data-ke-type="codeblock"><code>body, html {
  scroll-behavior: smooth;
  /*  스크롤이 스무스하게 움직이려면 필수!!  */
}
header {
  position:fixed;
  top: 0;
  z-index:100;
  width: 100%;
}
.gnb {
  display: flex;
  justify-content: center;
}
.gnb li a {
  display:inline-block;
  color: #fff;
  text-decoration: none;
  padding: 20px 30px;
}</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p data-ke-size="size16">JS 영역</p>
<pre id="code_1723962091345" class="javascript" data-ke-language="javascript" data-ke-type="codeblock"><code>window.onload = function(){
  let menulist = document.querySelector('.gnb li a');
  
  // section.scroll. menu click 시 스크롤될 section
  let contents = document.querySelectorAll('.scroll');
  
  let doc = document.querySelector('html, body');
  
  menulist.addEventListener('click', (e) =&gt; {
  	// index 번호
    let idx = this.index();
    // 메뉴 스크롤되었을때 section의 번호
    let sectionIdx = contents.eq(idx);
    // 해당 section의 스크롤 높이
    let offSetTop = sectionIdx.offset().top;
    
    doc.stop().animate({scrollTop: offSetTop}, 800);
    return false;
  });
}</code></pre>
<p data-ke-size="size16">&nbsp;</p>
<p class="codepen" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-height="300" data-default-tab="html,result" data-slug-hash="OJeQyOq" data-pen-title="menu click scroll" data-user="jeunseon" data-ke-size="size16"><span>See the Pen <a href="https://codepen.io/jeunseon/pen/OJeQyOq"> menu click scroll</a> by jeunseon (<a href="https://codepen.io/jeunseon">@jeunseon</a>) on <a href="https://codepen.io">CodePen</a>.</span></p>
<p data-ke-size="size16">
<script src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</p>
<p data-ke-size="size16">&nbsp;</p>