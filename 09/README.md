# [9. 그리드 레이아웃](https://github.com/CaesiumY/frontend-web-design-forBeginners/tree/master/09)

## [09-1] 다단 칼럼을 사용해 그리드 레이아웃 만들기

### 다단 칼럼으로 레이아웃 만들기

```html
<style>
    #columns {
        column-count: 2; // 칼럼 개수 2개
        column-gap: 10px; // 칼럼 사이 간격 10px
    }

    @media (min-width: 1100px) {
        // 화면 너비가 1100이상일 때
        #columns {
            column-count: 4; // 칼럼 개수 2개
        }
    }
</style>
```

## [09-2] jQuery 플러그인을 사용해 그리드 레이아웃 만들기

### vGrid 플러그인

[깃허브 링크](https://github.com/xlune/jQuery-vGrid-Plugin)

```html
<script>
    $("#container").vgrid({
        time: 400, // 애니메이션 실행 시간
        delay: 30, // 애니메이션 지연 시간
        wait: 500 // 애니메이션 대기 시간
    });
</script>
```

## [09-3] 플렉스 박스 사용하기

### 플렉스 박스 레이아웃

그리드 레이아웃을 기본으로 하여 플렉스 아이템을 원하는 위치에 배치하는 것. <br>
플렉스 레이아웃을 사용하려면 콘텐츠를 플렉스 컨테이너로 묶고, 그 안에 플렉스 박스를 배치.

### 플렉스 컨테이너 속성

-   `display` : 플렉스 아이템을 감싸는 요소를 **플렉스 컨테이너**로 쓰려고 할 때 사용하는 속성

    -   `flex` : 컨테이너 안의 플렉스 아이템을 블록 레벨 요소로 배치
    -   `inline-flex` : 컨테이너 안의 플렉스 아이템을 인라인 레벨 요소로 배치

-   `flex-direction`: 플렉스 컨테이너 안에서 플렉스 아이템을 배치하는 주축과 방향을 지정. 기본값은 row

    -   `row` : 주축을 가로로 지정.
    -   `row-reverse` : 가로 순서를 반대로
    -   `column` : 주축을 세로로 지정
    -   `column-reverse` : 세로 순서를 반대로

-   `flex-wrap` : 플렉스 아이템을 여러 줄에 걸쳐 표시. 기본값은 nowrap

    -   `nowrap` : 플렉스 아이템을 한 줄에 표시 -> 컨테이너 밖으로 빠져나갈 수 있음
    -   `wrap` : 플렉스 아이템을 여러 줄로 표시 -> 꽉차면 다음 줄로
    -   `wrap-reverse` : 여러 줄로 표시하나, 아래에서부터 줄을 세움

-   `flex-flow` : flex-direction 속성과 flex-wrap 속성을 한꺼번에 지정. 기본값은 row nowrap

    -   `flex-flow: row wrap`

-   `justify-content` : 주축에서 플렉스 아이템 간 간격을 지정. text-align과 비슷

    -   `flex-start` : 시작점에 맞춰 배치
    -   `flex-end` : 끝점에 맞춰 배치
    -   `center` : 중앙에 맞춰 배치
    -   `space-between` : 첫 번째 아이템과 끝 아이템을 양 끝에 배치한 후, 나머지는 같은 간격으로 배치 (양쪽 정렬)
    -   `space-around` : 모두 같은 간격으로 배치

-   `align-content` : 교차축에서 플렉스 아이템 간의 간격을 지정. 위의 justify-content와 같은 속성값을 씀.

    -   `stretch` : 아이템을 늘려서 간격 없이 배치

-   `align-items` : 교차축에서 플렉스 아이템의 상대 위치와 크기를 지정
    -   `flex-start` : 세로로 맨 위에 배치
    -   `flex-end` : 세로로 맨 아래에 배치
    -   `center` : 세로로 중앙에 배치
    -   `baseline` : 세로로 기준선에 배치
    -   `stretch` : 아이템을 늘려 간격 없이 배치

### 플렉스 아이템 속성

-   `align-self` : 플렉스 아이템을 따로 원하는 형태로 배치할 때 쓰임. -> 혼자 따로

    -   속성은 align-items와 같음

-   `flex` : 플렉스 아이템의 너비를 늘이거나 줄일 수 있도록 세 가지 값으로 표시
    -   `flex-grow`
    -   `flex-shrink`
    -   `flex-basis` : 기본 크기
        -   `auto`
        -   `initial` : 기본값

```css
flex: 2; // 값이 하나, 단위가 없다면 flex-grow
flex: 30px; // 값이 하나, 단위가 있다면 flex-basis
flex: 1 40px; // 값이 두 개, 단위가 없는 건 grow, 있는 건 basis
flex: 1 1; // 값이 두개, 둘다 단위가 없다면 flex-grow, flex-shrink
flex: 2 2 0; // 값이 세 개면 순서대로 grow shrink basis
```

## CSS 그리드 레이아웃 모듈

### 플렉스 박스 레이아웃과 CSS 그리드 레이아웃의 차이점

플렉스 박스 레이아웃에서는 아이템을 배치할 때 가로나 세로 중 하나를 주축으로 정해놓고 배치 = 1차원 <br>
그리드 레이아웃에서는 배치할 때 가로와 세로를 모두 사용 = 2차원

### 그리드 레이아웃 만들기

플렉스 박스처럼 컨테이너를 만들고, 그 안에 아이템을 배치

#### display

```css
.wrapper {
    // 컨테이너의 클래스명
    display: grid; // 또는 inline-grid
}
```

#### grid-template-columns

```css
grid-template-columns: 200px 200px 200px; // 칼럼의 너비를 200px씩, 3개씩 배치
```

#### grid-template-rows

```css
grid-template-rows: 100px 200px; // 첫 번째 줄과 두 번째 줄의 높이를 지정
```

가끔 지정한 높이 보다 내용이 많을 경우에는 내용이 밖으로 넘쳐버림

```css
grid-template-columns: minmax(100px auto);
```

이런 식으로 최소는 `100px`, 최대는 `auto` 로 설정

#### fr 단위

px을 사용하면 항상 크기가 고정되기 때문에 반응형에 적합하지 않음
그래서 상대적인 크기를 지정하는 `fr` 단위를 사용

```css
grid-template-columns: 1fr 1fr 1fr; // 같은 비율로 3칸 표시
grid-template-columns: 2fr 1fr 2fr; // 2:1:2의 비율로 3칸 표시

grid-template-columns: repeat(3, 1fr); // 3개 반복
```

#### grid-column-gap, grid-row-gap, grid-gap

-   grid-column-gap: 칼럼 사이 간격
-   grid-row-gap: 줄 사이의 간격
-   grid-gap: 칼럼과 줄 둘 다

```css
grid-column-gap: 30px;
grid-row-gap: 20px;
grid-gap: 20px 30px;
```

이 외에도 플렉스 박스의 align-content나 justify-content 같은 속성 사용 가능

### 그리드 라인을 사용해 배치하기

그리드 레이아웃에는 눈에 보이지 않는 **그리드 라인**이 존재

[예시](https://github.com/CaesiumY/frontend-web-design-forBeginners/blob/master/09/css-grid/grid-4.html)

```css
grid-column: 1/4; // 칼럼 1번부터 4번까지
grid-row: 2/4; // 줄 2번부터 4번까지
grid-column-start: 3; // 칼럼 3번부터 시작
grid-row-start: 2; // 줄 2번부터 시작
```
