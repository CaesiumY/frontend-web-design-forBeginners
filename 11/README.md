# [11. 캐러셀](https://github.com/CaesiumY/frontend-web-design-forBeginners/tree/master/11)

## [11-1 캐러셀이란?]

### 여러 형태의 캐러셀

> 캐러셀 : 몇 가지 내용을 하나씩 회전하면서 보여주고, 마지막 내용 다음에는 다시 첫 번째 내용으로 연결해서 보여주는 것을 뜻함.

## [11-2 bxslider 플러그인]

[bxslider 공식 사이트](https://bxslider.com/)

```
<script>
    $(function() {
        $('요소명').bxSlider({
            slideWidth: 600,    // 화면 너비 설정
            captions: true      // img 태그의 title 속성을 캡션으로 추가
        });
    });
</script>
```

## [11-3] Owl Carousel 플러그인

[Owl Carousel 공식 사이트](https://owlcarousel2.github.io/OwlCarousel2/)

> 무려 css 2개, js 4개(jquery 포함)를 연결해야한다.

```
<script>
    $(function() {
        $('요소 이름').owlCarousel({
            items: 3,                   // 표시할 항목 개수
            margin: 10,                 // 항목 사이의 간격
            loop: true,                 // 무한 반복
            autoplay: true,             // 자동 스크롤
            autoplayTimeout: 3000,      // 자동 스크롤 시간 간격
            autoplayHoverPause: true,   // 마우스 올리면 일시정지
            nav: true,                  // 네비게이션 활성화
            navText:['이전', '다음']     // 버튼 텍스트 지정
        })
    })
</script>

<div class="요소 이름">
    <div class="item">
        <img src=""></div>
    </div>
</div>
```

## [11-4] 그 밖의 캐러셀 플러그인

### SlideJS 플러그인

[링크](https://slidesjs.com/)

### Camera slideshow 플러그인

[링크](https://github.com/pixedelic/Camera)