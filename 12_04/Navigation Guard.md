# Navigation Guard

- Vue router를 통해 특정 URL에 접근할 때 다른 URL로 redirect를 하거나 취소하여 내비게이션을 보호
- 내비게이션 가드는 특정 URL로 이동하기 전이나 후에 실행되는 기능

# Navigation Guard 종류

1. Globally (전역 가드)
   - 애플리케이션 전역에서 모든 라우트 전환에 적용되는 가드
2. Per-route (라우터 가드)
   - 특정 라우트에만 적용되는 가드
3. In-component (컴포넌트 가드)

   - 컴포넌트 내에서만 적용되는 가드

# Globally Guard(전역 가드)

- 애플리케이션 전역에서 동작하는 가드 -> 작성 위치 : index.js
- Globally Guard 종류
  1. beforeEach()
  2. beforeResolve()
  3. afterEach()

1. Globally Guard : beforeEach()구조

- 다른 URL로 이동하기 직전에 실행되는 함수(Global Before Guards)
- 모든 가드의 콜백 함수는 2개의 인자를 받음
  - to : 이동 할 URL 정보가 담긴 Route 객체
  - from : 현재 URL 정보가 담긴 Route 객체
- 선택적으로 다음 값 중 하나를 반환
  1. false
     - 현재 내비게이션을 취소
     - 브라우저 URL이 변경된 경우 (사용자가 수동을 또는 뒤로가기 버튼을 통해) 'from' 경로의 URL로 재설정
  2. Route Location
     - router.push()를 호출하는 것처럼 경로 위치를 전달하여 다른 위치로 redirect
     - return이 없다면 자동으로 'to' URL Route 객체로 이동

2. Globally Guard : beforeResolve()

- beforeEach와 모든 컴포넌트 단위 가드가 실행된 후, 내비게이션이 확정되기 직전에 호출
- 모든 비동기 컴포넌트가 로드되고, 모든 가드가 통과된 상태에서 마지막으로 무언가를 확인하고 싶을 때 사용
- 주로 사용 예시
  - 페이지에 진입하기 전에, 사용자의 권한과 관련된 데이터를 미리 가져오는 등의 작업에 사용
- 비교적 사용 빈도가 beforeEach보다 낮음

3. Globally Guard : afterEach()

- 내비게이션이 완전히 확정된 후, 즉 URL이 변경되고 화면 렌더링이 끝난 뒤에 호출
- 이미 이동이 완료된 상태이므로, 내비게이션을 중단시키거나 변경할 수 없음
- 주로 사용 예시
  - 페이지 이동 기록을 로깅(logging)하거나, 이동한 페이지에 맞춰 문서의 제목(document.title)을 변경하는 등 후처리 작업에 적합

# Per-route Guard(라우터 가드)

- 특정 라우트(경로)에 진입할 때만 실행되도록 라우트 설정 객체에 직접 정의하는 가드 -> 작성 위치 index.js의 각 routes
- 주로 beforeEnter 가드를 많이 사용

1. Per-route Guard : beforeEnter() 설명 및 예시

- 특정 route에 진입했을 때만 실행되는 함수
- 단순히 URL의 매개변수나 쿼리 값이 변경 될 때는 실행되지 않고, 다른 URL에서 탐색해 올 때만 실행 됨
- 라우터 가드 beforeEnter 작성
- HomeView에서 LoginView로 이동 후 각 인자 값 출력 확인하기
- to에는 이동할 URL인 login 라우트에 대한 정보, from에서는 현재 URL인 home 라우트에 대한 정보가 있음
- 다른 경로에서 login 라우트를 탐색 했을 때 실행 된 것

2. Per-route Guard : beforeEnter() 활용

- 이미 로그인 한 상태라면 LoginView 진입을 막고 HomeView로 이동 시키기
- 로그인 상태라면 HomeView로 이동, 로그인 상태가 아니라면 LoginView로 이동

# In-component Guard(컴포넌트 가드)

- 특정 컴포넌트 내에서만 동작하는 가드 -> 작성위치 : 각 컴포넌트의 `<script>` 내부
- In-component Guard 종류
  - onBeforeRouteLeave()
    - 현재 라우트에서 다른 라우트로 이동하기 전에 실행
    - -> 사용자가 현재 페이지를 떠나는 동작에 대한 로직을 처리
  - onBeforeRouteUpdate()
    - 이미 렌더링 된 컴포넌트가 같은 라우트 내에서 업데이트 되기 전에 실행
    - -> 라우트 업데이트 시 추가적인 로직을 처리

# Navigation Guard 정리

1. Globally (전역 가드)
   - 애플리케이션 전역에서 동작
   - 작성위치 : index.js
2. Per-route (라우터 가드)
   - 특정 route에서만 동작
   - 작성위치 : index.js의 각 routes
3. In-component (컴포넌트 가드)
   - 특정 컴포넌트 내에서만 동작
   - 작성위치 : 각 컴포넌트의 script
