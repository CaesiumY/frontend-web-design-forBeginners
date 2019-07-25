# [15. 플렉스 박스로 웹 사이트 만들기](https://github.com/CaesiumY/frontend-web-design-forBeginners/tree/master/15)


## [15-1] 웹 사이트 구상하기

> 책 보고 따라하기

> 헤더, 네비바, 섹션, 아티클, 푸터 등 시맨틱 요소들 설명

## [15-2] 캐러셀 삽입하기

bxSlider 플러그인 사용

[이전 자료 참고](https://github.com/CaesiumY/frontend-web-design-forBeginners/tree/master/11)

## [15-3] 플렉스 박스 사용하기

### 미디어 쿼리를 사용해 이미지 표시

```css
.img {
    display: none;  // 평소엔 숨김(764px 이하의 경우)
}

@media screen and (min-width:764px) {   // 764px 이상일 경우
    .img {
        display: block; // 이미지를 화면에 표시
    }
}
```

### 플렉스 박스 사용

```css
.intro {
    display: flex;
}

.text {
    flex: 2;    
}

.img {
    flex: 1;
}
```

텍스트와 이미지를 2대 1 비율로 배치.

### 플렉스에서 여백 두기

```css
.list {
    display: flex;
    justify-content: space-between; // 첫 번째의 왼쪽과, 마지막의 오른쪽 블록에 여백 X
}
.item {
    flex-basis: 22%;    // 기본 너비 설정
}
```