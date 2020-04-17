---
title:  "[React] - React Native 를 이용해 앱 빌드하기"
search: true
toc : true
toc_label : 네비게이션
header:
  teaser: "/assets/images/header/react_native.png"
toc_sticky : true
tag:
  - app
  - react-native
  - react
categories:
  - React-Native
excerpt: "React Native 를 사용해 첫 번째 앱 빌드하기"
last_modified_at: 2020-04-17T08:06:00-05:00
---

리액트의 가장 큰 장점 중 하나는 바로 유사한 문법의 리액트 네이티브를 사용해 앱을 만들 수 있다는 건데, 한번 리액트 네이티브를 통해 앱을 빌드해보자. 😄   

---

## 1. 🧪 앱을 만들기에 앞서   

먼저 준비물로는 npm을 사용하기 위한 node.js와 **AVD**(Android Vertual Device) 설정을 위한 [**안드로이드 스튜디오**](https://developer.android.com/studio)가 필요하다.  

안드로이드 스튜디오를 설치할 때, 설치 마법사에서 **install Virtual Device** 라는 설정이 있을 텐데 반드시 설정해주자.   

---

<img src = "/assets/images/2020-04-17-react-native로 앱 만들기/install.PNG"/>

---

안드로이스 스튜디오를 설치했다면 이제 에뮬레이터를 어느 환경에서든 사용하기 위해 시스템 환경 변수에 SDK 정보를 추가할 것이다.   

우선 안드로이드 스튜디오 상단의 **[File] - [Settings]** 메뉴에 들어간 후, **[Appearance & Behavior] - [System Settings] - [Android SDK]** 에 진입한다.   

그러면 수많은 안드로이드 SDK 목록과 SDK를 위한 개발 도구들의 목록이 나타날 텐데, 이들 중 사진에 체크된 5가지 항목을 체크해 설치해주자.   

---

* **Android SDK Build-Tools 30-rc2**
* **Android Emulator**
* **Android SDK Platform-Tools**
* **Android SDK Tools**
* **Intel x86 Emulator Accelerator (HAXM installer)**

---

<img src = "/assets/images/2020-04-17-react-native로 앱 만들기/settings.PNG"/>

---

설치가 끝났다면 상단에서 **[Tools] - [AVD Manager]** 를 선택한 후 **[Create Virtual Device]** 를 눌러 원하는 가상 기기를 생성한다.   

---

<img src = "/assets/images/2020-04-17-react-native로 앱 만들기/AVD.PNG"/>

---

사진은 9.0버전의 OS를 탑재한 픽셀 3을 가상으로 생성한 모습인데, 이 과정이 어려우면 [**안드로이드 공식 문서**](https://developer.android.com/studio/run/managing-avds?utm_source=android-studio) 를 참조하는 것도 좋다.

<img src = "/assets/images/2020-04-17-react-native로 앱 만들기/device.PNG"/>

---

마지막으로, Windows 검색창에 "환경 변수" 라고 검색하면 아래와 같이 **[시스템 환경 변수 편집]** 이라는 메뉴가 보일 것이다.

---

<img src = "/assets/images/2020-04-17-react-native로 앱 만들기/환경 변수.PNG"/>

---

그 후, **[고급] - [환경 변수]** 메뉴에 들어가 다음과 같은 내용을 사용자 변수에 추가해준다.   

- **변수 이름 : ANDROID_HOME**
- **변수 값 : SDK 설치 경로 (C:\Users\계정명\AppData\Local\Android\Sdk)**



여기까지 마쳤다면 에뮬레이터 설정은 모두 끝났다.   
이제 리액트 네이티브 환경을 만들어 보자.

---

## 2. 🍔 리액트 네이티브 맛보기   

우선 리액트 프로젝트를 생성할 때와 마찬가지로 리액트 네이티브 역시 npm을 사용해 프로젝트를 초기화한다.   

터미널에 ```npx create-react-app init "프로젝트명"``` 을 입력하면 프로젝트 이름으로 된 폴더가 생성되고 그 안에 리액트 네이티브 프로젝트가 초기화된다.   

이후 ```npx react-native run-android``` 명령을 터미널에 입력하면 첫 번째 리액트 네이티브 프로젝트가 에뮬레이터 위에서 실행된다.    

---

**- 첫 번째 React-Native 프로젝트 모습**
{: .notice--info}

<img src = "/assets/images/2020-04-17-react-native로 앱 만들기/run-native.PNG"/>

---

