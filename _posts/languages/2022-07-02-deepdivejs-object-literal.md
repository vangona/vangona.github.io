---
layout: post
title: DeepDiveJS Chapter 10. 객체 리터럴
categories: Languages
tags:
  - DeepDiveJS
  - Javascript
hero: "https://source.unsplash.com/random"
overlay: purple
published: true
---

# [10장. 객체 리터럴]

</br>

### ✏️ 추상화란?

---

&nbsp; 객체를 쓰기 전에, 추상화를 설명하지 않을 수가 없었다.

> _추상화는, 공통적인 속성이나 기능을 가지는 것을 묶어서 이름 붙이는 것이다._

이게 무슨 말인가. 우리는 추상화라는 단어를 처음 들어보지만 매일 추상화를 하며 살고 있으며, 삶에 추상화가 없으면 우리는 모두 불편한 설명충이 된다.

우리가 **집**이라고 부르는 개념은 **거주가능한 공간을 제공하며...** 라는 등의 **공통적인 기능과 속성을 가지는 어떤 개념**들을 **묶어서 설명**하기 위해 이름 붙인 개념이다.

인간은 여러 복잡한 개념들을 효율적으로 설명하고 전달하는 의사소통의 수단으로 추상화를 선택했고, 이를 통해 놀랄만한 성장을 이뤄냈다.

그러니 이 추상화된 언어라는건 인류가 세상을 지배한만큼 오래되어서, **추상화**라는 단어는 설명을 듣는 것조차 부담스러울만큼 추상화되어 익숙해진 것이다.

인간은 컴퓨터와 소통하고, 컴퓨터에 쓰여진 명령을 이해하는데에도 이런 추상화의 능력을 사용하고자 했다. 이것이 **객체 지향 프로그래밍**이라는 패러다임이며, 이를 위해 도입된 개념이 후의 설명될 **객체**이다.

### ✏️ 객체란?

---

&nbsp; 객체는 다른 객체와 구분되게, 상태나 동작을 공유할 수 있도록 개념을 묶어서 추상화한 것을 말한다.

다르게 말하자면, 물리적으로 존재하거나 추상적으로 생각할 수 있는 것 중에서 다른 것과 식별 가능한 것을 말한다.

사실 계속 공부하면서 느끼는 건, 객체는 딱 떨어지게 설명할 수 있는 것이라기보다는 개념에 가까운 것 같다.

'이건 객체, 이건 객체가 아니야.' 라고 구분할 수 있다기보다는 '이건 객체로 표현하는게 효율적일 수 있겠다.' 라고 구분하는 것이 더 적당한 것을 객체로 표현한다.

추상화와 객체 자체가 효율적인 의사소통을 위해 만들어진, 합의된 개념이라 당연한 것 같기도 하다.

</br>

### ✏️ 프로퍼티와 메서드, 컴퓨터에서 객체를 사용하는 방법

---

&nbsp; 컴퓨터에서는 객체를 다루기 위해 **프로퍼티**와 **메서드**를 사용한다.

위의 설명을 축약하자면 추상화는 공통적인 **속성이나 기능**을 묶어서 이름 붙이는 것이며, 그렇게 묶여서 이름 붙은 것이 **객체**라는 것인데.

여기서 말하는 공통적인 속성의 상태를 프로퍼티라고 하며, 공통적인 기능을 메서드라고 한다.

객체의 프로퍼티와 메서드는 객체를 어떤 관점으로보고 어떤 기능과 속성을 공통적으로 보았는지에 따라서 달라지게 된다.

> **개발자가 제일 어려워하는건 변수명 짓기이다.**

라는 말의 일부분에는 이런 맥락이 있다. 어디까지 추상화해야할지, 추상화한 내용을 어떻게 표현할지가 굉장히 어렵고 중요하다.

이렇듯 이러한 속성의 상태나 기능을 어떻게 묶어서 표현할지는 개발자의 능력에 달렸으며, 이런 부분을 보완하기 위해 디자인 패턴을 학습하게 된다.
