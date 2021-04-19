
# HTML
## Internet Service
- Telnet - IRC
- e-mail - Archie
- Usenet - Gopher
- FTP - WWW(현재)

## WWW
- World Wide Web
- Who: "Tim" Berners-Lee가 만듦. 
- Why: Connect(멀리 떨어져있는 정보를 전부 연결해줌)


## WEB
- Back-End : Server, Database, Application Layer
- Front-End : Client, Web Browser, Presentation Layer

## FRONT_END(Web 기술의 설정값)
- HTML: 건강한 신체
- CSS: 근사한 스타일링
- JS: 스마트한 두뇌

## Web Standards
- World Wide Web Consortiums에서 만듦
- 제프리 젤드만의 웹표준 가이드(추천 도서)

## Web Accessibility(웹 접근성)
- `The power of the Web is in its universality, access by everyone regardless of disability is an essential aspect. -Tim Burners Lee-`
- 지하철에 계단과 경사로가 있다. 하지만 우리는 평소에 계단만 서비스한다. 누군가는 불편할 수 있다. 대부분 서비스가 마우스에만 의존하는 서비스이다. 장애인분들뿐만 아니더라도 캐리어를 든 사람들도 이용을 할 수 있다.
- "장애인에게 필요한 것은 줄기세포가 아니라 **현실적인 정보기술(IT)**"

### 장애에 대한 이해
- 시각 장애 - 전맹, 저시력
- 청각 장애
- 지체 장애 - 절단 및 지체기능 장애
- 뇌병변 장애

### 장애는
- 볼수 없는 것이 아니라 보는 방법이 다를 뿐
- 걸을 수 없는 것이 아니라 걷는 방법이 다를 뿐
- 말할 수 없는 것이 아니라 말하는 방법이 다를 뿐

### 환경에 대한 이해
- 다양한 Platform
- Cross Browsing
- SEO(Search Engine Optimization)
- 저사양 또는 저속회선

