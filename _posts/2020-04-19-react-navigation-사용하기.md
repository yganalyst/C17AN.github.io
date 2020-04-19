---
title:  "[React] - React Navigation 사용하기"
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
excerpt: "React Navigation 으로 라우팅 구현하기"
last_modified_at: 2020-04-19T08:06:00-05:00
---

웹 페이지를 만들 때 다른 웹페이지를 보여주기 위해서는 `<a href = "Login.html" />` 처럼 링크를 사용할 수 있었다. 😄  

하지만 앱에서는 저런 방식의 페이지 전환이 불가능하므로 다른 화면(컴포넌트) 를 탐색할 때 [**React Navigation**](https://reactnavigation.org/) 을 사용할 수 있다.   

---

**- 🧳 네비게이션을 사용하면 다른 화면들을 넘나들 수 있다.**
{: .notice--danger}

<img src = "/assets/images/2020-04-19-react-navigation-사용하기/screens.PNG" />

---

한가지 유의할 점이라면 [**React Native Navigation**](https://wix.github.io/react-native-navigation/docs/before-you-start/) 과 [**React Navigation**](https://reactnavigation.org/)은 완전히 다른 라이브러리로, **React Native Navigation** 은 설치 및 초기 적용이 꽤나 복잡하여 **React Navigation** 의 손을 들어주게 되었다.   

---

## 1. 💻 React Navigation 설치

React Navigation은 **npm**을 사용해 간단하게 설치할 수 있다.

---

```
npm install @react-navigation/native
```

---

그 후, 라이브러리 의존성 파일들을 아래 명령어로 설치해 준다.   

```
npm install react-native-reanimated react-native-gesture-handler react-native-screens react-native-safe-area-context @react-native-community/masked-view
```

---

설치한 의존성 파일들 중 **react-native-gesture-handler** 는 화면 스와이핑, 드래깅 등 다양한 손동작을 처리하기 위한 파일인데, 이를 사용하기 위해서 엔트리 파일 (루트 파일, Ex. App.js / Index.js) 가장 위에 **import 'react-native-gesture-handler';** 구문을 추가해 준다.

**- 🚨 만약 이 작업이 생략되면 앱이 빌드되지 않을 수 있음!**
{: .notice--danger}

여기까지 따라왔다면 초기 설정은 모두 끝이다.   

혹시 생략된 부분이 있을 수 있으니 더 자세한 내용은 [**Get Started**](https://reactnavigation.org/docs/getting-started) 를 참조해도 좋다.

---

## 2. 🌌 네비게이션 설정   

네비게이션 설정은 웹에서 페이지 라우팅을 하는 과정과 아주 비슷하다.   
우선 가장 기본적인 **stack** 형 네비게이션을 적용해 보았는데, 한번 네비게이션을 통해 메인화면과 로그인 화면, 회원가입 화면을 넘나들어 보자.

우선 stack 형 네비게이션을 사용하기 위해 npm을 사용해 네비게이션을 설치한다.

---

```
npm install @react-navigation/stack
```

---

그 후, 네비게이션 설정을 위해 엔트리 파일의 **모든 컴포넌트**를 `<NavigationContainer>` 라는 컨테이너로 감싼다.

---

**- App.js**
{: .notice--info}

```javascript
import * as React from 'react';
import {NavigationContainer} from '@react-navigation/native';
import {createStackNavigator} from '@react-navigation/stack';
import 'react-native-gesture-handler';
import MainPage from './mainPage/MainPage';

const Stack = createStackNavigator();

const App = () => {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="Main" component={MainPage} />
      </Stack.Navigator>
    </NavigationContainer>
  );
};

export default App;
```

---

우리가 알고있는 View 나 Text 같은 기본 컴포넌트가 아니라 당황할 수도 있다.    
이 코드를 찬찬히 살펴보면 다음과 같은 의미를 갖는다.   

---

```javascript
<NavigationContainer>
    <Stack.Navigator>
        <Stack.Screen name="Main" component={MainPage} />
    </Stack.Navigator>
</NavigationContainer>
```

---

* **const Stack = createStackNavigator();**
  * Stack 형태의 네비게이션을 만들기 위해 **Navigator** 와 **Screen** 을 값으로 갖는 객체를 반환한다.   

* **NavigationContainer**
  * 네비게이션 계층 구조와 네비게이션 상태를 관리하는 컨테이너 역할

* **Navigator**
  * Screen 을 관리하는 중간 관리자 역할

* **Screen**
  * 페이지(컴포넌트) 의 별명과 컴포넌트를 각각 name / component 라는 props 로 가지며, 하나의 **Navigator** 에 여러 스크린이 들어갈 수도 있음.   

---

App.js 에는 이렇게 네비게이터와 네비게이팅을 진행할 스크린을 정해주면 된다.   

예를 들면 메인 컴포넌트에서 로그인 컴포넌트와 회원가입 컴포넌트로 이동하기 위해서는 다음과 같이 한 네비게이션 안에 각자 다른 스크린으로 불러온다.

---

**- App.js**
{: .notice--info}

```javascript
import * as React from 'react';
import {NavigationContainer} from '@react-navigation/native';
import {createStackNavigator} from '@react-navigation/stack';
import 'react-native-gesture-handler';
import MainPage from './mainPage/MainPage';
import LoginPage from './loginPage/LoginPage';
import RegisterPage from './RegisterPage/RegisterPage';

const Stack = createStackNavigator();

const App = () => {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="Main" component={MainPage} />
        <Stack.Screen name="Login" component={LoginPage} />
        <Stack.Screen name="Register" component={RegisterPage} />
      </Stack.Navigator>
    </NavigationContainer>
  );
};

export default App;
```

---

이렇게 되면 **MainPage** 라는 컴포넌트는 네비게이션 안에서 **Main** 이라는 별명(**경로**)을 갖게 되고, 로그인과 회원가입 컴포넌트 역시 **"Login"**, **"Register"** 라는 별명을 갖게 되었다.

---

## 3. 🚄 네비게이션을 통해 화면 전환하기    

이제 네비게이팅이 끝났으니 본격적으로 버튼을 통해 화면을 넘나들어 보자.   
화면을 실제로 넘나들 때는 navigation 을 props 로 받아야 한다.

---

**- 🚨 navigation 을 props로 받되, screen에서 명시적으로 넘길 필요는 없다.**
{: .notice--info}

```javascript
import * as React from 'react';
import 'react-native-gesture-handler';
import {View, Text, Button, StyleSheet} from 'react-native';

const MainPage = ({navigation}) => {
  return (
    <View style={styles.container}>
        <Button
          name={'로그인'}
          onPress={() => navigation.navigate('Login')}
        />
    </View>
  );
};

export default MainPage;
```

---

버튼의 onPress 이벤트에 `navigation.navigate()` 함수를 사용해 **Login** 이라는 경로로 화면 전환을 진행하는 코드다.   

이 때 **Login** 은 컴포넌트의 진짜 이름이 아닌, App.js 에서 네비게이션 설정을 진행할 때 스크린의 props 로 주어진 **name** 의 값이다.   

---
**- 🛫 버튼을 통해 컴포넌트를 오가는 모습**
{: .notice--info}

<img src = "/assets/images/2020-04-19-react-navigation-사용하기/navigation.gif" />
