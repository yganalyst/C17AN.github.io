---
title:  "[React] - React Native 기초 - 1편"
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
  - App
excerpt: "React Native 기초 정보 - 1편"
last_modified_at: 2020-04-19T08:06:00-05:00
---

리액트 네이티브가 리액트와 유사한 문법을 가지고 있다고는 하지만, 100% 모든 점이 리액트와 호환되는 것은 아니다. 😔  

오늘은 리액트 네이티브만의 특징 몇 가지와 리액트 네이티브를 사용할 때 유의할 점 몇 가지를 정리해본다.   

---

## 1. ⚽ 기본 컴포넌트

리액트 네이티브는 어플리케이션 개발을 목적으로 하는 만큼, 웹에서 사용되는 `<div>`, `<li>` 등의 태그는 호환되지 않는다.   

대신 이에 대응하는 기본 컴포넌트들을 제공하는데, [**리액트 네이티브 공식 문서**](https://reactnative.dev/docs/components-and-apis) 를 참조해 목적에 맞는 컴포넌트를 사용하면 될 것이다.   

---

```javascript
import React from 'react';
import {Text, View} from 'react-native';
const App = () => {
  return (
    <View>
      <Text>Hello, React Native!</Text>
    </View>
  );
};
```

---

또, 기본 컴포넌트를 사용하기 위해서도 `react-native` 모듈에 있는 컴포넌트를 꺼내 사용해야 하니 이를 잊지 않도록 하자.

---

## 2. 🎨 StyleSheet

처음 디자인을 꾸밀 때 당황했던 부분으로, 리액트 네이티브는 CSS가 아닌 CSS를 적당히 구현한 자체적인 **StyleSheet** 컴포넌트를 제공한다.

그런데 태그명이 CSS와는 다른 부분이 일부 있다.   
예를 들면 **justify-content** 처럼 `-` 기호가 들어가는 태그를 모두 **카멜 표기법** 으로 바꾸어 **justifyContent** 와 같이 사용한다.   

태그명뿐만 아니라 **flex-direction** 의 기본 설정 역시 다른데, 웹에서는 디폴트 옵션으로 **flex-direction** 이 가로 방향인 'row' 를 가리켰지만 리액트 네이티브에서는 flexDirection 옵션이 기본적으로 세로 방향인 'Column' 을 가리킨다.

---

**- 리액트 네이티브는 기본적으로 위에서 아래로 향하는 flex-direction 을 가진다**
{: .notice--info}

---

<img src = "/assets/images/2020-04-19-react-native-기초-정리-1/column.PNG" width = "300">

---

## 3. 🔊 키보드 제어   

이것도 처음에 엄청 당황했던 부분인데, TextInput 을 받는 과정에서 키보드를 띄우면 키보드의 높이만큼 뷰가 위로 밀리는 경험을 해본 사람들도 있을 것이다.   

---

**👆 키보드가 올라오면 로그인 폼도 함께 올라가는 모습**
{: .notice--info}

<img src = "/assets/images/2020-04-19-react-native-기초-정리-1/resize.gif" width = "500">

---

이 부분은 프로젝트 폴더의 **[android] - [src]** 경로에 있는 `AndroidManifest.xml` 파일을 수정해 해결할 수 있었는데, 위 사진과 동일한 증상을 겪는다면 `AndroidManifest.xml` 의 항목 중 `android:windowSoftInputMode` 속성의 값이 **"adjustResize"** 로 설정되어 있었을 것이다.   

---

<img src = "/assets/images/2020-04-19-react-native-기초-정리-1/manifest.PNG">

---

여기서 **"adjustResize"** 값을 **"adjustNothing"** 으로 변경하면 키보드가 나타나도 뷰의 형상에는 영향을 미치지 않는 원하던 결과를 얻을 수 있다.

---

**✌ 키보드가 올라와도 뷰의 형상이 유지되는 모습**
{: .notice--info}

<img src = "/assets/images/2020-04-19-react-native-기초-정리-1/nothing.gif" width = "500">

---
