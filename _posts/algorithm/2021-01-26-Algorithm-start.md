---
layout: post
title: boj_14500 테트로미노
categories: Algorithm
tags:
  - algorithm
  - boj
  - dfs
hero: "https://source.unsplash.com/collection/261936/"
overlay: purple
published: true
---

# <center>boj_14500 테트로미노</center>

---

## 문제

폴리오미노란 크기가 1×1인 정사각형을 여러 개 이어서 붙인 도형이며, 다음과 같은 조건을 만족해야 한다.

정사각형은 서로 겹치면 안 된다.
도형은 모두 연결되어 있어야 한다.
정사각형의 변끼리 연결되어 있어야 한다. 즉, 꼭짓점과 꼭짓점만 맞닿아 있으면 안 된다.
정사각형 4개를 이어 붙인 폴리오미노는 테트로미노라고 하며, 다음과 같은 5가지가 있다.

![tetromino](https://onlinejudgeimages.s3-ap-northeast-1.amazonaws.com/problem/14500/1.png)

아름이는 크기가 N×M인 종이 위에 테트로미노 하나를 놓으려고 한다. 종이는 1×1 크기의 칸으로 나누어져 있으며, 각각의 칸에는 정수가 하나 쓰여 있다.

테트로미노 하나를 적절히 놓아서 테트로미노가 놓인 칸에 쓰여 있는 수들의 합을 최대로 하는 프로그램을 작성하시오.

테트로미노는 반드시 한 정사각형이 정확히 하나의 칸을 포함하도록 놓아야 하며, 회전이나 대칭을 시켜도 된다.

## 입력

첫째 줄에 종이의 세로 크기 N과 가로 크기 M이 주어진다. (4 ≤ N, M ≤ 500)

둘째 줄부터 N개의 줄에 종이에 쓰여 있는 수가 주어진다. i번째 줄의 j번째 수는 위에서부터 i번째 칸, 왼쪽에서부터 j번째 칸에 쓰여 있는 수이다. 입력으로 주어지는 수는 1,000을 넘지 않는 자연수이다.

## 출력

첫째 줄에 테트로미노가 놓인 칸에 쓰인 수들의 합의 최댓값을 출력한다.

## 느낀 점

참 쉽지 않았다.

내 코드에 대한 자신감이 많이 떨어져 있던 것 같다.
전체적으로 우울감이 동반되는 바람에 논리성이 부족해졌다고 생각할 수 있었다.

처음부터 끝까지 머리써서 다시 푸니 괜찮았다.

## 풀이 코드

```js
const fs = require("fs");
const input = fs.readFileSync("/dev/stdin").toString().trim().split("\n");

const [N, M] = input
  .shift()
  .split(" ")
  .map((el) => parseInt(el));
const board = input.map((line) => line.split(" ").map((el) => parseInt(el)));

let max = 0;

let visited = new Array(N);
for (let i = 0; i < N; i++) {
  visited[i] = new Array(M);
}

let awesomeVisited = new Array(N);
for (let i = 0; i < N; i++) {
  awesomeVisited[i] = new Array(M);
}

for (let i = 0; i < N; i++) {
  for (let j = 0; j < M; j++) {
    dfs(0, 0, i, j);
  }
}

console.log(max);

function dfs(depth, answer, x, y) {
  if (depth === 4) {
    if (max < answer) {
      max = answer;
    }
    return;
  }

  let dx = [1, -1, 0, 0];
  let dy = [0, 0, 1, -1];

  answer += board[x][y];
  visited[x][y] = true;

  checkAwesomeShape(x, y);

  for (let i = 0; i < 4; i++) {
    const newX = x + dx[i];
    const newY = y + dy[i];
    if (isRange(newX, newY)) {
      if (visited[newX][newY]) continue;
      checkAwesomeShape(x, y);
      dfs(depth + 1, answer, newX, newY);
    }
  }
  answer -= board[x][y];
  visited[x][y] = false;
}

function isRange(x, y) {
  if (x >= 0 && y >= 0 && x < N && y < M) {
    return true;
  } else {
    return false;
  }
}

function checkAwesomeShape(x, y) {
  let upward;
  let downward;
  let right;
  let left;

  // 윗방향
  if (isRange(x, y + 1)) {
    upward = board[x][y + 1];
  }
  // 아랫방향
  if (isRange(x, y - 1)) {
    downward = board[x][y - 1];
  }
  // 오른쪽방향
  if (isRange(x + 1, y)) {
    right = board[x + 1][y];
  }
  // 왼쪽방향
  if (isRange(x - 1, y)) {
    left = board[x - 1][y];
  }

  if (upward && right && left) {
    const upwardShape = board[x][y] + upward + right + left;
    if (max < upwardShape) max = upwardShape;
  }

  if (upward && right && downward) {
    const rightShape = board[x][y] + upward + right + downward;
    if (max < rightShape) max = rightShape;
  }

  if (left && right && downward) {
    const downShape = board[x][y] + left + right + downward;
    if (max < downShape) max = downShape;
  }

  if (upward && left && downward) {
    const leftShape = board[x][y] + left + upward + downward;
    if (max < leftShape) max = leftShape;
  }
}
```
