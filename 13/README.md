# [13. 웹 폰트](https://github.com/CaesiumY/frontend-web-design-forBeginners/tree/master/13)

## [13-1] 웹 폰트 표시 단위

### 상대 크기로 표시하는 em

px 단위가 항상 고정된 크기라면, em은 **상대 크기**로 표시하는 단위

부모 요소에서 지정한 폰트 크기를 1em 으로 놓고 상대 크기를 계산

이렇게 부모 요소 크기를 기준으로 하기 때문에, 부모가 여러 단계로 중첩되어 있으면 **자식 요소의 폰트 크기도 점점 커지는 문제점**이 발생.

### em의 문제점을 해결하기 위한 rem

위의 부모 요소 크기 기준으로 한 방법의 문제점을 막기 위한 단위가 바로 rem(Root Em).

루트에서 지정한 크기를 기준값으로 사용하기 때문에 중간에 값이 바뀔 염려가 없음.

~~모르겠으면 그냥 rem~~

아쉽게도 오래된 인터넷 익스플로러 버전에서는 인식 불가능
~~어딜가나 민폐인 익스플로러~~

이를 피하기 위해서 px를 함께 선언

```html
<style>
    div {
        font-size: 30px;
        font-size: 1.5rem;
    }
</style>
```

둘 다 쓰일 때, rem을 지원하지 않으면 px를 사용하게 됨

### 줄 바꿈 유지하기

보통 요소 너비가 달라지면 글자 크기를 그대로 유지하고 자동으로 줄 바꿈이 되지만,

[FlowType.js 플러그인](https://simplefocus.com/flowtype)을 사용하면 요소 너비를 기준으로, 원래 줄 형태를 유지하고 글자 크기를 변경하게 됨

```js
$('요소').flowtype();
```


## [13-2] CSS로 웹 폰트 사용하기

### 웹 폰트 파일을 포함하는 간단한 방법

```html
<style>
    @font-face {
        font-family: Blackout, Arial Black;         //지원하지 않으면 Arial Black
        src: url('Blackout.ttf') format('truetype');
    }
</style>
```
Blackout이라는 자신만의 폰트 이름을 정의

### 다양한 폰트 파일 형식

- TTF (True Type Font)
- OTF (Open Type Font)
- EOT (Embedded Open Type)
- SVG (Scalable Vector Graphic)
- WOFF (Web Open Font Format)

예전 버전을 위해서는 TTF, 최신 버전은 WOFF 타입
ttf는 용량이 크기 때문.

```html
<style>
    @font-face {
        font-family: Blackout, Arial Black;
        src: 
        local('Blackout'),
        url('Blackout.eot'),
        url('Blackout.woff') format('woff'),
        url('Blackout.ttf') format('truetype');
    }
</style>
```
1. 로컬에서 찾아봄
2. 익스플로러 8 이하 버전을 위한 설정
3. woff를 지원하면 여기서 멈춤
4. 마지막 수단

## [13-3] 구글 웹 폰트 사용하기

### 구글 웹 폰트를 사용하는 방법

[구글 폰트 링크](https://fonts.google.com/)

별 거 없고 선택 후 복사 붙여넣기면 완성

### 한글 웹 폰트 사용하기

우측에 Korean을 선택할 경우 한글 웹 폰트만 모아서 보는 게 가능


`Family Selected` 에서 `CUSTOMIZE`를 선택한 후, `Languages`에서 `Korean` 선택