# [7. 화면 크기에 반응하는 미디어쿼리 알아보기](https://github.com/CaesiumY/frontend-web-design-forBeginners/tree/master/07)

## [7-1] 뷰포트와 미디어 쿼리 알아보기

```
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

1. `content="width=device-width`: 문서 너비를 현재 기기의 너비에 맞춥니다.
2. `initial-scale=1.0`: 문서를 불러와 화면에 표시할 때 기본 배율을 1로 지정합니다.

### 뷰포트 속성 정리
- `width`: 뷰포트의 너비. 기본값 device-width
  
- `height`: 뷰포트의 높이. 기본값 device-height  
- `initial-scale`: 초기 배율. 기본값 1(1보다 작은 값이면 축소페이지를, 1보다 큰 값이면 확대 페이지를 표시)
- `user-scale`: 사용자가 페이지를 확대/축소할 수 있는 지 여부 지정. 기본값 yes
- `minimum-scale`: 확대/축소할 수 있는 최솟값(가로 기준). 기본값 0.25
- `maximum-scale`: 확대/축소할 수 있는 최댓값(가로 기준). 기본값 0.25


### 미디어 쿼리 구문

```
@media [only | not] 미디어 유형 [and 조건] * [and 조건]
```

- `media`: 스타일 시트 안에서 미디어 쿼리를 시작하는 속성.
  
- `only | not`: only를 사용하면 only 다음의 미디어 유형에만 적용되고, not을 사용하면 not 다음의 미디어 유형을 제외한 나머지 유형에만 적용.
- `미디어 유형`: 적용할 기기를 지정. 쉼표(,)를 이용하여 여러 미디어 유형 나열. (ex. screen)
- `조건`: 미디어 유형 외에 기기와 관련된 조건을 지정. 조건은 괄호()로 묶어서 나열하며, and 연산자를 사용.
  - width
  - height
  - device-width
  - device-height
  - orientation
  - aspect-ratio
  - deveice-aspect-ratio  
  - resolution
  - color
  - color-index

#### *예시
```
@media screen and (min-width:921px) and (max-width: 1260px){}
```

## 미디어 쿼리를 지원하지 않는 브라우저에 대응하려면

```
<!--[if lt IE 9]>
	<script src="js/respond.js"></script>
<![endif]-->
```
익스플로러 6~8 버전을 위한 자바스크립트 라이브러리 다운.

[다운 링크](https://github.com/scottjehl/Respond)

<hr>

## [7-2] 미디어 쿼리 사용하기

### 1. 외부 CSS 파일로 정의하기

#### `<link>` 태그 사용하기

```
<link rel="stylesheet" media="미디어 쿼리 조건" href="style.css">
```

```
<link rel="stylesheet" media="screen and (max-width:768px)" href="style.css">
```

#### `@import` 구문 사용하기

```
@import url(css 파일경로) 미디어 쿼리 조건
```
```
@import url("css/style.css") screen and (max-width:768px)
```

### 2. 웹 문서에서 직접 정의하기

#### `<style>` 태그에서 조건 지정하기

```
<style media="미디어 쿼리 조건">
    스타일 규칙들
</style>
```
```
<style media="screen and (max-width:320px)">
    body {
        ...
    }
</style>
```

#### `@media` 구문으로 조건 지정하기
```
<style>
    @media 미디어 쿼리 조건 {
        스타일 규칙들
    }
</style>
```
```
<style>
    @media screen and (max-width:320px) {
        body {
            ...
        }
    }
</style>
```

<hr>

## [07-3] 가변 이미지

### 기본 방법

그냥 `width:100%` 로 지정하게 되면 화면 너빗값에 따라 이미지의 너비가 줄어들거나 늘어나게 되지만, 원래 크기 이상으로 늘어나면 화질이 깨짐.

그래서 원래 이미지 이상으로 늘어나지 않도록 `max-width` 속성을 사용.

`height:auto;` 를 사용해 너빗값에 따라 높이도 자동 조절되도록 설정.

```
img {
    max-width:100%;
    height: auto;
}
```

### 문제점

* 용량이 큰 이미지가 포함된 페이지를 모바일에서 볼 경우 -> **데이터 폭발**

* 미디어 쿼리를 사용해 모바일에서는 작은 이미지를 다운하자!
  * 브라우저에서 이미지를 Preload(미리 로딩)하기 때문에 결국 둘 다 다운받게 됨 -> **데이터 대폭발**

* 게다가 모바일에서 옆으로 보면 이미지가 다르게 보인다... 전용 이미지가 또 필요.


### `<img>` 태그의 `srcset` 속성

이 속성은 기본으로 사용할 이미지 파일 경로를 지정하고, px **너비**나 **밀도**에 맞는 여러 이미지를 함께 지정.

```
<img src="이미지" srcset="파일1, 파일2, 파일3">
```

#### 픽셀 너비 서술자
'파일 이름, 너비w'

```
<img src="sky.png" srcset="sky-large.png 1024w, sky-medium.png 640w, sky-small.png"> 
```

#### 픽셀 밀도 서술자
```
<img src="sky.png" srcset="sky-large.png 3x, sky-medium.png 2x, sky-small.png"> 
```

### <picture 태그>

| 속성 | 설명 |
|:-----:|:------:|
|media| srcset에 지정한 이미지를 표시하기 위한 조건 |
|sizes| 파일 크기 |
|srcset| 이미지 파일 경로 |
|type| 파일 유형 |

#### 예시코드

```
<picture>
    <source srcset="lime-1000.jpg" media="(min-width:1024px)">
    <source srcset="lime-740.jpg" media="(min-width:768px)">
    <source srcset="lime-300.jpg" media="(min-width:320px)">
    <img src="lime.jpg" alt="lime" style="max-width:100%">
</picture>
```