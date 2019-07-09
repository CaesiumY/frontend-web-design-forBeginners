# [9. 그리드 레이아웃](https://github.com/CaesiumY/frontend-web-design-forBeginners/tree/master/09)

## [09-1] 다단 칼럼을 사용해 그리드 레이아웃 만들기

### 다단 칼럼으로 레이아웃 만들기

```
<style>
    #columns {
        column-count: 2;    // 칼럼 개수 2개
        column-gap: 10px;   // 칼럼 사이 간격 10px
    }

    @media(min-width:1100px) {  // 화면 너비가 1100이상일 때
        #columns {
            column-count: 4;    // 칼럼 개수 2개
        }
    }
</style>
```

