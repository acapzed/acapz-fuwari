---
title: "로아시뮬 회고 3 - 시뮬레이션 엔진 만들기"
published: 2026-05-07
description: "성능, 성능을 보자"
image: "./lostarksim_title.svg"
tags: [Project, Dev, Lostarksim]
category: Project
draft: false
---

본격적으로 메인 기능인 시뮬레이터를 만들자!

관성적으로 원래 웹서비스를 만들던 JS로 토대를 만들다가, 이런 생각이 났다.

> JS는 single thread으로 돌아갈텐데, 성능(속도)가 나올까?

특히 node.js는 io만 multi thread고 내부 로직은 single thread로 돌아가기 때문에 blocking 문제라도 해결하기 위해서 async/await을 쓴다고 네부캠에서 학습한 기억이 나서, 단순히 single thread으로 돌아가고 + 실행속도 자체도 느린 js으로 시뮬레이터가 커버될까 의문이 들었다.

이번 프로젝트는 책임에 따라 module화를 잘 해놓은 덕분에 각 모듈마다 언어를 다르게 선정할수 있어서 시뮬레이터에 적합한 언어를 선정할 수 있었다. MSA의 장점이기도 하다.

보통 이런 프로젝트에서 사용되는 언어는 C++이다. 다만 전에 sdl2 + mingw 빌드환경 만들면서 쓸데없는 개고생을 한적이 있어서 뭔가 거부감이 들기도 했고, C++는 메모리 관리하기가 되게 힘들다고 생각했다. 결정적으로 C++에 그렇게 익숙하지 않아서 만들면서 배울거면 최근 유행하는 Go나 Rust와 같은 언어를 해보는것도 나쁘지 않겠다 싶어서 무턱대고 C++를 고르지 않았다.

# Simulator Stack 고민
