---
layout: post
title: 베어유 리액트 8강 &#58 Props란 무엇일까요?
image: 6.jpg
date: 2023-09-24 15:15:20 +0900
tags: [React, BearU]
categories: React
---
> 리액트의 컴포넌트에 값을 넘길 수 있는 Props(프로퍼티)에 대해서 배워봅시다.

#### App.js
```jsx
<pre>
<code>
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }

}
</code>
</pre>
```

#### Hello.js
```jsx
<pre>
<code>
public class BootSpringBootApplication {
  public static void main(String[] args) {
    System.out.println("Hello, Honeymon");
  }

}
</code>
</pre>
```

#### 비구조화 할당
```jsx
import React from 'react';

function Hello({name}){ // 중괄호 까먹지 말기
    return <h1>Hello, {name}</h1> // 결과는 위 코드와 동일
}

export default Hello;
```

#### 프로퍼티의 기본값 설정
```jsx
import React from 'react';

function Hello({name}){
    return <h1>Hello, {name}</h1>
}

Hello.defaultProps = {
    name: "react!"
}
export default Hello; 

/*
import React from 'react';
import Hello from './Hello';

function App(){
  return(
    <Hello />
  );
}

export default App;
결과는 동일
*/
```