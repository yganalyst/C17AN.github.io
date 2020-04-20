---
title:  "[블로그] - minimal-mistakes 테마 팁 소개"
search: true
toc : true
toc_label : 네비게이션
toc_sticky : true
tag:
  - 블로그
  - tip
categories:
  - Info
excerpt: "몸으로 겪은 minimal-mistakes 팁 소개"
last_modified_at: 2020-02-27T08:06:00-05:00
---

우선 이 블로그는 Jekyll 테마 중에서 [minimal-mistakes](https://github.com/mmistakes/minimal-mistakes) 테마를 이용해 만들어졌다.  


minimal-mistakes 테마는 현재 제공되는 `Jekyll` 블로그 테마 중에서 가장 이용자 수가 많고, [문서](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)도 굉장히 체계적으로 제공되어 커스텀이 용이하다는 장점이 있다.  

근 한달동안 이루어진 삽질 끝에 얻은 지식 몇가지를 소개해보려 한다. 😄


## 1. 포스팅 설명 추가하기 : excerpt 설정 추가
excerpt 를 사전에 검색해보면 "발췌" 라는 아리송한 뜻만 나오는데, jekyll 에서는 글의 간략한 설명을 의미한다.  
`excerpt` 태그를 본문에 설정하면 포스팅 목록에서 내가 설정한 간략한 설명을 볼 수 있다.  


<img src="/assets/images/2020-02-26-blog/excerpt.PNG">

위는 기본값 설정으로 본문 설명이 나타나지 않는 모습이고, 아래는 excerpt 를 설정함으로써 포스팅에 대한 간략한 설명을 추가한 모습이다.  


만약 "excerpt" 설정을 추가하고 싶다면, 본문 최상단에 있는 문서 정보에 다음과 같이 `excerpt:` 옵션을 추가해주면 된다.

```
---
title:  "[Blog] - minimal-mistakes 커스텀 팁"
excerpt: "블로그 제작기, 여러 팁"
categories:
  - Blog
last_modified_at: 2020-02-27T08:06:00-05:00
---
```


## 2. 백틱(``) 을 이용한 인라인 코드 하이라이팅 ✨
`Jekyll` 은 마크다운 문법으로 코드 하이라이팅을 지원하는데, 한 줄에 대해서는 기본적으로 하이라이팅이 지원되지 않는다. 😅  

### - 하이라이팅 전
{: .notice--info}

<img src="/assets/images/2020-02-26-blog/하이라이팅 전.png">


### - 하이라이팅 후
{: .notice--info}

<img src="/assets/images/2020-02-26-blog/하이라이팅 후.png">

이 설정과 관련된 정보는 구글링을 아무리 해봐도 없어서 꽤나 애를 먹었는데, 결국 `_sass` 폴더를 열심히 뒤지다가 찾는데 성공했다.  

**- 🚨 해당 설명은 minimal-mistakes 테마를 기준으로 함! 🚨**
{: .notice--danger}

1. **최상위 폴더에서 [_sass] 폴더 진입**
<img src="/assets/images/2020-02-26-blog/sass.PNG">

2. **[minimal-mistakes] 폴더 진입**
<img src="/assets/images/2020-02-26-blog/minimal-mistakes.PNG">

3. **[_base.scss] 파일 열기**
<img src="/assets/images/2020-02-26-blog/base.png">

4. **[td > code] 찾기**  
<img src="/assets/images/2020-02-26-blog/하이라이팅.PNG">

처음 저 부분을 보면 `color` CSS 속성이 없을 것이다.   

`color` : 글씨색 / `background` : 배경색

`color` CSS 속성을 직접 추가한 후, 구글 ["color picker"](https://www.google.com/search?q=color+picker) 등에서 원하는 색을 찾아 그에 해당하는 RGB값의 HEX 값을 넣으면 된다.  

## 3. 🚦 `notice` 추가하기 🚦

`notice` 는 특별한 기능은 없지만, 나는 그냥 글이 밋밋할 때 사용한다.  

이러면 빨간색
{: .notice--danger}

```
이러면 빨간색
{: .notice--danger}
```

이러면 노란색
{: .notice--warning}

```
이러면 노란색
{: .notice--warning}
```

이러면 초록색
{: .notice--success}

```
이러면 초록색
{: .notice--success}
```

이러면 파란색
{: .notice--info}

```
이러면 파란색
{: .notice--info}
```

`notice` 안에는 li, strong 등 효과도 적용이 가능하다.  

**이러면 굵은 파란색**
{: .notice--info}

```
**이러면 굵은 파란색**
{: .notice--info}
```

한 가지 팁을 적자면, `notice` 를 사용할 때는 마크다운에 작성할 때 위아래로 한 칸씩 개행을 해주는게 좋다.   

가끔씩 원하지 않았던 게 `notice` 속성에 들어가버려 커밋을 다시 하게되면 괜히 귀찮다.  

## 4. TOC (Table Of Content)
TOC는 본문의 \<h1>, \<li> 등 제목과 요소 태그를 인식해 자동으로 간단한 페이지 리모콘을 만들어주는 기능이다.  

특별한 설정은 필요하지 않으며 `excerpt` 설정을 했던 것처럼 본문 최상단 포스트 정보에 `toc` 와 관련된 설정을 추가해주면 된다.  

- toc : toc 설정 여부 (true / false)
- toc_label : toc 제목이 될 내용 (큰따옴표 X)
- toc_sticky : toc가 스크롤을 따라올지 여부 (true / false)

**TOC 설정 예시**
{: .notice--success}

```
---
title:  "[Blog] - minimal-mistakes 커스텀 팁"
toc : true
toc_label : 네비게이션
toc_sticky : true
excerpt: "minimal mistakes 일부 팁"
last_modified_at: 2020-02-27T08:06:00-05:00
---
```

<img src="/assets/images/2020-02-26-blog/네비게이션.PNG">


그리고 블로그를 만들 때 정말 많이 참조했던 블로그들인데, 포스팅 내용 외의 큼지막한 설정들은 대부분 이 두 분이 이미 작성해주셨다.   

- ***Imreplay*** 님 블로그   
  [https://imreplay.com](https://imreplay.com/categories/blogging)   


- ***취미로 코딩하는 개발자***  님 블로그   
[https://devinlife.com/](https://devinlife.com/categories/)


- minimal-mistakes 공식 스타트 가이드   
[minimal-mistakes start-guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)

 + 추가로 궁금한 설정이 있다면, 댓글로 남겨 주시면 감사드립니다~!
