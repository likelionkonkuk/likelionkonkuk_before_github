---
title: "(중요)과제 제출방법"
tag: notice
author: "건대멋사"
---

건대멋사는 협업툴의 원활한 사용을 위해 `git`을 통하여 과제를 다운로드(`clone`, `pull`) 업로드(`push`)합니다. 내용을 충분히 숙지한 뒤 과제를 제출해 주세요!


### 과제 제출방법
- 주어진 다운로드 링크에 들어가 `git`을 사용하거나, `zip`파일로 다운로드 합니다.

```
git clone https://github.com/likelionkonkuk/example.git
```

- __중요__ 과제를 받으면 자신의 이름을 `branch`로 추가, `checkout`으로 자신의 이름으로 전환한 뒤 과제를 수행합니다.(최초에는 `branch`가 `master`로 설정되어 있습니다. __절대로__ `master branch`로 과제를 수행하지 않도록합니다.)

```
git branch minwoo #branch를 추가한 뒤
git checkout minwoo #자신의 이름으로 전환
```

- 과제를 수행할때 유의사항 및 참고자료를 최대한 활용합니다.
- 과제를 수행하면서 어려운부분은 주석으로 표시하고, 그부분에 대한 내용을 튜터가 한번에 확인할수 있도록 `REAME.md`에 남기세요.

```
(예를들어 html일 경우 )
<!--1-->
<!-- 어려웠던 내용이나 이유 -->
<div>어려운부분</div>
<!--1 end-->
```

커밋직후 메시지를 수정할수 있습니다. `source tree`를 사용하면 더욱 쉽게 할 수 있습니다. 어려운 부분 뿐만아니라 과제를 수행하면서 느낌점을 함께 써줘도 좋습니다.

```
git commit -m "천민우 #3"
git commit --amend #vi를 사용해 commit메시지를 수정할수 있다. 어렵다면 source tree를 사용하는게 좋다.
```

![]({{ site.url }}/assets/homework/howto-1.png)

- 마지막으로 `push` 합니다. (절대로 `master branch`에 `push`하거나 `merge`하지 않습니다.)
- 과제 제출기한을 엄수하세요.(벌금과 더불어 튜터의 comment`를 받을수 없습니다.)
- 매주 과제발표를 합니다. ppt는 필요없습니다. 과제를 수행하는 과정을 상세히 `README.md` 파일에 작성하고, 그 파일로 발표 합니다.
- 코드리뷰 및 크리틱을 거친뒤 __우수과제__를 선정합니다.

---

### 참고자료
- [git 간편안내서](https://rogerdudler.github.io/git-guide/index.ko.html)
- [과제제출 예시](https://github.com/project42da/git-example)

---

## Author

written by [건대멋사](likelionkonkuk.github.io).

![](https://avatars.githubusercontent.com/likelionkonkuk?v=2&s=100)

<a href="https://github.com/likelionkonkuk" target="_blank" class="btn btn-black"><i class="fa fa-github fa-lg"></i> Visit on Github &rarr;</a>
