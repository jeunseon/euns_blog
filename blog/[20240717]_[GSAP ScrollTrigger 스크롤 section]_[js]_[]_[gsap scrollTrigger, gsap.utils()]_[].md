
```javascript
    gsap.timeline({
        scrollTrigger:{
            trigger:'.visual',
            start:'top top',
            end:'bottom top',
            scrub:1,
            pin:true,
            // 스크롤트리거 할 동안 영역이 고정될수 있도록
            markers:true
        }
    })
    .to('.visual h1', {'opacity':'1', 'ease':'none', 'duration':'10'}, 5)
    .to('.visual img', {'scale':'0.4', 'ease':'none', 'duration':'10', 'opacity':'0.3'}, 5)
```

스크롤 하면 배경 이미지는 점점 작아지고 text가 나타나도록

scrollTrigger 의 pin은 스크롤이벤트가 끝날때까지 화면이 고정되도록 한다.

```javascript
    // toArray()는 문서 내 요소를 배열로 만든다.
	// imgBox 배열로 만들고 이 배열을 forEach()로 배열을 반복문으로 함수 사용
    gsap.utils.toArray('.imgBox').forEach(function(imgBox){
        gsap.timeline({
            scrollTrigger: {
                trigger:imgBox,
                start:'50% 100%',
                toggleClass: {'targets': imgBox, className: 'active'},
                // toggleClass로 active 적용
                scrub: 1,
                markers: true
            }
        })

    })
```

gsap.utils. toArray()는 문서 내 요소를 배열로 만드는 메소드.

forEach() 는 배열을 반복문으로 사용하여 함수 적용.

```javascript
    gsap.utils.toArray('.textBox').forEach(function(textBox){
        gsap.timeline({
            scrollTrigger: {
                trigger: textBox,
                start:'50% 80%',
                toggleClass: {'targets' : textBox, className : 'active'},
                // toggleClass로 active 적용
                scrub: 1,
                markers: true
            }
        })

    })
```

toggleClass로 클래스를 첨가, 삭제한다.