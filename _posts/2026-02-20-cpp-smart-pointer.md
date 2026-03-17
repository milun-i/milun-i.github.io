---
layout: post
title: "C++ 스마트 포인터 — unique_ptr, shared_ptr, weak_ptr"
date: 2026-02-20 00:00:00 +0900
categories: [컴퓨터공학, C++]
tags: [수업과제]
cover_image: ""
excerpt: "raw pointer 대신 스마트 포인터를 써야 하는 이유와 세 가지 종류의 차이점."
---

## 왜 스마트 포인터인가

`new`/`delete`를 직접 쓰면 예외 발생 시 메모리 누수가 생길 수 있다.

## unique_ptr

```cpp
auto p = std::make_unique<MyClass>(args);
```

## shared_ptr

```cpp
auto p1 = std::make_shared<MyClass>();
auto p2 = p1; // 카운트 2
```

## weak_ptr

shared_ptr의 순환 참조 문제를 해결하기 위한 약한 참조.
