---
layout: post
title: Electron - Sentry 연동 후 페이지 멈춤
date: 2022-06-29 20:47:49 +0900
categories: Electron
---

얼마 전 진행하던 프로젝트에 Sentry 연동 후 페이지가 아예 멈춰버리는 버그가 발생했다. 🤦‍♀️
<br>

콘솔창도 멈춰버려서 무슨 문젠지 알 수 없던 찰나에 찬찬히 Sentry를 뗐다 붙였다 하던 중 문제를 찾았다..ㅜㅜ

**DOM에 접근하는 `console.log` 가 문제였다.**

`console.log(ref.current)`만 지워주니 해결됐다.

정확한 원인은 모르겠지만 Sentry 연동 후 console.log를 찍으면 `instrument.ts` 로 뜨는데 이것과 연관있지 않은가 생각하고있다.

<br /><br />
📌 추가로 console.log에 instrument.ts가 뜬다면

크롬 개발자 도구 설정에서
`/@sentry/` , `instrument.ts` 를 추가해주면 된다.

![image](https://user-images.githubusercontent.com/78190786/176440424-445c2fb9-22ca-41c7-877c-1b143bbe4d6d.png)

**참조**

<https://github.com/getsentry/sentry-react-native/issues/794>
