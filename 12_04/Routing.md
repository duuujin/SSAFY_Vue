# Routing

- 네트워크에서 경로를 선택하는 프로세스
- 라우팅은 사용자가 접속한 URL 주소에 따라 적절한 페이지(컴포넌트)를 보여주는 기능

# SSR에서의 Routing

- SSR : 서버에서 완성된 HTML 페이지를 만들어, 브라우저에 보내는 방식
- SSR에서 routing은 서버 측에서 수행
- 서버가 사용자가 방문한 URL 경로를 기반으로 응답을 전송
- 링크를 클릭하면 브라우저는 서버로부터 HTML 응답을 수신하고 새 HTML로 전체 페이지를 다시 로드

# CSR에서의 Routing

- CSR : 서버는 뼈대만 주고, 브라우저가 직접 페이지를 그리는 방식
- CSR에서의 routing은 클라이언트 측(브라우저)에서 수행
- 클라이언트 측 JavaScript가 새 데이터를 동적으로 가져와 전체 페이지를 다시 로드 하지 않음

# SPA에서 Routing이 없다면

- spa : 하나의 페이지 안에서, 내용만 바꿔가며 보여주는 웹 앱
- 유저가 URL을 통한 페이지의 변화를 감지할 수 없음
- 페이지가 무엇을 렌더링 중인지에 대한 상태를 알 수 없음
  - URL이 1개이기 때문에 새로 고침 시 처음 페이지로 되돌아감
  - 링크를 공유 할 시 첫 페이지만 공유 가능
- 브라우저의 뒤로 가기 기능을 사용할 수 없음
- -> 페이지는 1개이지만, 주소에 따라 여러 컴포넌트를 새로 렌더링 하여 마치 여러 페이지를 사용하는 것처럼 보이도록 해야 함

# Vue Router

- Vue 공식 라우터
- Vue.js의 공식 라우팅 라이브러리로, Vue로 만든 SPA에서 페이지 이동 기능을 구현할 때 사용됩니다.

# 라우팅 기본 동작 순서

1. index.js에 라우터 관련 설정 작성
2. RouterLink에 index에 정의한 주소 값 작성
3. RouterLink 클릭 시 경로와 일치하는 컴포넌트가 RouterView에서 렌더링

# path 경로를 그대로 사용하기

- 현재는 index.js에서 입력한 path 경로를 그대로 RouterLink에 사용하고 있음
- 이 방식은 URL 경로를 변경할 때, 해당 경로를 사용한 모든 파일을 일일이 찾아다니며 사용해야 하는 단점이 있음(유지보수 난이도 증가)

# Named Routes

- name 속성 값에 경로에 대한 이름을 지정
- 경로에 연결하려면 RouterLink에 v-bind를 사용해 'to' props 객체로 전달 가능
- 하드 코딩된 URL 을 사용하지 않아도 되며, 오타를 방지할 수 있음

# Dynamic Route Matching

- URL의 일부를 변수로 사용하여 경로를 동적으로 매칭
- 동적 라우트 매칭은 /user/1 , /user/2 처럼 패턴은 같지만 ID값만 다른 여러 URL을 하나의 라우트 설정으로 처리하는 기능입니다.

# Nested Routes

- 중첩된 라우팅
- 중첩 라우트는 특정 페이지(부모)의 레이아웃은 유지한 채, 그 안의 일부 영역만 다른 내용으로 교체하는 라우팅 방식입니다.

## 중첩된 라우팅 주의사항

- 컴포넌트 간 부모-자식 관계 관점이 아닌 "URL에서의 중첩된 관계를 표현"하는 관점으로 바라보기
- 자식 라우트의 path는 / 없이 작성해야, 부모 경로 뒤에 자동으로 연결 됨
- 부모 라우트의 파라미터(:id)는 자식 컴포넌트에서도 바로 접근해서 사용할 수 있음

# Programmatic Navigation

- `<RouterLink>`를 사용하는 대신, JavaScript 코드를 사용해 페이지를 이동시키는 것
- Programmatic Navigation은 사용자가 `<router-link>`를 대신, JavaScript코드(로직)를 통해 특정 URL로 이동시키는 기능입니다.

## Programmatic Navigation

- 프로그래밍으로 URL 이동하기
- router의 인스턴스 메서드를 사용해 RouterLink로 `<a>`태그를 만드는 것처럼 프로그래밍으로 네비게이션 관련 작업을 수행할 수 있음
- router의 메서드
  1. router.push()
     - 다른 위치로 이동하기
  2. router.replace()
     - 현재 위치 바꾸기

## 1. router.push()

- 다른 URL로 이동하는 메서드
- 새 항목을 history stack에 push하므로 사용자가 브라우저 뒤로 가기 버튼을 클릭하면 이전 URL로 이동할 수 있음
- RouterLink를 클릭했을 때 내부적으로 호출되는 메서드이므로 RouterLink를 클릭하는 것은 router.push()를 호출하는 것과 같음
- 선언적 표현 : `<RouterLink :to="...">`
- 프로그래밍적 표현 : router.push(...)

## 2. router.replace()

- 현재 위치를 바꾸는 메서드
- push 메서드와 달리 history stack에 새로운 항목을 push 하지 않고 다른 URL로 이동
- 선언적 표현 : `<RouterLink :to="..." replace>`
- 프로그래밍적 표현 : router.replace(...)
