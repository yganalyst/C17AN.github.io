---
title:  "[React.js] - propTypes 소개"
search: true
toc : true
toc_label : 네비게이션
toc_sticky : true
header:
  teaser: "/assets/images/header/react.png"
tag:
  - 자바스크립트
  - 리액트
categories:
  - React
excerpt: "컴포넌트에 전달되는 프로퍼티를 검사하는 propTypes 프로퍼티 소개"
last_modified_at: 2020-02-25T08:06:00-05:00
---

<img src = "/assets/images/header/react.png"/>   

---

`React` 에서는 컴포넌트의 `props` 에 값을 대입하는 과정에서 **타입 충돌** 로 인한 문제를 예방하는 강력한 도구를 지원한다.  
[propTypes](https://ko.reactjs.org/docs/typechecking-with-proptypes.html#___gatsby) 프로퍼티가 그 주인공으로, 어떻게 사용할 수 있을지 알아보자. 😃


## 1. propTypes 의 역할 소개
`TestComponent` 는 문자열로 이루어진 `props` 속성을 받기로 되어 있다고 가정하자.  
하지만, 상위 컴포넌트에서는 `props` 에 해당하는 `props1` 에 숫자 타입의 값이인 12345 를 전달하고 있는 모습이다.  

{% highlight js %}
import React, { Component } from "react";
import PropTypes from "prop-types";

class App extends Component {
  render() {
    return (
      <div>
        <TestComponent props1={12345}/>
      </div>
    );
  }
}

class TestComponent extends Component {
  render() {
    const { props1 } = this.props;
    return <Mmdiv>{props1}</div>;
  }
}

export default App;
{% endhighlight js %}

**콘솔 검사결과**
{: .notice--info}

<img src="/assets/images/2020-02-25-propTypes/에러메시지 X.PNG">
컴포넌트를 설계할 때 하위 컴포넌트에는 문자열로 된 값이 `props1` 로 주어지길 바랬지만, 실제 주어진 값은 숫자 타입의 값이었다.  


프로그램이 거대해지면 props로 주고받는 데이터의 양도 사람이 컨트롤하기 어려울 정도로 거대해질 것이고, 타입 충돌로 인한 디버깅을 위해서는 props 값을 일일히 디버거로 찍어봐야 하는 귀찮은 일을 해야 할 것이다.  


🌟 바로 이럴 때, `propTypes` 프로퍼티가 빛을 발한다. 🌟


## 2. propTypes 프로퍼티 사용하기
propTypes 프로퍼티는 기본적으로 `prop-types` 라이브러리에서 불러와야만 사용할 수 있다.  

철자에 유의하며 코드 최상단에 아래 구문을 추가한다.  
{% highlight js %}
import propTypes from 'prop-types';
{% endhighlight js %}

사용하는 방법은 간단하다.
{% highlight js %}
(컴포넌트명).propTypes = {
  (프로퍼티명): PropTypes.(타입명);
};
{% endhighlight js %}  
이렇게 `.propTypes` 라는 프로퍼티를 컴포넌트에 사용할 수 있으며, 프로퍼티에는 타입을 지정할 `props 속성 이름` 과 `타입` 을 키 - 값의 쌍으로 가지는 객체를 대입한다.  


## - propTypes 를 사용한 코드
`propTypes` 프로퍼티는 프로그램의 표면에는 보이지 않지만 매우 강력한 역할을 수행한다.  
1절에서 등장한 "propTypes 를 사용하지 않은 코드" 를 `propTypes` 를 사용해 고쳐보자.

{% highlight js %}
import React, { Component } from "react";
import PropTypes from "prop-types";

class App extends Component {
  render() {
    return (
      <div>
        <TestComponent props1={12345}/>
      </div>
    );
  }
}

class TestComponent extends Component {
  render() {
    const { props1 } = this.props;
    return <div>{props1}</div>;
  }
}

// propTypes 프로퍼티를 이용한 props 타입 검사
TestComponent.propTypes = {
  props1: PropTypes.string
};

export default App;
{% endhighlight js %}

🚨 **콘솔 검사결과** 🚨
{: .notice--danger}

<img src="/assets/images/2020-02-25-propTypes/에러메시지 O.PNG">  

갑자기 아무것도 없던 콘솔에 요란한 경고가 등장하고 있다.  
`propTypes` 는 이렇게 `props` 값의 타입 검사를 수행하며, 지정한 타입 외의 값이 들어오면 이렇게 콘솔에 경고 메시지를 출력한다.

## 3. propTypes 를 사용할 때의 유의점
{% highlight js %}
(컴포넌트명).propTypes = {
  (프로퍼티명): PropTypes.(타입명);
};
{% endhighlight js %}  
`propTypes` 를 사용해 타입을 검사할 때, (타입명) 부분에 오는 타입은 자바스크립트 기본 자료형뿐만 아니라 객체나 배열 등을 적절히 가공한 형태로 주어질 수도 있다.  
이와 관련된 정보는 [propTypes 공식 리액트 문서](https://ko.reactjs.org/docs/typechecking-with-proptypes.html#proptypes) 를 참조하자.

## 4. propTypes 를 이용한 필수 프로퍼티 지정하기
강력한 타입 검사 기능은 분명 매력적이지만, 이외에도 유용한 기능이 있다.  
바로 반드시 받아야 할 프로퍼티가 있다면 `.isRequired` 라는 특수한 기능을 사용해서 해당 프로퍼티를 필수 프로퍼티로 지정할 수 있다.  

## - .isRequired 변수 사용법
필수 프로퍼티를 지정할 때는 자료형을 검사하는 코드에 `.isRequired` 기능을 덧붙이면 된다.  

{% highlight js %}
(컴포넌트명).propTypes = {
  (프로퍼티명): PropTypes.(자료형).isRequired
};
{% endhighlight js %}  


## - .isRequired 를 사용한 코드
{% highlight js %}
import React, { Component } from "react";
import PropTypes from "prop-types";

class App extends Component {
  render() {
    return (
      <div>
        <TestComponent/>
      </div>
    );
  }
}

class TestComponent extends Component {
  render() {
    const { props1 } = this.props;
    return <div>{props1}</div>;
  }
}

// isRequired 를 이용한 필수 프로퍼티 검사
TestComponent.propTypes = {
  props1: PropTypes.string.isRequired
};

export default App;
{% endhighlight js %}

필수 프로퍼티로 지정한 값이 들어오지 않으면, 콘솔은 다음과 같은 경고를 출력한다.

🚨 **콘솔 검사결과** 🚨
{: .notice--danger}
<img src="/assets/images/2020-02-25-propTypes/필수 프로퍼티.PNG">

이처럼 `propTypes` 의 기능을 잘 사용하면, 생각보다 훨씬 강력한 디버깅 도구가 되어줄 것이다.  
컴포넌트를 만들 때 가능하면 `propTypes` 프로퍼티를 사용하는 습관을 들여보자. 😄
