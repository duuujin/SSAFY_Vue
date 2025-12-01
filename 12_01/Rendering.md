# v-if
- 표현식 값의 true/false를 기반으로 요소를 조건부로 렌더링
- 특정 조건이 참(true)일 때만 HTML요소를 화면에 보여주도록 하는 Directive

## 여러 요소에 대한 v-if 적용
- template 요소에 v-if를 사용하면, 여러 요소를 하나의 조건부 블록으로 묶을 수 있음(v-else, v-else-if 모두 적용 가능)

# v-show
- 표현식 값의 true/false를 기반으로 요소의 가시성을 전환
- v-show는 v-if와 비슷하게 특정 조건에 따라 HTML 요소를 보여주거나 숨기는 Directive이다.
- 하지만 DOM에서 요소를 완전히 제거하는 v-if와 달리, v-show는 CSS의 display 속성을 none으로 바꿔 화면에서만 보이지 않게 숨김

# v-show 예시
- v-show를 사용한 요소는 조건과 관계없이 항상 DOM에 렌더링 됨
- CSS display 속성만 전환하기 때문(none 속성으로 변환)

## v-if와 v-show의 적절한 사용처
- v-if(Cheap initial load, expensive toggle)
    - 초기 조건이 false인 경우 아무 작업도 수행하지 않음
    - 토글 비용이 높음
- v-show(Expensive initial load, cheap toggle)
    - 초기 조건에 관계없이 항상 렌더링
    - 초기 렌더링 비용이 더 높음
 - -> 콘텐츠를 매우 자주 전환해야 하는 경우에는 v-show를, 실행 중에 조건이 변경되지 않는 경우에는 v-if를 권장

 # v-for
 - 소스 데이터를 기반으로 요소 또는 템플릿 블록을 반복 렌더링
 - 배열(array)이나 객체(Object)의 데이터를 렌더링하는 반복문 Directive이다
 
 ## v-for 구조
 - v-for는 alias in expression 형식의 특별한 구문을 사용
 - 객체는 key-value 쌍으로 이루어져 있어, 값(value), 키(key), 인덱스(index)를 조합하여 순회할 수 있음

 # v-for와 key
 - v-for 구문은 각 요소를 key를 활용하여 고유한 값으로 식별할 수 있음
 - key는 각 항목을 고유하게 식별할 수 있는 문자열이나 숫자여야 함

 ## 내장 특수 속성 'key'의 특징
 - 각 항목이 서로 구분되는 고유 식별자 역할
 - number 혹은 string으로만 사용해야 함
 - Vue의 내부 가상 DOM이 알고리즘이 이전 목록과 새 노드 목록을 비교할 때 각 node를 식별하는 용도로 사용
 - key를 통해 '이 항목은 이 테이터에 해당한다'는 힌트를 줌으로써 변경 시에도 올바른 항목만 효율적으로 업데이트 할 수 있음
 - -> 반드시 v-for와 key를 함께 사용한다


 ## 올바른 key 선택 기준
 - 권장되는 key 값
    - 데이터베이스의 고유 ID
    - 항목 고유 식별자 (예:UUID)
- 피애햐 할 key 값
    - 배열 인덱스(index)
    - 객체 자체

