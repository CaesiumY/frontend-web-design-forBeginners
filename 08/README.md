# [8. 원페이지 사이트와 패럴랙스 스크롤링](https://github.com/CaesiumY/frontend-web-design-forBeginners/tree/master/08)

## [08-1] 원 페이지 사이트 만들기

### 기본 원 페이지 사이트 만들기

```html
<a href="섹션 아이디"></a> // 같은 아이디를 가진 섹션으로 이동

<section id="섹션 아이디"></section>
```

부드러운 스크롤을 위해 [scrollTo.js 플러그인](https://github.com/flesler/jquery.scrollTo)을 삽입.

```html
<script>
    $(function() {
        $("nav a").click(function(e) {
            // 링크 클릭시 실행
            $.scrollTo(this.hash || 0, 1500); // 클릭한 링크 섹션으로 스크롤
            e.preventDefault(); // 링크의 원래 기능을 끕니다
        });
    });
</script>
```

### jQuery 플러그인을 사용해 원 페이지 사이트 만들기

#### 원 페이지 사이트를 부드럽게 스크롤할 수 있는 Smint 플러그인

알아서 부드럽게 스크롤 + 네비게이션이 항상 맨 위 + 저용량

```html
<script>
    $("navid").smint(); // navid에는 네비게이션을 연결
</script>
```

[사용법 링크](http://www.outyear.co.uk/smint/)

#### 기본 형태를 만들기 편리한 One Page Scroll 플러그인

css의 트랜스폼 기능을 이용해 화면을 전환.

-   jquery.js
-   onpage.scroll.js
-   onepage-scroll.css

를 모두 링크

```html
<div id="page">
    <section>...</section>
    <section>...</section>
    <section>...</section>
</div>
```

위와 같은 형태를 취해야 함.

```html
<script>
    $(`#page`).onepage_scroll();
</script>
```

[다운 링크](https://github.com/peachananr/onepage-scroll)

#### 사용하기 쉬운 fullPage.js

[깃허브 링크](https://github.com/alvarotrigo/fullPage.js)

-   jquery.fullPage.js
-   jquery.fullPage.css

모두 연결

**<사용 방법>**

1. 네비게이션을 제외한 내용 전체를 감싸는 `<div>`태그와 아이디를 삽입.

    - `<div id="fullpage"></div>`

2. 각 섹션에 `class="section"` 추가
    - `<section class="section"></section>`
3. 섹션 내부 슬라이드에 `class="slide"` 추가
    - `<div class="slide"></div>`
4. 스크립트 태그로 마무리

```html
<script>
    $(document).ready(function() {
        $("#fullpage").fullpage();
    });
</script>
```

#### 앵커 사용하기 (fullpage.js)

data-anchor 속성을 사용하여 원하는 이동포인트로 스크롤
id처럼 중복되면 안 됨.

```html
<section class="section" data-anchor="1st"></section>
```

#### 앵커 옵션 사용하기 (fullpage.js)

스크립트 태그의 플러그인 옵션을 이용해서 앵커 설정 가능

```html
<script>
    $(document).ready(function() {
        $("#fullpage").fullpage({
            anchors: ["1st", "2nd", "3rd"], // 앵커들의 리스트
            menu: "#menu" // 네비게이션의 아이디
        });
    });
</script>
```

`data-menuanchor` 속성을 사용해 네비게이션 바의 선택된 항목 강조 표시 활성화

[다른 속성 살펴보기](https://github.com/alvarotrigo/fullPage.js#options)

<hr>

## [8-2] 패럴랙스 스크롤링 효과 만들기

패럴랙스란 화면을 스크롤할 때 애니메이션 효과를 주는 것. PC용 사이트에 적합.

### 원리

내용 레이어가 위로 움직일 때 배경 레이어를 반대 방향으로 움직이거나, 같은 방향으로 시간차를 두고 움직이는 것.

### jQuery 소스를 추가해서 만들기

배경 이미지가 삽입된 요소에 `data-type` 과 `data-speed` 속성을 추가.

> `data-*` 속성은 웹 문서의 레이아웃이나 내용에는 영향을 주지 않으면서 특정한 속성을 지정하고 싶을 때 사용자가 원하는 이름으로 만들 수 있는 속성입니다.

```html
<section data-type="background" data-speed="0.5">
    <article><img src="" /></article>
</section>
```

jQuery를 연결한 다음,

```html
<script>
    $(document).ready(function() {
        // 줄여서 $로 사용하기도 함
        var wd = $(window); // 윈도우 객체를 변수로 지정
        $('section[data-type="background"]').each(function() {
            //위의 data-type값
            var bg = $(this); // 현재 섹션 요소를 변수로 지정
            $(window).scroll(function() {
                // 스크롤 이벤트가 발생하면
                var yPos = -(wd.scrollTop() / bg.data("speed")); // -(스크롤 얼마나)
                var coords = "50%" + yPos + "px"; // 좌표값 생성
                bg.css({ backgroundPosition: coords }); // css 속성 값을 바꿈
            });
        });
    });
</script>
```

~~(어렵다)~~

### jQuery 플러그인을 이용한 패럴랙스 효과 만들기

[jQuery 홈페이지](https://jquery.com/)

#### Stellar.js 플러그인

[링크](https://plugins.jquery.com/stellar/)

사용법이 간단한 것이 장점.

```js
$("#main").stellar();
```

#### ScrollMagic 플러그인

[링크](http://scrollmagic.io/)

#### parallax-scroll 플러그인

[데모 링크](https://parallax-scroll.aenism.com/)

배경이 적용되는 요소에 `bg-holder`라는 클래스를 추가하고, `data-width`, `data-height`를 통해 크기를 조절

```html
<div class="bg-holder" data-width="1200" data-height="730"></div>
```

```html
<script>
    $(".bg-holder").parallaxScroll({
        friction: 0.3 // 효과 강도
    });
</script>
```

#### 섹션이 화면에 가득차게 만들기

```html
<script>
    $(function() {
        $(window).resize(function() {
            $(".container")
                .width($(window).width())
                .height($(window).height());
            $(".content").each(function() {
                $(this)
                    .css("margin-left", ($(this).width() / 2) * -1 + "px")
                    .css("margin-top", ($(this).height() / 2) * -1 + "px");
            });
        });

        setTimeout(function() {
            $(window).resize();
        }, 1000);
    });
</script>
```
