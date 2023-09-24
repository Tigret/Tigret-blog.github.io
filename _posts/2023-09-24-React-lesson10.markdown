---
layout: post
title: 베어유 리액트 10강 &#58 리액트의 꽃, State
image: 6.jpg
date: 2023-09-24 15:26:20 +0900
tags: [React, BearU]
categories: React
---
#### App.js
```jsx
import React, {useState} from "react"; // import useState method

function Counter(){ //component
  const [number, setNumber] = useState(0); // default = 0, setNumber : Setter

  const onIncrease = () => { // 람다식?
    setNumber(number + 1);
  };

  const onDecrease = () => {
    setNumber(number - 1);
  };

  return (
    <div>
    <h1>{number}</h1>
    <button onClick={onIncrease}>+1</button>
    <button onClick={onDecrease}>-1</button>
    </div>
  )
}

export default Counter;
```
number의 경우 const로 정의되어 있기 때문에 setNumber 함수가 필요함.