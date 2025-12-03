# $emit()
- 자식 컴포넌트가 이벤트를 발생시켜 부모 컴포넌트로 데이터를 전달하는 메서드

## emit 메서드
```vue
$emit(event, ...args)
```
- 자식 컴포넌트가 이벤트를 발생시켜 부모 컴포넌트에게 신호를 보내고 데이터를 전달하는 기능
- event
    - 커스텀 이벤트 이름
- args
    - 추가 인자

## 이벤트 발신 및 수신(Emitting and Listening to Events)
1. $emit을 사용하여 템플릿 표현식에서 직접 사용자 정의 이벤트를 발신
2. 부모 컴포넌트에서는 v-on(또는 @)을 사용하여 이벤트를 수신할 수 있음

# emit 이벤트 선언
- defineEmits()를 사용하여 발신할 이벤트를 선언
- props와 마찬가지로 defineEmits()에 작성하는 인자의 데이터 타입에 따라 선언 방식이 나뉨
    - 배열
    - 객체(가급적 객체를 활용한 선언을 추천)
- defineEmits()는 `<script setup>`내에서 이벤트를 발신하기 위한 emit 함수를 반환(템플릿의 $emit과 달리 `<script setup>`에서는 직접 접근 할 수 없기 때문)
