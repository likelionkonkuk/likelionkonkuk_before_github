---
title: "5주차 첼린지 : 성인용SNS"
tag: challenge
author: "천민우"
winner: ""
mvp: ""
---



성인용 SNS의 데이터베이스를 설계해 보자.
사용자 정보에는 한장의 이미지(image), 이름(name), 이메일(email), 나이(age) 등이 있다. 사용자는 다수의 게시물(post)를 작성할수 있고,
게시물에는 다수의 사진(photo), 게시물의 제목(title), 게시물의 내용(content)이 필요하다. 
사용자들은 게시물에 다수의 댓글(comment)을 작성할수 있다.

---

### 조건

- 사용자의 이름은 20자까지 가능하다.
- 사용자의 이메일은 반드시 이메일 형식을 갖춰야 한다.
- 19세 이하의 사용자는 가입할수 없다.
- 댓글에는 욕설(fuck,shit,bitch)가 들어가서는 안된다.
- 댓글의 길이는 100자 이내이다.)
- 지금 이 SNS에는 40명의 사용자(20대 20명, 30대 10명, 40대 5명, 50대 5명)가 가입한 상태다.
- 50대 회원은 1인당 1개의 게시물을 작성했고, 40대는 1번과 2번 게시물에만 1인당 1개의 댓글을 달았다.

### 유의사항

- 모든내용은 `task`를 사용하여 입력하시오.
- 설계한 내용을 `README.md`에 작성하시오.
- 전원이 성공해야 끝나는 첼린지 입니다.
- 전원이 **15분내**에 설계와 `README.md` 작성을 끝내면 전원에게 상점부여.
---

### 참고자료
- [Rails Active Record](http://guides.rubyonrails.org/association_basics.html)
- [Rails Active Record Validations](http://guides.rubyonrails.org/active_record_validations.html)
- [Faker](https://github.com/stympy/faker)

---

## Author

written by [천민우](https://project42da.github.io).

![](https://avatars.githubusercontent.com/project42da?v=2&s=100)

<a href="https://project42da.github.io" target="_blank" class="btn btn-black"
