# [8. 원페이지 사이트와 패럴랙스 스크롤링](https://github.com/CaesiumY/frontend-web-design-forBeginners/tree/master/08)

## [08-1] 원 페이지 사이트 만들기

### 기본 원 페이지 사이트 만들기
```
<a href="섹션 아이디"></a>  // 같은 아이디를 가진 섹션으로 이동

<section id = "섹션 아이디"></section>
```

부드러운 스크롤을 위해 [scrollTo.js 플러그인](https://github.com/flesler/jquery.scrollTo)을 삽입.

```
<script>
    $(function() {
        $('nav a').click(function(e) {  // 링크 클릭시 실행
            $.scrollTo(this.hash || 0, 1500);   // 클릭한 링크 섹션으로 스크롤
            e.preventDefault(); // 링크의 원래 기능을 끕니다
        });
    });
</script>
```

### jQuery 플러그인을 사용해 원 페이지 사이트 만들기

#### 원 페이지 사이트를 부드럽게 스크롤할 수 있는 Smint 플러그인
알아서 부드럽게 스크롤 + 네비게이션이 항상 맨 위 + 저용량

```
<script>
    $('navid').smint();   // navid에는 네비게이션을 연결
</script>
```

[사용법 링크](http://www.outyear.co.uk/smint/)

#### 기본 형태를 만들기 편리한 One Page Scroll 플러그인
css의 트랜스폼 기능을 이용해 화면을 전환.

- jquery.js
- onpage.scroll.js
- onepage-scroll.css
  
를 모두 링크

```
<div id="page">
  <section>...</section>
  <section>...</section>
  <section>...</section>
</div>
```
위와 같은 형태를 취해야 함.

```
<script>
    $(`#page`).onepage_scroll();
</script>
```

[다운 링크](https://github.com/peachananr/onepage-scroll)


#### 사용하기 쉬운 fullPage.js

[깃허브 링크](https://github.com/alvarotrigo/fullPage.js)

- jquery.fullPage.js
- jquery.fullPage.css

모두 연결

**<사용 방법>**

1. 네비게이션을 제외한 내용 전체를 감싸는 `<div>`태그와 아이디를 삽입.   
   - `<div id="fullpage"></div>`

2. 각 섹션에 `class="section"` 추가
   - `<section class="section"></section>`
3. 섹션 내부 슬라이드에 `class="slide"` 추가
   - `<div class="slide"></div>`
4. 스크립트 태그로 마무리

```
<script>
    $(document).ready(function() {
        $("#fullpage").fullpage();
    });
</script>
```

#### 앵커 사용하기 (fullpage.js)
data-anchor 속성을 사용하여 원하는 이동포인트로 스크롤
id처럼 중복되면 안 됨.

```
<section class="section" data-anchor="1st"></section>
```

#### 앵커 옵션 사용하기 (fullpage.js)
스크립트 태그의 플러그인 옵션을 이용해서 앵커 설정 가능
```
<script>
    $(document).ready(function() {
        $("#fullpage").fullpage({
            anchors:["1st", "2nd", "3rd"],  // 앵커들의 리스트
            menu: "#menu"   // 네비게이션의 아이디
        });
    });
</script>
```

`data-menuanchor` 속성을 사용해 네비게이션 바의 선택된 항목 강조 표시 활성화

[다른 속성 살펴보기](https://github.com/alvarotrigo/fullPage.js#options)
