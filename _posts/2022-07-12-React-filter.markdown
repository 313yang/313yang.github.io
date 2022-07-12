---
layout: post
title: React - 배열 차집합 비교
date: 2022-07-12 22:56:00 +0900
categories: React, javascript
---

전체회원 리스트에서 체크박스 선택된 회원만 그룹으로 묶고 선택되지 않은 회원만 그룹으로 나눠야했다.
그룹을 비교하는 과정에선 해당 회원의 `id`로 비교했다.

```js
👉 선택되지 않은 회원목록

const filterList = allList?.filter(
  (user) => !selectedList.some((selectedUser) => selectedUser.id === user.id)
);
```

추가로 메세지 수신인 추가하는 과정에서 이미 추가된 회원은 제외하고 전체 회원리스트에 추가해야하는 일이 생겼다.

```js
const filterList = allUserList
  .filter((user) => !addUserList.some((addUser) => addUser.id === user.id))
  .concat(addUserList);
```
