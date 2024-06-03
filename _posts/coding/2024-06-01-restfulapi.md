---
layout: post
title: Restful API
date: 2024-06-01 16:39 +0900
description: Restful API에 대해 알아보기
image: ../assets/img/restfulapi.jpg
category: ETC
tags: RestfulAPI
published: true
sitemap: true
---

### 1. RESTful API(Representational State Transferful Application Programming Interface)란?

▶ RESTful API는 REST 원칙을 따르는 API를 의미합니다. RESTful API는 클라이언트와 서버 간의 통신을 위해 HTTP를 사용하며, 웹 서비스 설계의 기본 원칙을 준수합니다. RESTful API는 간단하고 확장 가능한 시스템을 구축하는 데 적합하고 웹 서비스의 설계 및 구현에서 널리 사용되는데 오늘은 이러한 RESTful API에 대해 한번 알아보도록 하겠습니다.

### 2. RESTful API의 핵심 원칙

1. 리소스 식별 (Resource Identification)
: 리소스는 URI(Uniform Resource Identifier)로 고유한 식별을 가지게 됩니다. 예를 들어, 특정 사용자의 정보가 /users/{userId}와 같은 URI를 통해 접근할 수 있다고 할 때 이 URI는 리소스를 명확하게 식별하며, 클라이언트는 이 URI를 사용하여 서버와 상호 작용합니다.

2. 리소스의 표현 (Resource Representation)
: 리소스는 JSON, XML, HTML 등 다양한 포맷으로 표현될 수 있으며, 일반적으로 RESTful API는 가볍고 읽기 쉬운 JSON 형식을 주로 사용합니다. 이 때, 클라이언트는 서버로부터 리소스를 요청할 때 원하는 표현 형식을 지정할 수 있습니다.

3. 상태 없는 상호 작용 (Stateless Interactions)
: 모든 요청은 독립적이며 서버는 각 요청을 완전히 이해하기 위해 필요한 모든 정보를 요청에 포함해야 합니다. 이는 클라이언트와 서버 간의 통신을 단순화하고 확장성을 높입니다.

4. 표준 HTTP 메서드 사용 (Use of Standard HTTP Methods)
: RESTful API는 CRUD(Create, Read, Update, Delete) 작업을 수행하기 위해 HTTP 메서드를 사용하는데 해당 메서드는 아래와 같습니다.
- GET: 리소스를 **조회**합니다.
- POST: 새로운 리소스를 **생성**합니다.
- PUT: 기존 리소스 **전체를 업데이트**합니다.
- PATCH: 기존 리소스 **일부를 업데이트**합니다.
- DELETE: 리소스를 **삭제**합니다.

5. 자기 설명적 메시지 (Self-descriptive Messages)
: 요청 및 응답 메시지는 자체적으로 이해할 수 있어야 합니다. 즉, 메시지에는 필요한 모든 메타데이터가 포함되어 있어야 하며, 이를 통해 클라이언트와 서버는 상호 작용을 이해할 수 있습니다.

6. HATEOAS(Hypermedia As The Engine Of Application State)
: 클라이언트는 서버로부터 받은 응답 내의 하이퍼링크를 통해 애플리케이션의 상태를 전이할 수 있습니다. 이는 클라이언트가 애플리케이션의 다른 부분으로 이동할 수 있도록 하는 링크를 제공하여 API의 사용성을 높입니다.

### 3. RESTful API의 장점

1. 단순성
: RESTful API는 HTTP 프로토콜을 기반으로 하여 웹 표준을 따르기 때문에 개발자들이 쉽게 이해하고 사용할 수 있도록 해줍니다.

2. 확장성
: 클라이언트와 서버 간의 역할 분리로 인해 시스템 확장성이 높습니다. 이를 통해 서버는 클라이언트와 독립적으로 개발 및 배포될 수 있습니다.

3. 유연성
: RESTful API는 다양한 데이터 형식을 지원하며 JSON, XML 등 원하는 형식으로 데이터를 주고받을 수 있습니다.

4. 가독성
: RESTful API는 명확하고 일관된 URI 구조를 가지고 있어 가독성이 높습니다. 이는 사용자가 API 사용법을 쉽게 이해할 수 있도록 합니다.

5. 캐시 가능성
: HTTP 캐시 메커니즘을 통해 응답을 캐시할 수 있습니다. 이는 성능을 최적화하고 서버 부하를 줄이는 데 도움이 됩니다.

### 4. RESTful API의 단점

1. 복잡한 요청 처리
: 특정 작업을 수행하기 위해 여러 요청이 필요할 수 있으며, 이는 클라이언트와 서버 간의 상호 작용을 복잡하게 만들 수 있습니다.

2. 표준의 모호성
: REST는 소프트웨어 스타일 중 하나로, 명확한 구현 표준이 없습니다. 이는 개발자마다 다른 방식으로 구현될 수 있어 일관성을 유지하기 어려울 수 있습니다.

3. 데이터 과잉 전송
: 필요한 데이터만 전송하기 어렵기 때문에 불필요한 데이터가 포함될 수 있습니다. 이는 네트워크 사용량을 증가시키고 성능에 영향을 미칠 수 있습니다.

### 5. RESTful API의 사용 예시

##### (1) 블로그 포스트 조회 - GET 사용

- 모든 블로그 포스트 조회

````bash
GET /posts
````

- 모든 블로그 포스트 조회에 대한 응답처리

````json
[
  {
    "id": 1,
    "title": "RESTful API의 이해",
    "content": "RESTful API는..."
  },
  {
    "id": 2,
    "title": "HTTP 메서드 활용",
    "content": "HTTP 메서드는..."
  }
]
````

- 특정 블로그 포스트 조회

````bash
GET /posts/1
````

- 특정 블로그 포스트 조회에 대한 응답 처리

````json
{
  "id": 1,
  "title": "RESTful API의 이해",
  "content": "RESTful API는..."
}
````

##### (2) 새로운 블로그 포스트 작성 - POST 사용

- 새로운 블로그 작성 시

````bash
POST /posts
Content-Type: application/json

{
  "title": "새로운 블로그 포스트",
  "content": "이것은 새로운 블로그 포스트의 내용입니다."
}
````

- 새로운 블로그 작성에 대한 응답 처리

````bash
HTTP/1.1 201 Created
Location: /posts/3
````

<br>

이렇게 오늘은 RESTful API에 대해 알아봤는데요,<br>
헷갈리기 쉬운 개념인만큼 면접에서도 충분히 나올 수 있는 질문이기 때문에 미리 공부해두면 좋을 것 같네요!
그렇다면 저는 다음에 또다른 면접에 대비한 내용을 들고오도록 하겠습니다 😁!