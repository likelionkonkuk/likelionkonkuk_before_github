---
title: "1주차 금요 수업자료 (jQuery)"
tag: material
author: "천민우"
---

[다운로드링크](https://github.com/likelionkonkuk/w1_fri_material)

- 다운받아 사용하세요.
- jQuery를 사용해서 간단하게 **Navigation Bar Toggle**을 구현해보자.

```js
    $('#menu').on('click',function(e){
      $('#drawer').addClass("open");
      e.stopPropagation();
    });

    $('main').on('click',function(e){
      $('#drawer').removeClass("open");
    });
```


#### 참고자료
- [제이쿼리](http://jquery.com/)
- [경로](http://www.homejjang.com/03/html.php/img_path.php)

---

## Author

written by [천민우](https://project42da.github.io).

![](https://avatars.githubusercontent.com/project42da?v=2&s=100)

<a href="https://project42da.github.io" target="_blank" class="btn btn-black"><i class="fa fa-github fa-lg"></i> Visit on Github Page &rarr;</a>