# HTML5 Markup
## HTML의 탄생
- HTML5가 탄생하기 이전까지 HTML의 최초버전은 1993년에, 최신 버전은 1999년에 발표 됨
- W3C가 XHTML1.0을 구체화 하기 위해 XHTML2.0 작업을 진행 중이었으나 하위 호환성에 치명적인 문제가 있었음
  - HTML5의 등장으로 웹표준이 이제 정착해가고 있지만 아직도 HTML 4.0.1이나 XHTML 1.0을 사용하는 경우도 있다.
  - 초기 HTML은 단순 텍스트 위주의 표현을 위하였지만 점차 발전을 통해 다양한 요소를 표현하고 디자인적인 태그들도 생겼고 IE에 독주로 ActiveX 사용등 특정 브라우저에서만 볼 수 있는 기술들이 생겨났다. 하지만 점점 다양한 플랫폼 ,다양한 브라우저 사용이 늘어나면서 웹 표준이 필요하게 되었다.
  웹 표준을 만들기 위해 HTML4.01, XHTML의 등장의 과정을 겪고 현재 HTML5가 탄생하였다. 웹 표준은 HTML에서는 구조만 짜고 디자인적인 표현요소는 CSS로 분리하였다.
  - XML
    - '사과'라는 단어를 쓰면 의미가 없다. `<과일>사과</과일>` 이라고 쓰면 과일이라는 의미를 가지게 된다. `<음식><과일>사과</과일><음식>`과 같이 조금 더 자세한 표현이 가능하다.
    - 이처럼 데이터를 주고받을 때 구분하기 쉽게 해준다.
    - 현재는 JSON으로 주고 받는 방식으로 바뀌었다.
    - 그래서 기존에 있었던 HTML 4.01을 XML 방식으로 재정의 한 것이 XHTML 1.0이다.
    - HTML 4.01 = XHTML 1.0 (소문자만 지원)(self closing해야한다.)(`<br>`은 안되고 `<br/>`하면 맞다.)(따라서 문서 타입에 따라 문법이 달라진다.)(https://docs.emmet.io/cheat-sheet/)
    - `<BODY>`, `<body>`, `<BoDy>` 처럼 대문자 소문자를 구분하지 않는 경우가 있다. 그렇게 되면 너무 형식이 자유롭게 되어 문제가 있다.
    - DTD(Document Type Definition)
      - Strict: 단어 뜻대로 웹 표준을 엄격하게 지키는 버전. center, font를 포함한 14가지 태그를 사용하지 않는다.
      - Transitional: 아직까지도 많이 쓰이며 프레임을 제외한 모든 태그 사용 가능
      - Frame-set: 프레임 관련 태그까지 모두 사용 가능

- https://validator.w3.org/ : html 문법 유효성 검사 사이트


- 2004년 애플, 모질라 재단, 오페라 소프트웨어가 공동으로 설립한 공개 그룹인 WHATWG(Web Hyprtext Application Echnology Working Group)가 W3C와 별개로 Web Application 1.0과 Web Forms 2.0을 만들어 냄.
- 2007년 3월 W3C가 공개적으로 XHTML 2.0의 실패를 인정한 후 새롭게 HTML을 개발하기로 결정하면서 WHATWG의 표준안을 대부분 수용하여 HTML5가 탄생하게 됨.


## XHTML4.01, XHTML1.0과 HTML5의 차이점
- 새롭게 등장한 콘텐츠 모델(Content Models)
  - 명확한 정보 구조 설계 및 구성을 위해 카테고리를 정의하여 각 요소별로 비슷한 성격을 가지고 있는 것끼리 그룹화하였는데, 이를 HTML5의 콘텐츠 모델(Content Models)이라고 함.
- 콘텐츠 모델의 카테고리(Category)
  - HTML5의 카테고리(Category)는 Sectioning Root, Metadata Content 등의 그룹이 있으며, 하나의 요소가 여러 그룹에 속해 있을 수 또 있고, 그렇지 않을 수도 있음
- **문법체크 항상 하자!!** 

## HTML5에 추가된 개념(카테고리, 컨텐츠 모델, 아웃라인 알고리즘)
- HTML4.01과의 차이점
  - HTML4: 인라인 요소와 블록요소로 구분하는 정도의 개념만 존재
  - HTML5: 요소별 카테고리를 정의하여 각 요소별로 비슷한 성격을 가지고 있는 것끼리 그룹화

### 카테고리
- 요소간의 관계를 좀 더 구체적이고 명확하게 정의하는 것
- Metadata 콘텐츠: 다른 컨텐츠의 표현과 행동을 설정, 문서와 문서의 관계를 정할때 사용
- Flow 콘텐츠: 웹페이지상 직접 표시되지 않는 일부 메타데이터를 제외하고, 거의 모든 요소들이 그룹에 속함
- Sectioning 콘텐츠: HTML5에 새롭게 추가된 요소, Heading과 Footer의 범위를 설정. 모든 Sectioning 컨텐츠는 Heading과 아웃라인을 가짐(`<article>`, `<section>`, `<nav>`, `<aside>`)
- Heading 콘텐츠: 섹션의 제목을 정의할 때 사용(`<h1>` ~ `<h6>`)
- Phrasing 콘텐츠: 문단에서 텍스트를 마크업할때 사용.
- Embedded 콘텐츠: 이미지, 비디오, 오디오 플래시 등 외부 콘텐츠를 문서내에 표현할 때 사용
- Interative 콘텐츠: 사용자가 값을 입력하거나 무언가를 선택하는 등의 상호작용하는 요소를 의미

### 콘텐츠 모델
- 어떤 요소에 어떤 컨텐츠를 포함해야하는지 또 어떤요소가 어떤요소를 포함 할 수 있는지를 정의한것.
- 컨텐츠 모델이라는 개념을 통해 자식 요소로 포함할 수 있는 카테고리에 제한을 두었으며, 역으로 자식 요소가 작성될 수 있는 카테고리에 제한을 두었는데, 이는 HTML5가 구조가 아닌 구성에 중점을 두었기 때문이다.
### 아웃라인 알고리즘(Outline Algorithm)
- HTML5에는 정보 구조를 명확히 할 수 있도록 '아웃라인 알고리즘'(Outline Algorithm)이라는 개념이 도입되었음
- 아웃라인 알고리즘은 웹 페이지의 정보 구조를 판별할 수 있는 개념으로, 책의 목차와 비슷
- HTML5에서 추가된 많은 요소들은 대부분 아웃라인 알고리즘과 관련이 있으며 그 중에서도 직접적으로 아웃라인을 구성하는 요소에는 헤딩 콘텐츠, 섹셔닝 콘텐츠 그리고 섹셔닝 루트 요소 등이 있음
  - heading에 따라 section이 구분된다.
- 초창기에 존재했지만, 명세서에서는 빠졌다. 하지만, 없는 것은 아니다. heading에 의해서 암묵적으로 만들어진다. 콘텐츠에 대한 헤딩을 적절하게 지정해야 한다.


## HTML5의 API
- HTML5의 커다란 변화 중 하나로는 다양한 API의 추가를 들 수 있으며 대표적으로 다음과 같은 API가 추가됨.
- Web Storage
- Web Workers
- Web Socket
- Notifications
- etc..

- HTML 문서는 요소(elememt)와 태그(tag) 그리고 콘텐츠로 구성되어 있으며, 요소는 HTML의 의미를 가지고 있어야 한다.
- 코딩 컨벤션을 가지는 것이 중요하다. (naver 코딩 컨벤션 예시: https://nuli.navercorp.com/data/convention/NHN_Coding_Conventions_for_Markup_Languages.pdf)

## `<head>`
- Encoding set은 항상 문서의 가장 먼저 선언되어야 한다. title보다 먼저 선언될 것.
- http-equiv(equivalent): 문서의 초기정보를 나타내는 속성이다. 이 속성을 지정하면 문서의 기본언어(content-language), MIME타입(content-type), 기본 스타일시트(default-style), 브라우저호환성설정(X-UA-Compatible), 페이지 리로드(refresh) 등을 나타낼 수 있다. http-equiv 속성이 명시되어 있다면, 반드시 content 속성도 함께 명시되어야 한다. 
- `<meta http-equiv="X-UA-Compatible" content="IE=edge">`: IE='version', edge는 본인 환경에 설치되어 있는 최신 환경으로 렌더링하라는 의미. X-UA-Compatible 태그로 웹위 호환성을 지정할 수 있다.
- `<meta name="viewport" content="width=device-width, initial-scale=1.0">`: viewport대로 렌더링 해라.(반응형에서 동작해라)
- `title`
  - 예를 들어, '어서 오세요. 환영합니다.' 이러한 title을 썼다면 잘못된 것이다. SEO 문서를 지키면 40~60%까지 구글 검색도를 높일 수 있다. 
  - title은 유일해야하고 특성이 있어야 한다.
  - title은 별것 아닌거 같지만 매우 중요하다. - 쓸데없는 특수문자 넣지 말기. 스크린 리더가 별표별표.. 처럼 그냥 읽게 된다. 따라서, 심플하고 중요한 키워드로 제공하는 것이 가장 중요한 전략이다.
  - title에 공백이 있어도 되긴 하지만 없는 것이 좀 더 유리하다. `HTML5, CSS3`보다 `HTML5,CSS3`가 좀 더 검색이 잘된다.


## 구조
### 3단구조
- 헤더, 콘텐츠, 푸터
- 3단구조일때는 네비게이션을 헤더에 포함시킨다. 분리하는 것이 나중에 유지보수나 확장성에 있어서는 좋다.
### CafeW
1. 구성은 다음곽 같이 5부분으로 나눈다.
    - 헤더(네비게이션), 비주얼/광고, 콘텐츠, 슬로건, 푸터
2. 시맨틱 마크업 결정
    - 대부분 개발자는 `div`를 쓴다. css가 편하기 때문이다. 그러나 시맨틱을 사용하면 목표가 명확해지고 엔진에게 목적을 전달할 수 있다.
    - Semantic Element(의미 요소)는 HTML로 만든 문서에 추가적으로 의미를 부여해준다. 무의미한 요소로 문서를 작성할 경우, HTML문서를 접하는 사람이 어떤 데이터를 봐야할지, 어떤 데이터를 제공하는지 파악하기 어렵다. 유지보수하거나 소프트웨어 재공학을 위해 다시 문서를 분석할 경우, 시간을 절약할 수 있다.
    - 사용자 또는 보조기기들이 시맨틱 마크업으로 인해 목적을 잘 알 수 있게 된다. 
    - 시맨틱을 사용할 수 없는 환경이라면?
        - WAI에서 만든 기술 ARIA(Accessible reach internet application)을 사용한다.(landmark role: 탐색이 용이해진다.)
            - role
            - property
            - status
            - ex) div[role="article"], div[role="main"], div[role="banner"]
    ```md
    <article>: 문서나 사이트에서 독립된 컨텐츠 영역을 지정합니다. 이 부분을 다른 곳에 옮기더라도 분리되어지고, 의미가 통해야합니다.

    <aside>: 페이지의 왼쪽 혹은 오른쪽에 위치한 컨텐츠영역을 의미합니다.

    <details>: 추가정보를 기술하는 영역을 의미합니다.

    <dialog>: 대화상자나 창을 지정하며 open속성을 사용하여 숨기거나 보이도록 할 수 있습니다.

    <figure>: 문서흐름상 이해를 위해 필요한 그림, 동영상을 포함할때 사용합니다.

    <figcaption>: <figure>요소의 제목을 지정합니다.

    <footer>: 문서나 Section의 하단 정보 영역을 의미합니다.

    <header>: 문서나 Serction의 상단 정보 영역을 의미합니다.

    <main>: 문서의 주 컨텐츠영역을 지정합니다.

    <mark>: 마크되거나 강조된 텍스트를 의미합니다.

    <menuitem>: 팝업메뉴의 아이템을 지정합니다.

    <nav>: 문서의 네비게이션을 의미합니다.

    <section>: 페이지의 주요부분을 의미하며, 긴 글의 세부사항과 같은 관련 컨텐츠의 묶음, 또는 탭 키 사용을 요하는 인터페이스를 가진 웹 어플리케이션에서의 페이지의 묶음 단위를 의미합니다.
    ```

3. 네이밍
    - 각각을 시맨틱하게 네이밍하는 패턴을 알아야한다.
    - 네이밍 패턴은 여러개 있다. 
        - kebab-case
        - camelCase
        - PascalCase
        - snake_case
        - etc..
    - class 네이밍
      - .header
      - .visual
      - .main
      - .slogan
      - .footer

4. 디자인
    - .footer-inner와 같이 선언

### 4단구조
- 헤더, 내비게이션, 콘텐츠, 푸터

## 단축키
- `div.container`, `.container`
```html
<div class="container"></div>
```

- `.visual{visual}`
```html
<div class="visual">visual</div> 
```
- `header.header{헤더}`
```html
<header class="header">헤더</header>
```
- `footer.footer>.tooter-inner{footer}`
```html
<footer class="footer">
    <div class="tooter-inner">footer</div> 
</footer>
```
- `article.slogan{slogan}`
```html
<article class="slogan">slogan</article>
```
- `div.group.group$*3{group$}`
```html
<div class="group group1">group1</div>
<div class="group group2">group2</div>
<div class="group group3">group3</div>
```

## Chrome Extension
- web developer에서 Block level Line 체크가능, tools(validate local html)에서 문법 검사 가능
- [웹접근성 연구소 wai-aria 사례집](https://www.wah.or.kr:444/board/boardView.asp?page=4&brd_sn=5&brd_idx=1019)



# CSS

## html/css 연결
```html
<link rel="stylesheet" href="./css/stylesheet.css">
```
- cmd + click을 하면 파일이 자동으로 생성할 수 있다.

## font
- local font을 쓰게 되면 OS가 달라지면 문제가 생긴다. 그래서 등장한 것이 `WEB font`이다. 그러나 용량이 크면 지연이 발생할 것이고 로딩이 다 되기 전까지는 화면에 보이지 않는다. 따라서, Webfont를 한 화면에 여러개 쓰면 문제가 생길 수 있다. 
- 모든 브라우저가 같은 포맷을 지원하는 것이 아니다. eot, otf, ttf, woff, woff2, svg 등
- 대부분은 본인 서버에 font를 올려서 쓰지만, CDN을 이용해서 해볼것이다.
- Noto Sans(Adobe에서는 Spoqa Han Sans라고 부른다.)(본고딕)을 자주 사용한다.(다운로드해서 사용할 때 서브셋은 용량 작아서 사용추천)

- 단위: px, em, rem, %, vw, vh


### serif: 바탕체, san-serif: 고딕체
- serif(삐침있는 글자)는 모바일에서 c, g를 헷갈리게 한다. 
- san-serif 계열이 더 많이 사용된다.
https://demun.tistory.com/2402

- 배포 단계에서는 min처럼 압출 버전을 쓴다. 

## reset.css vs normalize.css
- reset.css와 normalize.css에서 선택해서 사용
- normalize.css에서는 모바일 환경까지 커버해준다.
- reset.css
  - 브라우저별로 각각 태그에 대한 기본 스타일링이 다르기 때문에, 기본적인 것들은 초기화해서 사용한다.
  - 장점: 익숙하다(현재 우리나라에서는 초기화하는 방법을 많이 사용하므로 익숙하다. 익숙하므로 작업의 속도 측면에서 고려할 부분이 존재하지 않기 때문에 작업 속도는 빠를 수 있다.), 다른 부분에 신경을 쓰지 않아도 된다.(만약 잘못 쓰고 있는 Resetting일 경우 예상치 못한 변수가 등장한다. 하지만 모든 것을 Resetting하였다면 고려해야할 변수가 적다.)
  - 단점: 코드의 복잡성(Resetting을 하면 우선순위에 따라 또한 상위 또는 하위에 작성했느냐에 따라 스타일이 달리 적용될 수 있다.), 최근 업데이트가 없다.(브라우저는 지속적으로 업데이트되고 있지만 업데이트가 없다.)
- normalize.css
  - normalize는 기존의 브라우저별 스타일을 모두 리셋시키는 방법이 아니라 이를 유지하고, 이용하려는 스타일링 방법이다. 
  - 장점: 코드의 간결함(리셋과 달리 기존 코드를 유지하고, 이용한다는 측면에서 코드의 우선순위 등 충돌이 일어날 가능성이 적다.), 지속적인 업데이트(Resetting과 다르게 최근에 v8.0이 나오고 github을 운영하여 지속적으로 업데이트하고 있다.)
  - 단점: 어색함(국내 개발자들은 Resetting을 사용해왔기 때문에, 어색하다. 그렇기에 생각지 못한 디자인 오류가 발생할 수 있다. 하지만 익숙해지면 괜찮다.)
- 결론: 정답은 없다. 각자 원하는 방법으로 효율적으로 작업하면 된다.


## 설계
- 무작정 코드 작성하지말고 설계를 하고 들어가자. 코드 퀄리티가 달라진다. 리팩토링 하지 않을 정도로 간결하게 구성할 수 있다.

- 높이는 가급적 고정하지 않는 것이 좋다. 
- 실습
  - .header의 width는 940px, 가운데 정렬
  - .visual의 width는 940px, 가운데 정렬
  - .main의 width는 940px, 30px의 padding
  - .main 내부에 그룹 3개. 그룹 여백 사이사이를 gutter라고 한다. width가 어긋나면 안된다. 설계를 정교하게 해서 어긋나게 하지 말자.
  - .slogan의 width는 940px, 가운데 정렬
  - .footer 내부에 .footer-inner는 가운데 정렬
  - 상위 container를 하나 선언하고 그 내부에 내용물들을 넣자.

## 개념
  - `margin: 0 auto;`: 가로 중앙 정렬
  - 화면 요소 배치 시: grid > flex > float > inline-block, absolute
  - CSS Box-Model
    - 태그에는 content, padding, border, margin이 존재한다. 
    - content: 보통 태그가 차지하는 공간(width와 height가 차지하는 공간)이 content이다. 
    - padding, border, margin은 width에 포함되지 않는다.(`box-sizing: border-box`이면 margin만 미포함)