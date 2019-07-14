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

## [10-2] 풀 스크린 배경 동영상 직접 만들기

### 사전 준비

#### 서버의 MIME 유형 설정
서버의 .htaccess 파일에서 지정
```
AddType video/webm .webm
AddType video/mp4 .mp4
AddType video/ogg .ogv
```

~~무슨 소리인지 모르겠;;~~

#### html5shiv 파일 포함

익스플로러 8 이하 버전에서는 html5 버전 인식 불가 <br>
-> 최소한 [html5shiv.js 파일을 링크](https://github.com/aFarkas/html5shiv)

```
<!--[if it IE 9]>
<script src="html5shiv.min.js"></script>
<![endif]-->
```

### jQuery 플러그인을 사용해 풀 스크린 배경 만들기

#### Vide.js 플러그인

[홈페이지 링크](http://vodkabears.github.io/vide/)

```
//문서 전체의 경우
<body data-vide-bg="비디오 링크, poster: 포스터 이미지 링크" data-vide-options="loop: true, muted: true">

// 일부 요소의 경우
$("요소").vide("비디오 링크", { 옵션들 });
```

### 유튜브 동영상으로 풀 스크린 배경 만들기 - tubular 플러그인

[다운 링크](https://code.google.com/archive/p/jquery-tubular/)

```
<script>
    $('document').ready(function() {
        var options={
            videoId: '유튜브 비디오 아이디',
            start:8
        };

        $('요소').tubular(options);
    })

</script>
```