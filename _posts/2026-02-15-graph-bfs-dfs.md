---
layout: post
title: "BFS/DFS 구현 패턴 정리 및 활용"
date: 2026-02-15 00:00:00 +0900
categories: [알고리즘, 그래프]
tags: [BOJ]
cover_image: ""
excerpt: "BFS와 DFS 각각 언제 쓰는지, 그리고 실전에서 자주 쓰는 구현 패턴."
---

## BFS — 최단 거리

```cpp
queue<int> q;
vector<bool> visited(n+1, false);
q.push(start); visited[start] = true;
while (!q.empty()) {
    int u = q.front(); q.pop();
    for (int v : graph[u])
        if (!visited[v]) { visited[v]=true; dist[v]=dist[u]+1; q.push(v); }
}
```

## 선택 기준

- 최단 거리 → BFS
- 연결 요소, 사이클, 위상 정렬 → DFS
