---
layout: post
title: "fork(), exec(), wait() — 프로세스 생성의 흐름 정리"
date: 2026-02-25 00:00:00 +0900
categories: [컴퓨터공학, 시스템프로그래밍]
tags: [수업과제]
cover_image: ""
excerpt: "수업 과제 중 헷갈렸던 부분들. zombie process와 orphan process 차이까지."
---

## fork()

현재 프로세스를 복사한다. 반환값으로 부모/자식을 구분한다.

```c
pid_t pid = fork();
if (pid == 0) {
    // 자식 프로세스
} else if (pid > 0) {
    // 부모 프로세스
}
```

## Zombie vs Orphan

| | zombie | orphan |
|---|---|---|
| 원인 | 자식 종료 후 부모가 wait() 안 함 | 부모가 먼저 종료 |
| 처리 | 부모가 wait()로 회수 | init(PID 1)이 입양 |
