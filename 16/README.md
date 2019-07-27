# [16. 부트스트랩으로 웹 사이트 만들기](https://github.com/CaesiumY/frontend-web-design-forBeginners/tree/master/16)

## [16-1] 부트스트랩 시작하기

[부트스트랩 링크](https://getbootstrap.com/)

### 소스 연결하기

1. 다운로드해서 파일을 직접 링크하기
   
2. CDN으로 링크하기

> 나머지는 그냥 부트스트랩이라 패스

## [16-2] 미디어 쿼리와 그리드 시스템

### 부트스트랩의 미디어 쿼리

부트스트랩은 기본적으로 12개의 칼럼을 가진 그리드 시스템을 사용

- 기본형식: .col-화면종류-묶을 칼럼 갯수
```html
<div class="col-md-3"></div>
```

- 전체 형식

```html
<div class="container">
    <div class="row">
        <div class="col-md-3"></div>
    </div>
</div>
```

이렇게 `container` > `row` > `col` 의 형식을 취해야 함

- 디스플레이

[공식 문서 링크](https://getbootstrap.com/docs/4.3/utilities/display/)

속성|의미
|---        |---|
.d-none     | 화면에서 감춤
.d-inline   | 인라인 레벨 요소로 표시
.d-block    | 블록 레벨 요소로 표시
.d-sm-none  | 작은 크기 화면에서 감춤
.d-sm-block | 작은 크기 화면에서 블록 레벨로 표시
.d-md-none  | 중간 크기 화면에서 감춤
.d-me-block | 중간 크기 화면에서 블록 레벨로 표시
