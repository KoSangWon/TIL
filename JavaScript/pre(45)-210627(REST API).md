# REST API
- REST(Representational State Transfer)는 HTTP/1.0과 1.1의 스펙 작성에 참여했고 아파치 HTTP 서버 프로젝트의 공동 설립자인 로이 필딩(Roy Fielding)의 2000년 논문에서 처음 소개되었다. 발표 당시 웹이 HTTP를 제대로 사용하지 못하는 상황을 보고 HTTP의 장점을 최대한 활용할 수 있는 아키텍처로서 REST를 소개했고 이는 HTTP 프로토콜을 의도에 맞게 디자인하도록 유도하고 있다. REST의 기본 원칙을 성실히 지킨 서비스 디자인을 "RESTful"이라고 표현한다.

- 즉, REST는 HTTP를 기반으로 클라이언트가 서버의 리소스에 접근하는 방식을 규정한 아키텍처고, REST API는 REST를 기반으로 서비스 API를 구현한 것을 의미한다.

## 1. REST API의 구성
- REST API는 자원(resource), 행위(verb), 표현(representations)의 3가지 요소로 구성된다. REST는 자체 표현 구조(self-descriptiveness)로 구성되어 REST API만으로 HTTP 요청의 내용을 이해할 수 있다.
<table>
  <thead>
    <tr>
      <th style="text-align: left">구성 요소</th>
      <th style="text-align: left">내용</th>
      <th style="text-align: left">표현 방법</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align: left">자원(resource)</td>
      <td style="text-align: left">자원</td>
      <td style="text-align: left">URI(엔드 포인트)</td>
    </tr>
    <tr>
      <td style="text-align: left">행위(verb)</td>
      <td style="text-align: left">자원에 대한 행위</td>
      <td style="text-align: left">HTTP 요청 메서드</td>
    </tr>
    <tr>
      <td style="text-align: left">표현(representations)</td>
      <td style="text-align: left">자원에 대한 행위의 구체적 내용</td>
      <td style="text-align: left">페이로드</td>
    </tr>
  </tbody>
</table>

## 2. REST API 설계 원칙
- REST에서 가장 중요한 기본적인 원칙은 두 가지다. **URI는 리소스를 표현**하는 데 집중하고 **행위에 대한 정의는 HTTP 요청 메서드**를 통해 하는 것이 Restful API를 설계하는 중심 규칙이다.

### 1. URI는 리소스를 표현해야 한다.
- URI는 리소스를 표현하는데 중점을 두어야 한다. 리소스를 식별할 수 있는 이름은 동사보다는 명사를 사용한다. 따라서 이름에 get 같은 행위에 대한 표현이 들어가서는 안 된다.
```
# bad
GET /getTodos/1
GET /todos/show/1

# good
GET /todos/1
```

### 2. 리소스에 대한 행위는 HTTP 요청 메서드로 표현한다.
- HTTP 요청 메서드는 클라이언트가 서버에게 요청의 종류와 목적(리소스에 대한 행위)을 알리는 방법이다. 주로 5가지 요청 메서드(GET, POST, PUT, PATCH, DELETE 등)를 사용하여 CRUD를 구현한다.

<table>
  <thead>
    <tr>
      <th style="text-align: left">HTTP 요청 메서드</th>
      <th style="text-align: left">종류</th>
      <th style="text-align: left">목적</th>
      <th style="text-align: center">페이로드</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align: left">GET</td>
      <td style="text-align: left">index/retrieve</td>
      <td style="text-align: left">모든/특정 리소스 취득</td>
      <td style="text-align: center">x</td>
    </tr>
    <tr>
      <td style="text-align: left">POST</td>
      <td style="text-align: left">create</td>
      <td style="text-align: left">리소스 생성</td>
      <td style="text-align: center">○</td>
    </tr>
    <tr>
      <td style="text-align: left">PUT</td>
      <td style="text-align: left">replace</td>
      <td style="text-align: left">리소스의 전체 교체</td>
      <td style="text-align: center">○</td>
    </tr>
    <tr>
      <td style="text-align: left">PATCH</td>
      <td style="text-align: left">update</td>
      <td style="text-align: left">리소스의 일부 수정</td>
      <td style="text-align: center">○</td>
    </tr>
    <tr>
      <td style="text-align: left">DELETE</td>
      <td style="text-align: left">delete</td>
      <td style="text-align: left">모든/특정 리소스 삭제</td>
      <td style="text-align: center">x</td>
    </tr>
  </tbody>
</table>

- 리소스에 대한 행위는 HTTP 요청 메서드를 통해 표현하며 URI에 표현하지 않는다. 예를 들어, 리소스를 취득하는 경우에는 GET, 리소스를 삭제하는 경우에는 DELETE를 사용하여 리소스에 대한 행위를 명확히 표현한다.
```
# bad
GET /todos/delete/1

# good
DELETE /todos/1
```
