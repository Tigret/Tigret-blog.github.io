---
layout: post
title: 베어유 리액트 13강 &#58 페이지가 로딩될 때 작동하는 Hook
image: 6.jpg
date: 2023-09-24 16:38:20 +0900
tags: [React, BearU]
categories: React
---
##### **useEffect Hook**
자동으로 호출이 됨. 컴포넌트가 마운트 되고 DOM이 변경된 다음 렌더링이 일어나는데 그 다음 useEffect가 실행

##### **useEffect는 언제 필요한 것일까?**
1. Props에 속한 값을 컴포넌트의 로컬 변수로 선언하는 경우 useEffect에서 이걸 할당해줌
2. 외부 API를 호출해서 통신을 통해서 어떤 값을 받아오거나 받은 값을 state로 넣어주는 작업
3. 써드파티 라이브러리를 써서 무언가 다른 작업들을 해줘야 할 때

> 렌더링이 다 되면 화면에는 요소들이 다 나타나고 그 다음에 다시 한 번 데이터를 변경하는 작업들을 useEffect가 한다.

```jsx
import React, { useState, useEffect } from "react";

function App() {
  const [count, setCount] = useState(0);

  useEffect(() => {// 변경된 값을 계속 refresh 해줌
    console.log("useEffect");
    document.title = `you clicked ${count} times`;
  });
  return (//return값 먼저 실행(DOM) 후 useEffect 실행
    <>
      <p>you clicked {count} times</p>
      <button
        onClick={() => {
          console.log("Click");
          setCount(count + 1); 
        }}
      >
        Click Me
      </button>
    </>
  );
}

export default App;
```


