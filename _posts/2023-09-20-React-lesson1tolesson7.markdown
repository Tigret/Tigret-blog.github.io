---
layout: post
title: 베어유 리액트 1강~7강
image: 6.jpg
date: 2023-09-13 20:23:20 +0900
tags: [React, BearU]
categories: React
---
1강

html tag -> 자바스크립트 내부 트리구조로 변경 : DOM(REACT으로 조작) -> 브라우저 화면에 출력(렌더링)

2강

컴포넌트(head,left,right,bottom) -> 오브젝트 구성

컴포넌트 : props를 입력받아 JSX를 리턴하는 "함수"

컴포넌트들을 모아서 전체 리액트 앱을 구성 -> 함수형 컴포넌트

{% highlight jsx %}
export default function MyComponent(props){
return <p>Hello React!</p>
}

{% endhighlight %}

컴포넌트의 장점 -> 가독성, 재사용성, 유지보수

HTML

{% highlight html %}
<html>
<head>
<title>My first web page</title>
</head>
<body>
<h1>
Hello World!
</h1>
<p>
How are you?
</p>
</body>
</html>
{% endhighlight %}

컴포넌트

{% highlight jsx %}
<Header/>
<body>
<ArticleTitle/>
<ArticleBody/>
</body>
{% endhighlight %}

==> 컴포넌트는 함수기 때문에 다른 리액트 모듈에서 다시 호출해서 사용할 수 있다(재사용 가능)

==> 수정사항이 다른 리액트 모듈에서 일괄적으로 변경

​

3강

JSX란?

HTML 태그처럼 생겼지만 자바스크립트(자바스크립트의 확장 문법)

컴포넌트를 편리하게 사용할 수 있도록 하는 리액트만의 문법

실제로는 리액트는 Babel을 이용해 JSX를 JS로 컴파일

{% highlight jsx %}
const element = <h1 className="article_title">Hello.world!</h1>
{% endhighlight %}

표현식

{% highlight jsx %}
const name = 'Josh Perez';
const element1 = <h1>Hello,{name}</h1>;
const element2 = (
<h1>
Hello,{formatName(name)}!
</h1>
);
{% endhighlight %}

중괄호 안에 JS라면 뭐든지 넣을 수 있다(변수, 함수, JSX 등등...)

{% highlight jsx %}
const element = (
<div>
<h1>Hello!</h1>
<h2>Good to see you here.</h2>
<body/>{/*body></body>*/}
</div>
);
{% endhighlight %}

1. JSX에서는 두 개 이상의 태그(h1,h2)를 하나의 태그(div)로 묶어줘야함

2. html과 마찬가지로 div 아래에 태그를 넣어 level을 지정

3. JSX에서는 여는 태그가 있으면 닫는 태그가 있어야 한다. 다만 위의 body같은 경우는 여는 태그와 닫는 태그가 동일 -> self closing tag -> 중간에 텍스트가 없을 경우 사용

{% highlight jsx %}
import React from 'react';
import Hello from './Hello';

function App(){
return (
<>
<Hello/>
<div>Goodbye</div>
</>
);
}

export default App;
{% endhighlight %}

태그 안에 아무런 이름이 적혀있지 않은 react fragment는 쓸모없이 태그가 낭비되는 것을 막는다.(<div> -> <>) -> 태그를 묶어주는 기능

{% highlight jsx %}
import React from 'react';
import Hello from './Hello';

function App(){
return (
<>
<Hello/>
<div className="good-bye">Goodbye</div>
</>
);
}

export default App;
{% endhighlight %}

어트리뷰트를 사용할 때 자바스크립트처럼 CamelCase를 사용한다. 만약 JSX 내부에 CSS를 넣는다면 전부 CamelCase로 바꿔줘야함.

{% highlight jsx %}
import React from 'react';
import Hello from './Hello';
import './App.css';

function App(){
//comment in javascript
return(
<>
{/*comment in jsx*/}
/*This is normal text*/
<Hello/>
<div className="good-bye">Goodbye</div>
</>
);
}

export default App;
{% endhighlight %}

자바스크립트는 //로 주석, JSX는 {/*내용*/}로 주석, 중괄호 없으면 텍스트로 인식되니 주의!!

​

4강

