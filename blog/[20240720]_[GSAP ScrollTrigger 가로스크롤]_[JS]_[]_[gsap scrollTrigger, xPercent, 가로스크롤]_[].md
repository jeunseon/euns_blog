gsap 가로 스크롤 애니메이션
<a href="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FuvnN0%2FbtsIGytvdm0%2F1kyUlINF0fu7Z7UyxGKOoK%2Fimg.jpg">
    <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FuvnN0%2FbtsIGytvdm0%2F1kyUlINF0fu7Z7UyxGKOoK%2Fimg.jpg" alt="xPercent_Scroll">
</a>

스크롤 내릴 시 가로로 스크롤이 되는 js 코드

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="oNrzpmN" data-pen-title="gsap scrollTrigger 가로스크롤" data-user="jeunseon" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/jeunseon/pen/oNrzpmN">
  gsap scrollTrigger 가로스크롤</a> by jeunseon (<a href="https://codepen.io/jeunseon">@jeunseon</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


```HTML
<!-- gallery -->
<section class="work">
    <ul>
        <li>
            <a href="#">
                <div class="imgBox">
                    <img src="https://cdn.pixabay.com/photo/2023/08/19/13/42/flowers-8200510_960_720.jpg" alt="">
                </div>
            </a>
        </li>
        <li>
            <a href="#">
                <div class="imgBox">
                    <img src="https://cdn.pixabay.com/photo/2023/12/29/18/23/board-game-8476665_1280.jpg" alt="">
                </div>
            </a>
        </li>
        <li>
            <a href="#">
                <div class="imgBox">
                    <img src="https://cdn.pixabay.com/photo/2024/06/17/23/30/trees-8836655_1280.jpg" alt="">
                </div>
            </a>
        </li>
        <li>
            <a href="#">
                <div class="imgBox">
                    <img src="https://cdn.pixabay.com/photo/2024/05/09/17/24/shih-tzu-8751508_1280.jpg" alt="">
                </div>
            </a>
        </li>
        <li>
            <a href="#">
                <div class="imgBox">
                    <img src="https://cdn.pixabay.com/photo/2024/02/09/23/02/trees-8563877_1280.jpg" alt="">
                </div>
            </a>
        </li>
        <li>
            <a href="#">
                <div class="imgBox">
                    <img src="https://cdn.pixabay.com/photo/2024/01/11/12/46/pitbull-8501582_1280.jpg" alt="">
                </div>
            </a>
        </li>
    </ul>
</section>
```

// matchMedia(매치미디어) 속성을 사용해 반응형 스크립트를 작성해준다.


```javascript
$(function(){
    gsap.registerPlugin(ScrollTrigger);

// 1024px 넓이까지 스크롤 되도록 설정.
    ScrollTrigger.matchMedia({
        '(min-width: 1024px)': function(){
            let list = gsap.utils.toArray('.work ul li');
            let scrollTween = gsap.to(list, {
                // Xscroll 만드는 공식.
                xPercent: -100 * (list.length - 1),
                // 원래 리스트의 개수보다 1을 빼서 길이를 구한 후에 가로로 이동
                ease: 'none',
                // 가속도 없이
                scrollTrigger:{
                    trigger:'.work',
                    pin: true,
                    scrub: 1,
                    start: 'center center',
                    end: '300%',
                    // 뷰포트 높이의 300% => 숫자가 높을수록 느려진다.
                    markers: true                    
                }
            })
        }
    })
});
```

**xPercent: -100 \* (list.length - 1),**  
// 원래 리스트의 개수보다 1을 빼서 길이를 구한 후에 가로로 이동하도록 한다.

scrollTrigger: {

     end: ' 300% '

}

// 뷰포트의 높이의 300% 로 길이를 잡는다. => 숫자가 높을수록 가로 스크롤 속도가 느려진다.
