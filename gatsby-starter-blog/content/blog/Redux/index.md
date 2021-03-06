---
title: Redux
date: "2022-03-03"
description: 상태관리 라이브러리로 리덕스와 리덕스 툴 킷을 선택한 이유. 작업하면서 있었던 이슈들.
---

왜 Redux Toolkit ?
(http://blog.hwahae.co.kr/all/tech/tech-tech/6946/)
리덕스는 플럭스 아키텍처 모델. store, action, reducer
reducer는 변화를 일으키는 함수로써 전달받은 액션을 가지고 새로운 상태를 만들어서 스토어에 전달합니다. 이 모든 설계는 데이터가 단방향으로 흐른다는 전제하에 데이터의 일관성을 향상시키고 디버깅을 쉽게 하려는 의도. 하지만 리덕스는!
환경 설정이 너무 복잡하고, 이런저런 패키지와 의존성을 추가해야하고 보일러 플레이트가 너무 부담이다!

따라서 이번 프로젝트에선 RTK를 사용해본다.

## RTK , ReduxToolkit

RTK의 핵심목표는 리덕스의 복잡성을 낮추고 사용성을 높이는 것이라고 한다
action type, action creator 를 따로 설정하지 않고 slice로 쉽게 설정 가능하고
immer가 내장되어 있어 mutable하게 state를 수정할 수 있어 편한듯
reduxasyncThunk 나 reduxQuery로 비동기를 쉽게 지원한다는데 아직은 익숙하게 사용하는데 어려움이 있는 상태임 ㅜㅜ
그리고 타입스크립트와 잘 맞는다는게 큰 장점이라는데 아직 타입스크립트를 쓸 줄 몰라서 정작 나는 편읜성을 크게 느끼진 못하고 있는것같다.ㅜㅜ

### 이슈

(https://redux-toolkit.js.org/api/createAsyncThunk)

RTK 의 createAsyncThunk 에서 고생을 좀 했다.
데이터를 fetching 하고 난 후 fetching한 데이터를 전역으로 상태관리 할 필요가 없다면 createAsyncThunk를 쓸 필요가 없나.

RTK query 가 데이터캐싱과 isLoading을 기본적으로 제공한다고 하는데 이것을 이번 프로젝트 기간에 배우지 못한게 많이 아쉽다.

> RTK의 createAsyncThunk를 사용하면 reduxDevTools로 디버깅하기엔 확실히 편할 것 같다. 하지만 >전 프로젝트에서 사용했던 recoil과 비교해보면 RTK는 여전히 무겁고 어렵고 손이 많이 가는 것 같다. >recoil은 loadable 객체로 데이터 캐싱과 promise resolve 상태까지 한번에 관리가 가능했어서 >recoil이 안정성만 보장이 된다면 recoil을 깊게 배우는 것도 괜찮을 것 같다.
