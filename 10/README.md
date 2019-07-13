# [10. 풀 스크린 배경](https://github.com/CaesiumY/frontend-web-design-forBeginners/tree/master/10)

## [10-1] 풀 스크린 배경 이미지 만들기

### 이미지 파일 최적화하기

#### JPEG 파일일 경우

[jpegmini 링크](https://www.jpegmini.com/)

> 근데 더 이상 안 되는 듯...

#### PNG 파일일 경우

[TinyPNG 링크](https://tinypng.com/)

### CSS3를 사용해 풀 스크린 배경 만들기

```
html {
    background: url('이미지 경로') no-repeat center center fixed;
    background-size: cover;
}
```

### 기존 CSS를 사용해 풀 스크린 배경 만들기

```
<style>
    .bg {
        min-height: 100%;
        min-width: 100%;
        width: 100%;
        height: auto;
        position: fixed;
        top: 0;
        left: 0;
    }
    @media screen and (max-width:1024px) {
        .bg {
            left: 50%;
            margin-left: -512px;
        }
    }    
</style>

<img src='이미지 경로' class="bg">
```

### jQuery 플러그인을 사용해 풀 스크린 배경 만들기

#### Backstretch.js 플러그인

[다운 링크](https://www.jquery-backstretch.com/)

```
$(function() {
    $.backstretch("이미지 파일");
});
```
```
$(function() {
    $.backstretch(["이미지1", "이미지2", ...], {duration: 시간, fade: 시간});
});
```

#### Vegas 플러그인

[Vegas 링크](https://vegas.jaysalvat.com/)

```
<script>
    $(function() {
        $('body').vegas({
            slides:[
                {src:'이미지 파일 1'},
                {src:'이미지 파일 2'},
                {src:'이미지 파일 3',
                    video:{
                        src:['비디오 파일'],
                        loop: false,
                        mute: true
                    }
                },
            ],
            delay: 3500
        });
    });
</script>
```