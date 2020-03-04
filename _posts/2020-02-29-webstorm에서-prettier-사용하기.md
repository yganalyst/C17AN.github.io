---
title:  "[정보] - WebStorm 에서 Prettier 사용하기"
search: true
classes: wide
tag:
  - tool
  - tip
categories:
  - Info
excerpt: "WebStorm에서 간단하게 Prettier 사용하기"
last_modified_at: 2020-02-29T08:06:00-05:00
---
WebStorm 에서는 기본적으로 [Shift + Alt + L] 키를 사용한 코드 정리 기능을 지원한다. 그러나 매번 저 숏컷을 입력하는 것도 번거로워 새로운 방법을 찾아본 결과, `prettier` 플러그인을 이용해 파일을 저장할 때마다 자동으로 코드 정리를 실행하는 방법을 찾을 수 있었다. 😎

## 1. Node.js, prettier 설치   
[`prettier`](https://prettier.io/) 는 WebStorm 뿐만 아니라 VS Code 나 Sublime Text 등 다양한 에디터에서 코드 정리를 수행하는데,  설치를 위해서는 우선 최신 버전의 [`Node.js` (다운로드 링크)](https://nodejs.org/en/) 가 필요하다.   


{% include figure image_path="/assets/images/2020-02-29-webstorm-prettier/nodejs.PNG" alt="Node.js 메인화면" caption="2020년 2월 29일 기준 화면" %}

보통 LTS(Long Term Support)는 안정화 버전, 그 옆은 최신 기능을 탑재한 버전인데 LTS 버전을 설치하는 것을 권장한다.   

`Node.js` 의 설치가 끝나면 CMD 창을 열고 `npm install --global prettier` 명령어를 입력해 `prettier` 를 설치한다.  

[WebStorm plugin Marketplace](https://plugins.jetbrains.com/plugin/10456-prettier) 에서 `prettier` 를 설치할 수도 있지만, 후에 설명할 `File Watcher` 와의 원활한 연동을 위해 Node.js 를 사용하는 것을 권장한다.

## 2. WebStorm 에서 prettier 설정하기
설치가 끝난 후, WebStorm 으로 돌아와 [File] - [Settings] 혹은 [Ctrl + Alt + S] 숏컷을 사용해 Settings 메뉴에 진입하면 이런 화면이 보일 것이다.   

<img src = "/assets/images/2020-02-29-webstorm-prettier/setting_1.PNG"/>    


여기서 [Languages & Frameworks] 탭에 들어간 후, JavaScript 메뉴에 들어간다.


<img src = "/assets/images/2020-02-29-webstorm-prettier/setting_2.PNG"/>   


화면이 이렇게 변하면 좌측 메뉴들 중에서 [Prettier] 에 들어간 후, Node Interpreter 는 설치한 node.exe 로 설정하고 Prettier Package 를 그림과 같이 설정한다.   


<img src = "/assets/images/2020-02-29-webstorm-prettier/setting_3.PNG"/>    


여기까지 마쳤다면 이제 [Ctrl + Shift + Alt + P] 숏컷을 사용해 화면 전체의 코드를 정돈할 수 있다.   

<img src = "/assets/images/2020-02-29-webstorm-prettier/prettier1.gif"/>  

## 3. File Watcher 를 사용해 저장 시 자동으로 코드 정리하기

숏컷 하나만으로 파일 코드 전체를 정리하는 것은 분명 좋은 기능이지만, 숏컷을 외우는 건 분명 어려운 일이다.   


`File Watcher` 플러그인을 사용해 코드를 저장할 때 자동으로 `prettier` 가 실행되도록 해보자.


[`File Watcher`(다운로드 링크)](https://plugins.jetbrains.com/plugin/7177-file-watchers) 를 해당 링크에서 설치한 다음, [File] - [Settings] 혹은 [Ctrl + Alt + S] 숏컷을 사용해 Settings 메뉴에 진입한다.   

<img src = "/assets/images/2020-02-29-webstorm-prettier/setting_4.PNG"/>  

설정에 진입한 후, [Tools] 탭에 들어가보면 [File Watchers] 라는 메뉴가 새로 생겨있을 것이다.    

<img src = "/assets/images/2020-02-29-webstorm-prettier/setting_5.PNG"/>

해당 메뉴를 클릭하면 위와 같은 화면이 나타날 텐데 우측 상단의 [+] 기호를 눌러 나타나는 항목들 중 `Prettier` 를 선택한다.   

<img src = "/assets/images/2020-02-29-webstorm-prettier/setting_6.PNG"/>   


`Prettier` 를 선택했을 때 나타는 화면 모습이다.   
여기서 Program 의 경로를 `prettier` 가 설치된 디렉토리로 바꿔줘야 하는데, npm을 통해 설치를 진행했으니 npm 설치 경로를 확인한다.  

- npm 설치 경로 확인방법
  - CMD 진입 - `npm prefix --g` 입력
{: .notice--success}

<img src = "/assets/images/2020-02-29-webstorm-prettier/setting_7.PNG"/>

설치 경로를 복사한 후, 다시 WebStorm 으로 돌아가 경로를 수정한다.

<img src = "/assets/images/2020-02-29-webstorm-prettier/setting_8.PNG"/>

Program 의 경로 설정이 끝났다면 [Enabled] 체크박스에 체크한 후 적용한다.

<img src = "/assets/images/2020-02-29-webstorm-prettier/setting_9.PNG"/>

## 4. 설정 끝 & 유의사항  
<img src = "/assets/images/2020-02-29-webstorm-prettier/prettier2.gif"/>  


위의 코드 정리는 [Ctrl + Shift + Alt + P] 숏컷을 통해 prettier 를 호출한 것이 아니라, [Ctrl + S] 단축키로 코드를 저장하면서 동시에 이루어진 모습이다.


이제 더이상 [Shift + Alt + L] 이나 [Ctrl + Shift + Alt + P] 같은 어려운 단축키를 외워야 할 일은 없겠지만, 이 방법의 한 가지 단점은 매 프로젝트마다 `File Watcher` 의 설정을 다시 해주어야 한다는 점이다. 😭


- 막히는 부분이 있거나 글과는 다른 화면이 나타나 설치에 지장이 있을 경우, 댓글을 통해 알려주시면 해결해드릴 수 있도록 하겠습니다. 😄
