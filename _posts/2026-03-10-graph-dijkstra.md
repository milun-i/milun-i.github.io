---
layout: post
title: "다익스트라(Dijkstra) 알고리즘 — 우선순위 큐 구현"
date: 2026-03-10 00:00:00 +0900
categories: [알고리즘, 그래프]
tags: [dijkstra, graph, priority-queue, BOJ]
cover_image: ""
excerpt: "우선순위 큐를 이용한 다익스트라 구현과, 흔히 하는 실수인 visited 배열 처리 방식 정리."
---

## 개요

다익스트라는 단일 출발점 최단경로 알고리즘이다. 음수 간선이 없을 때 사용한다.

## 구현

```cpp
#include <bits/stdc++.h>
using namespace std;

typedef pair<int,int> pii;
const int INF = 1e9;

vector<pii> graph[100001];
int dist[100001];

void dijkstra(int start) {
    priority_queue<pii, vector<pii>, greater<pii>> pq;
    fill(dist, dist + 100001, INF);
    dist[start] = 0;
    pq.push({0, start});

    while (!pq.empty()) {
        auto [d, u] = pq.top(); pq.pop();
        if (d > dist[u]) continue;
        for (auto [w, v] : graph[u]) {
            if (dist[u] + w < dist[v]) {
                dist[v] = dist[u] + w;
                pq.push({dist[v], v});
            }
        }
    }
}
```

## 시간복잡도

O((V + E) log V)
