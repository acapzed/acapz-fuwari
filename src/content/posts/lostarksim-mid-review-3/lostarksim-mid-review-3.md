---
title: "로아시뮬 회고 3 - 시뮬레이션 엔진 만들기"
published: 2026-05-07
description: "성능을 고려한 시뮬레이터 엔진"
image: "./lostarksim_title.svg"
tags: [Project, Dev, Lostarksim]
category: Project
draft: false
---

본격적으로 메인 기능인 시뮬레이터를 만들자!

관성적으로 원래 웹서비스를 만들던 JS로 토대를 만들다가, 이런 생각이 났다.

> JS는 single thread으로 돌아갈텐데, 성능(속도)가 나올까?

특히 node.js는 io만 multi thread고 내부 로직은 single thread로 돌아가기 때문에 blocking 문제라도 해결하기 위해서 async/await을 쓴다고 네부캠에서 학습한 기억이 나서, 단순히 single thread으로 돌아가고 + 실행속도 자체도 느린 js으로 시뮬레이터가 커버될까 의문이 들었다.

마침 이번 프로젝트는 책임에 따라 module화를 잘 해놓은 덕분에 각 모듈마다 다른 언어를 선택할 수 있었다.

보통 성능이 필요한 작업에 사용되는 언어는 C++이다. 다만 전에 sdl2 + mingw 빌드환경 만들면서 쓸데없는 개고생을 한적이 있어서 뭔가 거부감이 들기도 했고, C++는 메모리 관리하기가 힘들다고 생각했다. 결정적으로 C++에 그렇게 익숙하지 않아서, 배울거면 최근 유행하는 Go나 Rust와 같은 언어를 해보는것도 나쁘지 않겠다 싶었다.

# Simulator Stack 고민

c++의 차세대 언어로는 go와 rust가 있다고 들었는데, 이 둘을 claude와 비교했다.

go는 메모리관리를 gc가 대신해주고 배우기 쉬워 생산성이 높고, Rust는 메모리 관리를 직접해야하지만 안전하고, 소유권 개념이 있어서 접근하기 어렵다. 둘 다 성능은 비슷하다고 가정하면, 비교적 배우기 빠른   