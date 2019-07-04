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