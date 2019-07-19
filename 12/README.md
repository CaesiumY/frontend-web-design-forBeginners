# [12. SVG](https://github.com/CaesiumY/frontend-web-design-forBeginners/tree/master/12)

## [12-1] SVG 이미지란?

### 특징

#### 화질에 영향을 받지 않는다!
Scalable Vector Graphic의 약자로, scale이 가능한 벡터 이미지라는 뜻.

고로 이미지 크기를 늘리거나 줄이더라도 화질에 영향을 주지 않음.

#### 스타일 수정이 쉽다

코드를 사용해 이미지 수정이 가능하다

#### XML 기반의 문서

svg태그 안에 정보가 담긴다.

#### 애니메이션이나 CSS3 효과 적용 가능

웹 문서 안에 소스 코드 형태로 삽입 가능하기에 css 속성을 사용하여 애니메이션 및 css3 기능 적용 가능

### SVG 이미지는 어디에 사용할까

#### 로고와 아이콘

화질에 영향을 주지 않기 때문에 안심

#### 데이터 시각화

d3.js 나 Raphael 같은 프레임워크는 데이터 시각화에 svg 이미지를 사용한다.

### SVG 이미지 최적화

[SVG Optimizer 링크](https://petercollingridge.appspot.com/svg-optimiser)

Node.js 기반이라면 [SVGO](https://github.com/svg/svgo)

## [12-2] SVG 이미지 사용하기

### SVG 파일을 삽입하는 방법

#### `<img>` 태그 사용하기
```html
<img src="svg 파일" width="300" height="300">
```

#### 소스 그대로 넣기

`<svg>` 태그를 그대로 복사하여 삽입.

### SVG 파일을 지원하지 않는 하위 버전 대응하기

#### Modernizr 스크립트 추가

[Modernizr 링크](https://modernizr.com/)

1. Add your detects 클릭
2. SVG 선택
3. 빌드
4. 나온 js 파일을 연결

```html
<script>
    if (Modernizr.svg) {
        // 지원할 경우
    } else {
        // 지원하지 않을 경우
    }
</script>
```

### SVG 대신 PNG 파일 표시하기

[소스 복붙이 필요.](https://coderwall.com/p/u_ngaa/fallback-svg-to-png-in-img-element)

```js
// Check if browser can handle SVG
if(!Modernizr.svg){ // 지원 안 할 경우
    // Get all img tag of the document and create variables
    var i=document.getElementsByTagName("img"),j,y;

    // For each img tag
    for(j = i.length ; j-- ; ){
        y = i[j].src
        // If filenames ends with SVG
        if( y.match(/svg$/) ){
            // Replace "svg" by "png"
            i[j].src = y.slice(0,-3) + 'png'
        }
    }
}
```
