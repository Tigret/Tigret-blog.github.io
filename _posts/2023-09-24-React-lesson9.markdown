---
layout: post
title: 베어유 리액트 9강 &#58 실수하기 쉬운 Props 사용법
image: 6.jpg
date: 2023-09-24 15:24:20 +0900
tags: [React, BearU]
categories: React
---
#### App.js
```jsx
import Hello from './Hello';
import Wrapper from "./Wrapper";

function App(){
  return(
    <Wrapper> //Wrapper 컴포넌트 호출, Wrapper 안에 싸여있는 것들이 children
    <Hello name="react!"/> //Hello 컴포넌트 호출
    <p>I love React!</p>
    <Hello name="React!"/>
    </Wrapper>
  );
}

export default App;
```

#### Hello.js
```jsx
import React from 'react';

function Hello({name}){
    return <h1>Hello, {name}</h1>
}

Hello.defaultProps = {
    name: "react!"
}
export default Hello; 
```

#### Wrapper.js
```jsx
import React from "react";

function Wrapper({children}){ //중요 Point : 반드시 children을 프로퍼티로 불러와야함
    const style = {
        border: '1px solid red',
        padding: '12px',
    };
    return <div style={style}>{children}</div> //css style을 불러옴, 불러온 프로퍼티를 div태그에 싸서 리턴
}

export default Wrapper;
```