---
title:  "[정보] - Live Server 사용하기"
search: true
toc : true
toc_label : 네비게이션
header:
  teaser: "/assets/images/header/software.png"
toc_sticky : true
tag:
  - tip
  - tool
  - extension
categories:
  - Info
excerpt: "VS code의 Live Server 익스텐션 소개"
last_modified_at: 2020-04-08T17:06:00-05:00
---

**HTML** 문서를 만들면서 수정한 결과를 확인하려면 저장한 후 브라우저에서 새로고침을 해야만 한다.   

이게 약간 번거롭다고 느껴 좋은 방법이 없을까 찾아봤는데, 나같은 사람이 또 있었나보다. 🤣   

---

## 1. 🔨 Live Server 익스텐션   

<img src = "/assets/images/2020-04-10-live-server/intro.PNG">

---

[**Live Server**](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) 는 VS Code에서 제공되는 익스텐션(확장 프로그램)으로, HTML과 CSS의 수정사항을 새로고침 없이 실시간으로 확인할 수 있는 강력한 도구다.

사용 방법도 매우 간단하다.   
VS Code 에서 [Ctrl + Shift + C] 키로 익스텐션 마켓플레이스에 진입한 다음, `Live Server` 라고 검색했을 때 나오는 파일을 설치하면 된다.

설치가 끝나면 써먹고자 하는 HTML 파일에 들어가 보자.

---

<img src = "/assets/images/2020-04-10-live-server/sample.PNG">

---

화면으로 돌아오면, 여기서 터미널을 띄울 필요도 없이 그냥 화면에서 마우스를 우클릭해주자.   
그럼 못보던 **"Open with Live Server"** 라는 선택창이 추가된 모습을 확인할 수 있다.

---

<img src = "/assets/images/2020-04-10-live-server/menu.PNG">

---

이제 이를 클릭하면 내 컴퓨터를 의미하는 루프백 주소인 `127.0.0.1` 의 5500번 포트로 연결되며, 내가 만든 HTML 문서가 여기 출력되게 된다.

---

<img src = "/assets/images/2020-04-10-live-server/screen.PNG">

---

물론 출력만 하면 이걸 설치한 보람이 없을 테니, 한번 HTML 문서를 내 입맛대로 수정해 보자.

그러면 더이상 번거로운 새로고침 없이 자동으로 HTML과 CSS의 변경사항이 적용된 화면이 나타나는 모습을 볼 수 있을 것이다. 😄

---

**- Live Server 를 사용한 실시간 변동사항 적용 모습**
{: .notice--info}

<img src = "/assets/images/2020-04-10-live-server/live.gif">

---

**VS code** 에는 이처럼 생산성 향상을 위한 도구가 엄청나게 많다.   
코드를 짤때 뭔가 번거롭거나 귀찮은 일이 있다면, 일단 한번 검색을 해보자.   

나처럼 귀찮은 걸 싫어하는 사람이 만든 멋진 도구가 이미 올라와 있을 수도 있을 테니 말이다! 😆
