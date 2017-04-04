---
title: "3주차 보조자료(RESTful)"
tag: material
author: "정다혜"
---

## RESTful

### 1. HTTP란 무엇인가?
* **HTTP**란 **H**yper**T**ext **T**ransport **P**rotocol의 약자로 웹서버와 클라이언트간의 문서를 교환하기 위해 사용되는 프로토콜이다.

* World Wide Web( WWW )의 분산되어 있는 Server와 Client 간에 Hypertext를 이용한 정보교환이 가능하도록 하는 통신 규약이다.
 	> **하이퍼텍스트**는 문서 중간중간에 특정 키워드를 두고 문자나 그림을 상호 유기적으로 결합하여 연결시킴으로써, 서로 다른 문서라 할지라도 하나의 문서인 것처럼 보이면서 참조하기 쉽도록 하는 방식을 의미한다.

	> 인터넷 주소를 지정할 때 'http://www....' 와 같이 하는 것은 www로 시작되는 인터넷 주소에서 하이퍼텍스트 문서의 교환을 http 통신규약으로 처리하라는 뜻이다.

* http의 첫번째 버전은 인터넷을 통하여 가공되지 않은 데이터를 전송하기 위한 단순한 프로토콜이었으나, 데이터에 대한 전송과 요구·응답에 대한 수정 등 가공된 정보를 포함하는 프로토콜로 개선되었다.

### 2. HTTP method에는 어떤것이 있고 왜 있는가?

#### GET
 1. URL에 해당하는 자료의 전송을 요청한다.
 2. 데이터가 URL에 노출된다.
 3. 인코딩/디코딩의 과정이 없기 때문에 POST보다 빠르다.
 4. URL의 길이 제약으로 인해 많은 데이터 전송은 무리이다.

#### POST
 1. 서버가 처리할 수 있는 자료를 보낸다.
 2. 데이터는 HTTP Boby에 숨겨서 서버로 전송한다.
 3. GET으로 보낼수 없는 자료를 전송할때 사용 가능하다.

#### PUT
 1. 해당 URL에 자료를 저장한다.(POST와 유사한 전송 구조를 가지기 때문에 헤더 이외에 메시지(데이터)가 함께 전송된다.)
 2. 원격지 서버에 지정한 콘텐츠를 저장하기 위해 사용되며 홈페이지 변조에 많이 악용되고 있다. 

#### DELETE
 1. 해당 URL의 자료를 삭제한다.


### 3. RESTful 이란 무엇인가.
**RE**presentational **S**tate **T**ransfer의 약자로 장비간 통신을 위해 CORBA, RPC, SOAP등의 복잡한 방법을 사용하는 대신, 간단하게 HTTP를 이용하는 것이 목적이다.

HTTP URI를 통해 Resource를 명시하고, HTTP Method(Post, Get, Put, Delete)를 통해 해당 Resource에 대한 CRUD Operation을 적용한다. 즉, REST는 ROA(Resource Oriented Architecture) 설계의 중심에 Resource가 있고 HTTP Method를 통해 Resource를 처리하도록 설계된 아키텍쳐를 의미한다.

#### REST의 장점

- OPENAPI를 제공하기 쉽다.
- 멀티플랫폼 지원 및 연동이 용이하다.
- 원하는 타입으로 데이터를 주고받을수 있따. (XML, JSON, RSS )
- 기존 웹 인프라를(HTTP)를 그대로 사용가능하다 ( 방화벽, 장비 요건 불필요 )
- 사용하기 쉽다
- 세션을 사용하지 않는다. 각각의 요청에 독립적.

#### REST의 단점

- 표준이 없어서 관리가 어렵다.
- 사용할 수 있는 메소드가 4가지 밖에 없다.
- 분산환경에는 부적합하다.
- HTTP통신 모델에 대해서만 지원한다.

#### REST의 특징

- 클라이언트/서버 구조 : 일관적으로 독립되어야 한다.
- 무상태(Stateless) : 각요청 간 클라이언트의 Context는 서버에 저장되어서는 안 된다.
- 캐시가능(Cacheable) : WWW에서와 같이 클라이언트는 응답을 Caching 할 수 있어야 한다.
- 계층화(Layered System) : 클라이언트는 보통 대상 서버에 직접 연결 또는 중간 서버를 통해 연결되는지 모른다.
- Code on demand(option) : 자바 애플릿/ 자바스크립의 제공으로 서버가 클라이언트가 실행   시킬 수 있는 로직을 전송하여, 기능을 확장 할수 있다.
- 인터페이스 일관성 : 아키텍처를 단순화하고, 작은 단위로 분리하여, 클라이언트-서버 파트    별로 독립적으로 개선 될 수 있도록 한다.
- 자체 표현구조(Self-Descriptiveness) : API 메시지만 보고도 어떤 API인지를 이해 할수 있는 자체 표현 구조를 가진다.

---

## Author

written by [정다혜](https://dh00023.github.io).

![](https://avatars.githubusercontent.com/dh00023?v=2&s=100)

<a href="https://dh00023.github.io" target="_blank" class="btn btn-black"><i class="fa fa-github fa-lg"></i> Visit on Github Page &rarr;</a>