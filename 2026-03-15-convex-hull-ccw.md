---
layout: post
title: "볼록 껍질(Convex Hull)과 CCW 알고리즘 정리"
date: 2026-03-15 00:00:00 +0900
categories: [알고리즘, 기하]
tags: [convex-hull, ccw, BOJ]
cover_image: ""
excerpt: "Graham scan과 Andrew's monotone chain의 구현 차이, 그리고 실전 문제에서 어떤 걸 선택해야 하는지."
---

## 개요

볼록 껍질(Convex Hull)은 주어진 점들을 모두 포함하는 가장 작은 볼록 다각형을 찾는 문제다.

## CCW (Counter-Clockwise)

세 점 A, B, C에 대해 방향을 판단하는 기본 연산이다.

```cpp
long long ccw(pair<long long,long long> a,
              pair<long long,long long> b,
              pair<long long,long long> c) {
    return (b.first-a.first)*(c.second-a.second)
         - (b.second-a.second)*(c.first-a.first);
}
```

반환값이 양수면 반시계, 음수면 시계, 0이면 일직선이다.

## Graham Scan vs Andrew's Monotone Chain

| 방식 | 정렬 기준 | 구현 난이도 |
|------|-----------|------------|
| Graham Scan | 기준점 기준 각도 | 중간 |
| Andrew's MC | x좌표 → y좌표 | 쉬움 |

실전에서는 Andrew's Monotone Chain이 구현이 더 깔끔하다.
