---
title:  "[정보] - VS Code에서 파이썬 사용하기"
search: true
toc : true
toc_label : 네비게이션
header:
  teaser: "/assets/images/header/python.png"
toc_sticky : true
tag:
  - tip
  - python
  - extension
categories:
  - Info
excerpt: "VS Code에서 파이썬을 사용하는 방법 소개"
last_modified_at: 2020-04-10T17:06:00-05:00
---

이번 학기에는 파이썬을 이용한 수업이 둘이나 있다. 😂😂  

학교에서 **Anaconda** 를 사용하는 방법을 배웠지만, 나는 개발 환경이 변하는걸 원하지 않아 VS Code에서 파이썬 코드를 작성 - 실행까지 하는 방법을 새로 찾아보게 되었다. 😄

---

## 1. 🌻 VS Code 에서 파이썬 코드 실행하기

가장 기본적으로 파이썬이 깔려 있어야 한다.   
파이썬이 깔려있지 않다면, 먼저 [**파이썬 다운로드 링크**](https://www.python.org/downloads/) 에서 파일을 다운받자.   

**- 다운로드 링크의 모습**
{: .notice--info}

---

<img src = "/assets/images/2020-04-10-python-on-vsc/homepage.PNG">

---

다음으로, 설치한 파이썬을 VS Code 상에서 사용하기 위해 파이썬 익스텐션을 설치한다.   
익스텐션 스토어 기본 단축키는 **[Shift + Ctrl + X]** 키로, 어렵지 않게 스토어를 열 수 있을 것이다.

**- 익스텐션 스토어에서 "python" 을 검색 후 설치해주자.**
{: .notice--info}

---

<img src = "/assets/images/2020-04-10-python-on-vsc/python.PNG">

---

python **익스텐션**을 설치했다면, VS Code 상에서 파이썬을 실행할 인터프리터를 설정할 수 있다.   
**[Shift + Ctrl + P]** 키로 커맨드 목록을 띄운 뒤, **"Python : Select Interpreter"** 를 선택하자.

---

<img src = "/assets/images/2020-04-10-python-on-vsc/select.PNG">

---

해당 명령을 수행하면, 로컬 환경에 설치되어 있는 **python** 들이 전부 출력된다.  
(이렇게 많은 파이썬이 깔려 있는지 몰랐다 ^^; 다 지워야지...)   

**- 리스트 중 원하는 버전의 파이썬을 인터프리터로 지정해주자.**
{: .notice--info}

---

<img src = "/assets/images/2020-04-10-python-on-vsc/list.PNG">

---

인터프리터 지정까지 끝나면 이제 파이썬을 실행할 준비가 모두 끝났다.   
우측 상단에 새로 생긴 초록색 화살표를 클릭하면, 파이썬 코드의 실행 결과가 터미널에 출력된다.

---

<img src = "/assets/images/2020-04-10-python-on-vsc/arrow.PNG">

---

**- 하단 터미널 콘솔창에 파이썬 실행 결과가 출력된 모습**
{: .notice--info}

<img src = "/assets/images/2020-04-10-python-on-vsc/result.PNG">

---

## 2. 🌼 VS Code 에서 파이썬 모듈 사용하기   

VS Code에서는 파이썬 코드를 실행할 수 있을 뿐만 아니라, 각종 모듈 역시 파이썬 환경과 동일하게 설치 및 사용할 수 있다.   

터미널에 `pip install numpy` 라고 입력해 `numpy` 모듈을 설치해보자.   
설치가 끝나면, `Python/Python(버전)/Lib/site-packages` 디렉토리에 모듈이 설치된 것을 확인할 수 있다.   

---

<img src = "/assets/images/2020-04-10-python-on-vsc/numpy.PNG">

---

<img src = "/assets/images/2020-04-10-python-on-vsc/install.PNG">

---

이제 설치한 모듈을 import 하면 numpy 모듈에 속해있는 함수들을 모두 사용할 수 있다.   

**- numpy.linalg 라는 선형대수 모듈을 사용하는 모습**
{: .notice--info}

---

<img src = "/assets/images/2020-04-10-python-on-vsc/run.PNG">

---

+ 이렇게 외부 모듈에 속한 함수 역시 자동완성과 설명을 지원하니, 많은 도움이 될 것이다.   

---

<img src = "/assets/images/2020-04-10-python-on-vsc/desc.PNG">

---

이외에도 순정 파이썬에서 할 수 있는 건 모두 가능하니, 파이썬을 위한 에디터를 별도로 설치하기 싫다면 **VS Code** 에서 파이썬을 즐겨보자.   
분명 크게 만족할 것이다. 😍
