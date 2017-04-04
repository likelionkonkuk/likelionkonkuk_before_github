건국대학교 멋쟁이사자처럼 5기 깃헙페이지 😎
---
[![멋쟁이사자처럼 건대](https://img.shields.io/badge/likelion-Konkuk Univ Facebook-blue.svg)](https://www.facebook.com/likelionkonkuk)

- jekyll [shiori theme](https://github.com/ellekasai/shiori)

### 포스트 분류
- 포스트는 크게 `notice`, `homework`, `challenge` 3종류로 나뉜다. 
    - notice : 공지사항 및 기타 전달사항. (tag: notice, author: "건대멋사")
    - homework : 과제. (tag: homework, author: "수업진행자", until: 마감일(yy-mm-dd))
    - challenge : 수업 중 첼린지. (tag: notice, author: "수업진행자", winner: "승리팀", mvp: "홍길동")

### 작성방법 📝
- `_post` 디렉토리에 `markdown`으로 문서작성
- 문서명은 `년-월-일-tag-문서명` 으로함.(예: 2017-03-30-notice-5thnetworking.md)
- 문서 내용 상,하단에 문서 정보를 기재한다.
- 문서내에 사진 및 기타 소스가 있을경우 `assets` 디렉토리에 해당문서의 항목에 맞는 디렉토리에 넣는다. (예: assets/challenge/w1-orginal.png)
- 단, 공지사항에 포함된 소스일경우 별도의 디렉토리를 구분하지 않고, `assets` 디렉토리에 넣는다.

#### 상단 🔼
```
title: "(예)1주차 과제 : 쳌마~프로퐐!" //제목
tag: homework //과제:homework, 공지:notice
author: "천민우" //작성자
until: 2017-04-05 //과제일 경우
```

#### 하단 🔽
```
---

## Author

written by [천민우](https:본인깃헙url).

![](https://avatars.githubusercontent.com/아이디?v=2&s=100)

<a href="https://깃헙url" target="_blank" class="btn btn-black"><i class="fa fa-github fa-lg"></i> Visit on Github Page &rarr;</a>
```

### 첼린지 👾
- 1주차 퍼즐 : MVP 김현경(미연팀) / 승리팀 다혜팀
- 2주차 미연이의 성적표 : MVP 김지훈(다혜팀) / 승리팀 다혜팀
- 3주차 로또 : MVP 송지연(다혜팀) / 승리팀 다혜팀
