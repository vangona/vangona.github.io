---
layout: post
title: 와글와글 Parallax 스크롤
categories: Projects
tags:
  - 와글와글
  - Parellex
  - UX
hero: "https://source.unsplash.com/random"
overlay: purple
published: true
---

# <center>와글와글 Parallax 스크롤 도입기</center>

![scroll-animation (1)](https://user-images.githubusercontent.com/69471032/207240377-1d732c76-7d1c-439e-9ddf-4a67be2f11c5.gif)

## ❓ 스크롤 애니메이션 도입기

- 랜딩페이지에 단순한 설명이 적혀있으면 설명이 읽히지 않을 것이라고 생각했다.
- 캠퍼분들께 데모 사이트를 공유할 때, 가능하다면 어떤 것을 위한 서비스인지 전달할 수 있으면 좋겠다고 생각했다.
- 데모 사이트를 공유하는 글에 서비스 소개가 적히면, 글이 무거워져서 유저가 진입하기 어렵다고 판단했다.
- 사용하는 사람들이 흥미롭게 읽어볼 수 있는 소개 사이트를 만들기 위해 상호작용이 가능한 스크롤 애니메이션을 구현해보았다.
- 또한 유저가 소개글에 몰입하여 서비스와 유대감이 생길 수 있도록 Parallax 스크롤을 구현했다.

## 🛤️ 과정 : Intersection Observer, SVG, Parallax

### Intersection Observer API

- Intersection Observer를 통해 설명 섹션의 절반 이상을 지나면 이벤트가 발생할 수 있도록 구현

### SVG path 따라 그리기 (SVG dashoffset과 dasharray)

- 단순히 글자의 opacity를 바꾼다거나 slide-in 하는 것은 흥미를 끌기 어려웠고, 너무 화려한 애니메이션은 서비스의 성격과 맞지 않았고, 글자가 자연스럽게 써지는 효과가 있으면 좋겠다고 생각해서 구현하게 되었다.
- SVG dashoffset과 dasharray 속성을 이용하여 SVG의 path를 자연스럽게 그릴 수 있었다.
- 이러한 속성과 Intersection Observer를 활용하여 유저의 스크롤에 반응하는 스크롤 애니메이션을 구현했다.

### 시차 스크롤 (Parallax Scroll)

- 처음에는 background-attachment 속성을 이용하여 전체 배경 이미지에 parallax를 사용하려했으나, 구현하고나니 서비스 소개와 맞지 않는다는 것을 알게되었습니다. 가벼운 느낌의 서비스 소개와 어울릴 수 있도록 간단한 이미지와 사용할 수 있어야 했습니다. 이를 위해서 시차를 직접 구현했다.
- window scroll 이벤트에 window.scrollY를 리액트의 상태로 저장하고, 이 상태에 따라서 특정 이미지를 transform translateY을 사용해서 스크롤에 따라 이동할 수 있도록 했다.
- 여기에서 window.scrollY와 1:1로 이동하는 것이 아니라 비율을 조정하여 원근감이 있는 것처럼 보이도록 구현할 수 있었다.

## ❗결과 : UX적으로 몰입감 있는 서비스 소개

- 데모를 배포할 때, 소개글을 따로 추가하지 않아도 되어서 글이 가볍게 공유될 수 있었고 기대치인 30명보다 더 많은 47명의 사람들이 방문했다.
- 지루할 수 있는 서비스 소개에 대해서 많은 유저분들이 끝까지 읽어주셨고, 스크롤 애니메이션과 서비스에 대해 피드백을 받아볼 수 있었다.
