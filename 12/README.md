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