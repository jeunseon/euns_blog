\- 스크롤 시 애니메이션을 표시하기 위한 간단한 jQuery 플러그인

[https://maximzhurkin.github.io/jquery-scrolla/](https://maximzhurkin.github.io/jquery-scrolla/)

```
<script src="https://cdn.jsdelivr.net/npm/jquery-scrolla@0.0.3/dist/js/jquery.scrolla.min.js"></script>
```

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="KKjgywP" data-pen-title="Untitled" data-user="jeunseon" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/jeunseon/pen/KKjgywP">
  Untitled</a> by jeunseon (<a href="https://codepen.io/jeunseon">@jeunseon</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


HTML 코드

```
<div class="wrap">
    <section class="visual en animate" data-animate="bounceIn">
        <div class="inner">
            <div class="textBox">
                <p class="title">My<span class="en2">Work</span></p>
                <p class="subTitle">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Totam, dolorum?</p>
                <p class="text">Reprehenderit vitae quaerat, blanditiis, quod magni autem, voluptatem ab perferendis sit natus nisi inventore? Voluptatibus, excepturi porro voluptatem officiis aspernatur necessitatibus corrupti!</p>
            </div>
            <div class="aniBox">
                <img src="https://cdn.pixabay.com/photo/2017/10/23/17/50/circle-2881850_1280.png" class="spin">
                <img src="https://cdn.pixabay.com/photo/2012/04/24/13/58/arrow-40168_960_720.png" class="arrow">
            </div>
        </div>
    </section>
</div>
```

```
data-animate\="bounceIn"
```

scrolla.js 사용하기 위해 **data-animatie="bounceIn"** 을 붙여준다.

그다음 animate가 적용될때의 css를 적기위해 section의 class에 animate를 추가하고

css에 **animate\_\_bounceIn** 로 css를 적는다.

CSS 코드

```
body {
    font-size: 16px;
    line-height: 1.6;
}
.wrap {
    position: relative;
    margin: 0 auto;
    overflow: hidden;
    background: #000;
    color: #fff;
    margin-bottom: 3000px;
}

.visual {
    padding-top: 150px;
    height: 100vh;
    box-sizing: border-box;
}
.visual .inner {
    width: 70%;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
}
.visual .inner .textBox{
    width: 60%;
    line-height: 1.4;
}
.visual .inner .textBox .title {
    font-size: 150px;
}
.visual .inner .textBox .title .en2{
    font-size: 170px;
}
.visual .inner .textBox .subTitle {
    font-size: 30px;
    margin: 10px 0;
}
.visual .inner .aniBox {
    width: 350px;
    height: 350px;
    position: relative;
    margin-top: 80px;
}
.visual .inner .aniBox img {
    width: 100%;
    position: absolute;
    display: inline-block;
}
.visual .inner .aniBox img.spin{
    left: 0;
    top: 0;
    animation: spin 10s linear infinite;
}
.visual .inner .aniBox img.arrow{
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 20%;
}

@keyframes spin{
    0% {transform: rotate(0deg);}
    100% {transform: rotate(360deg);}
}

/* visual motion이 붙을 때 애니메이션 */
.visual.animate__bounceIn .inner .textBox {transform: translate3d(0, 0, 0);}
.visual.animate__bounceIn .inner .textBox p {animation-name: textAni3; animation-duration: 1s;}
@keyframes textAni3 {
    0% {opacity: 0;}
    40% {opacity: 0; transform: translate3d(0, 50px, 0)}
}

.visual.animate__bounceIn .inner .textBox p:nth-child(2) {animation-duration: 1.2s;}
.visual.animate__bounceIn .inner .textBox p:nth-child(3) {animation-duration: 1.4s;}
```

JS 코드

```
$(function(){
    $('.animate').scrolla({
        mobile: true,
        once: false
        // scroll 할때마다 적용되도록 false
    });
});
```