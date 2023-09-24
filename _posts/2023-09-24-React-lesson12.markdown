---
layout: post
title: 베어유 리액트 12강 &#58 React Hook이란?
image: 6.jpg
date: 2023-09-24 15:32:20 +0900
tags: [React, BearU]
categories: React
---
> **Hook이란?**    
기존에 사용하던 클래스 컴포넌트의 여러 기능을 자연스럽게 함수형 컴포넌트에서 사용하기 위한 장치.

1. 클래스형 컴포넌트는 State를 클래스 내부에서 직접 다룰 수 있을 뿐만 아니라 컴포넌트의 생명주기인 라이프사이클도 직접적으로 다룰 수 있었음
2. 클래스형 컴포넌트는 자바스크립트 클래스이기 때문에 클래스를 사용하려면 기본적인 자바스크립트 문법을 잘 알아야 함
3. 함수형 컴포넌트는 간결하지만 클래스형에서 사용하던 State와 생명주기관리를 할 수 없어 문제가 있음.
4. 그래서 React 16.8버전 이후부터는 이 문제를 React Hook을 추가해 해결 -> 함수형 컴포넌트가 기존의 클래스형 컴포넌트를 완전히 대체할 수 있게됨

### **컴포넌트의 생명주기**
![]({{site.baseurl}}/images/LifeCycleOfComponent.jpg)

1. 왼쪽에서 오른쪽으로 순서대로 진행
2. 각 phase 안에서는 위에서 아래로 진행
3. Mounting phase : constructor는 우리가 만드는 컴포넌트가 생겨나는 과정(함수를 정의할 때 생겨남) > Rendering(브라우저에 DOM에 어떤 객체가 들어가서 브라우저 화면에 나타나도록 하느 목적) > 생겨난 컴포넌트를 DOM에 등록
4. Updating : Rendering이 진행되며 함께 진행 > 함수에서 받고 있는 Props 그리고 함수 내부적으로 사용하는 State 두 가지 값을 이용해서 return 하고 있는 jsx 컴포넌트값을 업데이트 > 하나의 컴포넌트의 등록과 값이 업데이트 되는 Rendering을 모두 거친 다음에 실제로 React에서는 브라우저의 DOM에 우리 컴포넌트를 등록해서 업데이트 > 브라우저에 우리가 만든 컴포넌트가 나타남
5. Unmounting : 컴포넌트가 더 이상 필요 없어지면 Unmounting phase를 거쳐서 DOM에서 사라짐
6. Render phase : React에서 관리하는 부분
7. Commit phase : 브라우저에 나타나는 부분