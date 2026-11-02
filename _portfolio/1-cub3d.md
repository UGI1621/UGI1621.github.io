---
title: "cub3D"
excerpt: "C와 miniLibX로 구현한 레이캐스팅 기반 3D 그래픽 프로젝트 · 42경산 팀 프로젝트"
collection: portfolio
date: 2026-03-30
---

<!-- 스크린샷이나 GIF를 images/ 에 넣고 아래 주석을 풀어 주세요 -->
<!-- ![cub3D 실행 화면](/images/cub3d.gif) -->

## Overview
.cub 맵 파일을 읽어 1인칭 시점의 3D 미로를 화면에 그리는 프로젝트입니다.
Wolfenstein 3D와 같은 레이캐스팅(Raycasting) 방식으로 2D 맵을 3D처럼 렌더링했습니다.
팀 프로젝트로 진행했습니다.

## Tech Stack
C · miniLibX · Make

## 구현 내용
- .cub 맵 파일 파싱 및 유효성 검사 (벽으로 둘러싸였는지, 텍스처 경로, 바닥/천장 색상)
- DDA 알고리즘 기반 레이캐스팅으로 벽까지의 거리 계산
- 방향별 벽 텍스처 매핑
- 키보드 입력을 통한 이동 및 시점 회전

## 어려웠던 점과 해결
### 레이캐스팅 원리 이해
레이캐스팅의 수식을 이해하는 것이 가장 어려웠습니다.
여러 자료를 참고하면서 계산 과정을 직접 손으로 풀어 보며 원리를 이해했고, 이 과정에서 이전 so_long 프로젝트에서 부족했던 miniLibX 기초도 다시 다지게 되었습니다.

### 과도한 CPU 사용
처음에는 프레임 수를 제한하지 않아, 실행할 때마다 렌더링이 쉬지 않고 반복되면서 CPU 사용량과 발열이 크게 올라갔습니다.
프레임 레이트를 고정하는 방법을 적용해 불필요한 렌더링을 줄여 해결했습니다.

## Links
- [GitHub](https://github.com/UGI1621/cub3d){:target="_blank" rel="noopener noreferrer"}
