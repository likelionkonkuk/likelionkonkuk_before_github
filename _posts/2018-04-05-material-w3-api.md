---
title: "3주차 보조자료(API, JSON)"
tag: material
author: "정다혜"
---

### 1. 사용자를 위한 인터열이스 (UI : User Interface)

[로또 페이지 바로가기](http://www.nlotto.co.kr/common.do?method=main )

- 이 화면을 통해 우리(사용자)는 이번 주 로또에 대한 데이터를 얻을 수 있다.
- 하지만 우리는 프로그램에서 이번 주 로또에 대한 데이터를 사용하고 싶다!
- 컴퓨터는 멍청해서, 사람처럼 이 화면을 통해 데이터를 얻지 못한다.

### 2. 프로그램을 위한 인터페이스 (API : Application Programming Interface)

[로또 API 페이지](http://www.nlotto.co.kr/common.do?method=getLottoNumber&drwNo= )

- 사람에게는 전혀 도움이 안되는 페이지를 왜 제공하는 것일까?
- 바로 우리같은 개발자가, 프로그램에서 로또 데이터를 사용할 수 있도록 하기 위해.
- 주소(http://www.nlotto.co.kr/common.do?method=getLottoNumber&drwNo=) 맨 끝에 &drwNo= 뒤에 아무 값도 넣지 않으면 가장 최근의 로또 당첨 정보를, 얻고자 하는 회차를 넣으면 해당 회차의 정보를 제공한다.

### API 데이터 분석

사이트가 제공하는 데이터는 **JSON**(JavaScript Object Notation) 형식이다.

```json
{
  "bnusNo":10,
  "firstWinamnt":2608641000,
  "totSellamnt":73436852000,
  "returnValue":"success",
  "drwtNo3":21,
  "drwtNo2":19,
  "drwtNo1":15,
  "drwtNo6":44,
  "drwtNo5":41,
  "drwtNo4":34,
  "drwNoDate":"2017-02-25",
  "drwNo":743,
  "firstPrzwnerCo":7
}
```

#### JSON이란?
자바스크립트를 위한 것으로 객체 형식으로 자료를 표현한다. 단순히 데이터를 표현하는 방법이다. 데이터를 받아서 객체나 변수로 표현하기 위해서 사용하는 것이다.

* [JSON 공식 페이지](http://json.org/json-ko.html)
* [위키피디아](https://ko.wikipedia.org/wiki/JSON)

이 JSON파일을 Hash로 변환해서 사용할 것이다.

```erb
require ('open-uri')        # 웹 페이지 open 에 필요.
require ('json')            # JSON을 Hash로 변환하는데 필요.
```

자세한 내용은 challenge파일 내부에 주석으로 쓰여 있습니다.

## Author

written by [정다혜](https://dh00023.github.io).

![](https://avatars.githubusercontent.com/dh00023?v=2&s=100)

<a href="https://dh00023.github.io" target="_blank" class="btn btn-black"><i class="fa fa-github fa-lg"></i> Visit on Github Page &rarr;</a>