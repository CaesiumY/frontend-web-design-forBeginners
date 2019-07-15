# [11. 캐러셀](https://github.com/CaesiumY/frontend-web-design-forBeginners/tree/master/11)

## [11-1 캐러셀이란?]

### 여러 형태의 캐러셀

> 캐러셀 : 몇 가지 내용을 하나씩 회전하면서 보여주고, 마지막 내용 다음에는 다시 첫 번째 내용으로 연결해서 보여주는 것을 뜻함.

## [11-2 bxslider 플러그인]

[bxslider 공식 사이트](https://bxslider.com/)

```
<script>
    $(function() {
        $('요소명').bxSlider({
            slideWidth: 600,    // 화면 너비 설정
            captions: true      // img 태그의 title 속성을 캡션으로 추가
        });
    });
</script>
```