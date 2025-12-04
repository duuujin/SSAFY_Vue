# useRoute()

- 현재 활성화된 '경로 정보(route)'를 담은 route 객체를 반환
- useRoute()는 컴포넌트의 setup 함수나 `<script setup>`최상단에서만 호출해야함

# route 객체

- 현재 URL 상태를 보여주는 역할
  - route 객체 자체를 통해 페이지 이동(네비게이션)을 직접 제어 할 수는 없음
- 읽기 전용이며, 현재 URL/파라미터쿼리/name/matched 된 라우트 정보 등을 담고 있음
  - 경로 파라미터(route.params), 쿼리(route.query), name(route.name)등을 통해 현재 페이지 상태를 알 수 있음
- 반응형이며, URL이 변경되면 route 객체도 자동으로 변경됨
  - 예) route.params.id를 참조하고 있다면, URL이 바뀌어 id가 변경될 때 해당 값이 자동으로 반영됨

# useRouter()

- 라우터 인스턴스 router 객체를 반환
- useRouter는 페이지 이동 등 액션용, useRoute는 경로 정보 읽기용으로 역할이 다름

# router 객체

- 애플리케이션 전체 라우팅 로직을 제어할 수 있는 핵심 객체
- 페이지 이동, 네비게이션 관련 메서드 제공
  - router.push('~'), router.replace('~') 등을 통해 프로그래밍적으로 라우트를 변경할 수 있음
- 네비게이션 가드 등록, 히스토리 제어 같은 긴으 사용 가능

# route와 router 정리

- useRoute()
  - 현재 라우트 '상태'를 읽어오는 전용 객체
- useRouter() - 라우팅 로직 '제어'및 페이지 이동을 담당하는 인스턴스
  ![alt text](image.png)
