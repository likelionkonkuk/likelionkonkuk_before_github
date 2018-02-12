---
title: "1주차 보조자료 (jQuery Helper)"
tag: material
author: "천민우"
---

[다운로드링크](https://github.com/likelionkonkuk/w1_jqueryHelper)

`jquery`를 이용해서 동적으로 `DOM`을 제어할 수 있다. `html`을 사용하여 입력했던 부분을 jquery로 대체하자.

#### 코드설명

- 다운받아 사용하세요.
- `model`에 프로필정보를 입력한다.
- `controller`로 입력한 정보를 출력한다.
- 필요에 따라 `HTML변수명`으로 `html`태그를 추가할 수 있다.
- 추가한 `html`
- 태그는 `model`의 `display`내에 **jquery selector**를 통해서 `append`, `prepend`할수 있다.

#### 참고사항
- `jquery`, `js` 코드이긴 하지만, 해당언어를 전혀 몰라도 충분히 사용할 수 있다.
- `controller`부분은 수정하지 않는다.
- 반드시 `jquery`를 불러온 이후에 코드를 불러온다.
```html
  <!-- jquery먼저 -->
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
  <!-- helper.js -->
  <script src="helper.js"></script>
```
- `index.html`(예시파일)을 참고하자.


#### Author

written by [천민우](https://project42da.github.io).

![](https://avatars.githubusercontent.com/project42da?v=2&s=100)