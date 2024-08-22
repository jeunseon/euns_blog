[gsap 의 애니메이션 참고 사이트](https://gsap.com/resources/get-started/)

[스크립트 연결](https://cdnjs.com/libraries/gsap)

<script src="[https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js](https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js)"></script>

<script src="[https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js](https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js)"></script>

---

## **gsap.timeline**

▶ 시간에 배치하는 트윈용 컨테이너로 타임라인 재생헤드가 이동함에 따라 하위 트윈을 스크럽하고 그에 따라 렌더링.

**※ 트윈이란?**

트윈 은 모든 애니메이션 작업을 담당합니다 . 고성능 속성 세터 라고 생각 하면 됩니다. 대상(애니메이션화하려는 객체), 지속 시간, 애니메이션화하려는 속성을 입력한 다음, 트윈의 재생 헤드가 새 위치로 이동하면 해당 지점에서 속성 값이 무엇이어야 하는지 파악하여 그에 따라 적용합니다.

**※ 트윈을 만드는 일반적인 방법** 

-   gsap.to()
-   gsap.from()
-   gsap.fromTo()

gsap.to(".circle", { x: 40, fill: 'blue', });

▶ 현재상태에서 시작하여 정의된 값으로 애니메이션 적용  
  
gsap.from(".circle", { x: -40, fill: 'blue', });  
▶ 정의된 값에서 애니메이션을 시작하여 현재상태에서 끝나는 역방향

  
gsap.fromTo( ".circle",{ x: -40, fill: 'blue', }, { x: 40, fill: 'green' });

▶ 시작과 종료값을 모두 정리

GSAP는 특정요소(ScrollTrigger에서 정한 영역)에 애니메이션을 연결하여 해당 요소가 뷰포트에 있을 때만 재생되도록 한다. 이렇게 하면 성능이 향상되고 화려한 애니메이션을 볼 수 있다.

```
<script>

    gsap.registerPlugin(ScrollTrigger);

    $(function(){
        // to
        gsap.timeline({
            scrollTrigger:{
                trigger:'.con02 ul',
                // 트리거 대상
                start:'top 90%',
                // 스크롤트리거가 시작되는 지점
                // con02 ul 의 top부분으로. 브라우저의 90% 지점에서 시작
                end: '20% 100%',
                // con02 ul의 20%와 브라우저 100%가 만날때 끝난다.
                scrub: 2,
                // 부드럽게 되감기
                markers: true
                // 시작과 끝나는 영역의 구역이 보일수 있는 markers. 끝나면 주석처리
            }
        })
        .to('.con02 li:nth-child(1)', { y:'-400px', duration: 1, ease: 'none' }, 0.2 )
        .to('.con02 li:nth-child(2)', { y:'-400px', duration: 1, ease: 'none' }, 0.4 )
        .to('.con02 li:nth-child(3)', { y:'-400px', duration: 1, ease: 'none' }, 0.6 )
        .to('.con02 li:nth-child(4)', { y:'-400px', duration: 1, ease: 'none' }, 0.8 )

        // fromTo
        gsap.timeline({
            scrollTrigger:{
                trigger:'.con03',
                // 트리거 대상
                start:'top 100%',
                end:'100% 100%',
                scrub: 2,
                markers: true
            }
        })
        .fromTo( '.con03 span.a', { y:'400%' }, { y:'0' }, 1.2 )
        .fromTo( '.con03 span.b', { y:'400%' }, { y:'0' }, 1.4 )
        .fromTo( '.con03 span.c', { y:'400%' }, { y:'0' }, 1.6 )
        .fromTo( '.con03 span.d', { y:'400%' }, { y:'0' }, 1.8 )
        .fromTo( '.con03 span.e', { y:'400%' }, { y:'0' }, 2.0 )
    });

</script>
```