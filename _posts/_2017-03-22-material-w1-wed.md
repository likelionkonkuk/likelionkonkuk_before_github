---
title: "1주차 수요일 수업자료 (Display Flex)"
tag: material
author: "천민우"
---
#### DOM(Document Object Model)
![]({{ site.url }}/assets/material/w1_wed/DOM.png)

#### CSSOM(CSS Object Model)
![]({{ site.url }}/assets/material/w1_wed/CSSOM.png)

#### 브라우저 랜더링
![]({{ site.url }}/assets/material/w1_wed/CRP.png)

1. HTML 마크업을 처리하고 DOM 트리를 빌드합니다.
2. CSS 마크업을 처리하고 CSSOM 트리를 빌드합니다.
3. DOM 및 CSSOM을 결합하여 렌더링 트리를 형성합니다.
4. 렌더링 트리에서 레이아웃을 실행하여 각 노드의 기하학적 형태를 계산합니다.
5. 개별 노드를 화면에 페인트합니다.

---

#### Bootstrap & Display : flex

[다운로드링크](https://github.com/likelionkonkuk/w1_web_material)

**display:flex** 속성 적용하는 젤 간단한 방법
```css
/*부모선택자*/
.flexWrap{
  display: flex; 
  flex-wrap: wrap;
}
/*자식선택자*/
.child{
  order:1;
}
```



---

### 참고자료
- [CSS-Trigger](https://csstriggers.com)
- [CSS-TRICK](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [Bootstrap](http://getbootstrap.com/)
- [Udacity](https://www.youtube.com/watch?v=Buz0kFWQWjw)
- [Critical rendering path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-tree-construction)
- [Responsive Web Design Basic](https://developers.google.com/web/fundamentals/design-and-ui/responsive/)


---

## Author

written by [천민우](https://project42da.github.io).

![](https://avatars.githubusercontent.com/project42da?v=2&s=100)

<a href="https://project42da.github.io" target="_blank" class="btn btn-black"><i class="fa fa-github fa-lg"></i> Visit on Github Page &rarr;</a>
