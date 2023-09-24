---
layout: post
title: 베어유 리액트 11강 &#58 State를 직접 사용해봅시다!
image: 6.jpg
date: 2023-09-24 15:29:20 +0900
tags: [React, BearU]
categories: React
---
#### Input.js
```jsx
import React, { useState } from "react";

function Input() {
  const [inputs, setInputs] = useState({
    // 기본값을 오브젝트로 정의
    subject: "",
    score: "",
  }); // 기본값이 빈칸이기에 실제 창에서는 입력창에 텍스트를 넣을 수 없음

  const onChange = (event) => {
    //비구조화 할당
    const { value, name } = event.target; //input element는 기본적으로 event가 들어있음. 그래서 overriding 하는 중
    // event.target은 실제 이벤트가 발생하고 있는 target DOM을 찾아줌
    setInputs({
      ...inputs, // "..."이라는 스프레드를 사용하면 기존의 object를 풀어 key와 value가 순서대로 하나씩 있는 것과 똑같은 효과
      [name]: value, //dynamic property assign, string으로 변수이름을 바꿔줌
    });
  };
  return (
    <>
      <div>
        <h2>
          성적 : {inputs.subject}
          {inputs.score}
        </h2>
        <input
          name="subject"
          placeholder="수학"
          value={inputs.subject}
          onChange={onChange}
        />
        <input
          name="score"
          placeholder="99"
          value={inputs.score}
          onChange={onChange}
        />
      </div>
    </>
  );
}

export default Input;
```
스프레드 : "..."를 객체 앞에 붙여 사용하면  기존의 object를 풀어 key와 value를 순서대로 가져옴 -> 만약 사용을 안한다? -> setInputs에서 기존 object, 기존 스테이트 값을 복사하지 않고 생기는 값만 스테이트를 업데이트

dynamic property assign : 아래있는 name은 string인데 string은 object의 이름으로 쓸 수 없음. 왜냐? 위에 있는 변수명과 다른 것으로 property가 취급이 되기 떄문 -> 그래서 대괄호를 넣게 되면 아래 subject를 호출하고 값을 채웠을 때 위의 스프레드에 의해 정의되었던 subject가 아래 동적 프로퍼티 할당에 의해 덮어 씌워짐... -> 만약 동적 프로퍼티 할당을 하지 않을 경우 아무리 박스에 입력을 하더라도 subject의 값이 변하지 않음

```jsx
import React from "react";
import Input from "./Input"

function App(){
  return <Input/>
}

export default App;
```