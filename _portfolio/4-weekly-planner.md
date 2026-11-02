---
title: "Weekly Planner"
excerpt: "요일별로 일정을 추가·조회·수정·삭제할 수 있는 React 주간 플래너"
collection: portfolio
date: 2022-11-26
---

<!-- 스크린샷을 images/ 에 넣고 아래 주석을 풀어 주세요 -->
<!-- ![Weekly Planner 실행 화면](/images/weekly-planner.png) -->

## Overview
이름을 입력하고 들어가면 요일별로 일정을 관리할 수 있는 주간 플래너 웹 앱입니다.
React를 처음 공부하며 CRUD(생성·조회·수정·삭제) 기능과 컴포넌트 간 데이터 흐름을 익히기 위해 만들었습니다.

## Tech Stack
React 18 · React Router v6 · CSS Modules

## 구현 내용
- React Router로 시작 화면(`/`)과 플래너 화면(`/plan`) 라우팅, 이름 입력 후 `Link`로 이동
- 상태 끌어올리기(lifting state up)로 시작 화면에서 입력한 이름을 플래너 화면과 공유
- 요일 카드마다 해당 요일의 일정만 필터링해 표시
- 일정 추가(팝업 입력), 수정(수정 모드 전환), 삭제
  - 기존 배열을 직접 바꾸지 않고 `map`, `filter`, 스프레드 문법으로 새 배열을 만들어 상태를 불변하게 업데이트
  - 일정마다 `uuid`로 고유 ID를 부여해 수정·삭제 대상을 구분
- 역할별 컴포넌트 분리(`Days`, `PlanList`, `AddPlan`, `GetName`)와 CSS Modules로 컴포넌트별 스타일 분리

## 돌아보며
React를 처음 배우면서 만든 프로젝트라, 지금 다시 보면 아쉬운 점이 보입니다.
- **데이터가 저장되지 않음**: 일정은 JSON 예시 데이터로 시작해 메모리의 상태로만 관리되어 새로고침하면 초기화됩니다. 지금이라면 `localStorage`나 백엔드 API로 저장하겠습니다.
- **리스트 `key` 지정 실수**: 요일 카드 목록에 고유하지 않은 값을 `key`로 넘겨, React가 목록을 올바르게 구분하지 못할 수 있었습니다. 요일 ID처럼 항목마다 고유한 값을 써야 합니다.
- **상태 업데이트 방식**: 현재 상태 값을 그대로 참조해 새 상태를 만들고 있어, 연속으로 업데이트할 때 이전 변경이 덮어써질 수 있습니다. `setPlans(prev => ...)`처럼 함수형 업데이트를 쓰는 것이 안전합니다.

## Links
- [GitHub](https://github.com/UGI1621/Weekly-planner_CRUD){:target="_blank" rel="noopener noreferrer"}