Prettier : JS와 React의 Formatting을 맞춰줌 

-> Window 단축키 : alt + shift + F

ESLint : JS의 문법을 확인해줌

​

5강

JS -> browser의 DOM을 조작하기 위해 만들어짐 -> node.js 등장 후 일반 프로그램의 조작 가능(runtime, 자바의 JVM이나 파이썬 interpreter과 같은 기능)

node.js > JS > react.js

터미널

node --version

npm --version : 노트 패키지 매니저 -> 설치, 제거, 업데이트 도구

npx --version : 실행만 담당 -> create react app이라는 패키지를 실행할 때 사용 -> 실행결과가 저장되지 않기 때문에 용량을 아낄 수 있고 항시 최신버전으로 이용 가능

create react app : 

1. dev서버가 함께 포함 -> 코드를 수정을 하면 자동으로 코드 수정사항을 컴파일 해서 브라우저에서 변경사항을 실시간으로 보여줌

2. 웹핵 : 여러가지 흩어진 소스코드를 하나로 묶어줌 -> 용량을 줄여준다.

3. 바벨 : JSX는 자바스크립트의 확장문법! -> JSX를 JS로 컴파일해줌

​

6강 Create React APP(CRA)으로 앱 만들어보기

node_modules : mpn으로 설치한 것들이 모두 들어감

public : 서버를 배포하게 되면 기본적으로 접근 가능한 것들 -> index.html : 항상 인터넷 서버의 root에서 접근이 가능한 html 파일 어떤 서버를 화면에 표시하고자 할 때 가장 먼저 보이게 됨

src : react app을 구성

gitignore : 프로젝트를 만들기 위해서 어떤 git 파일을 추적하고 추적하지 않을지 정해놓은 파일

package.json : 프로젝터의 메타 데이터를 담음

yarn.lock : npm과 같은 것 지금은 필요 없음

ctrl + shift + ~ : 터미널 시작 -> npm start 입력(개발서버 시작) -> localhost 3000으로 port에서 실행

index.html -> body 아래 <div id="root">가 있음 -> root를 react가 찾아서 root 밑에 DOM을 쌓게 됨

index.js -> document.getElementByld에서 root를 찾고 있음

{% highlight jsx %}
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

{% endhighlight %}

ReactDOM.render라는 함수가 JSX 컴포넌트르 root 요소 밑에 rendering 하겠다는 뜻... -> 그렇기 때문에 index.html 밑에 아무것도 없어도 App이라는 컴포넌트가 rendering이 될 수 있음

App.js에서 <p/> 안을 수정하면 코드를 정할 때마다 개발서버에서 코드 변경 사항을 감지 ->  변경된 코드로 다시 한 번 compile 해서 자바스크립트 코드로 변경 -> JS코드가 브라우저 화면에 나타남

​

7강 : 함수형 컴포넌트와 클래스 컴포넌트의 차이점

{% highlight jsx %}
class App extends React.Component{
render(){
return <h1>Hello, React!</h1>
}
}

{% endhighlight %}

React.Component라는 React의 class를 extend 키워드로 상속받는 App이라는 class를 만듦 -> React.Component라는 컴포넌트를 상속받는 클래스형 컴포넌트를 만들 때에는 반드시 랜더 함수가 정의 되어야함 -> 랜더 함수는 반드시 jsx를 return하는 부분을 포함해야함

{% highlight jsx %}
function App(){
return <h1>Hello, React!</h1>
}
{% endhighlight %}

함수형 컴포넌트 : function 키워드와 App이라는 함수명, 함수 내부에서 jsx를 return하는 부분으로만 구성됨 -> React 버전에서는 클래스형 컴포넌트는 더 이상 사용하지 않고 함수형 컴포넌트를 사용하도록 권장 -> 왜냐하면 클래스의 사용법이 어렵고 복잡할 뿐 아니라 코드가 복잡해져서 -> 원래 클래스형 컴포넌트에서만 State라는 걸 사용할 수 있어서 기존에는 함수형 컴포넌트를 쓸 수 있었지만 실질적으로 쓰기가 굉장히 어려움 -> 하지만 최근에는 State가 React Hook으로 함수형 컴포넌트와 React hook의 조합으로 구성하는 것을 훨씬 더 많이 사용하고 있음