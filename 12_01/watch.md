# watch()
- 하나 이상의 반응형 데이터를 감시하고, 감시하는 데이터가 변경되면 콜백 함수를 호출

# watch 구조
1. 첫번째 인자(source)
    - watch가 감시하는 대상(반응형 변수, 값을 반환하는 함수)
2. 두번째 인자(callback function)
    - source가 변경될 때 호출되는 콜백 함수
    1. newValue
        - 감시하는 대상이 변화된 값
    2. oldValue (optional)
        - 감시하는 대상의 기존 값

# watch 기본 동작
- count 반응형 데이터가 변경될 때마다, 그 변화를 감지하여 특정 작업을 수행
- 버튼을 누를 때마다 count 값이 바뀌고, watch는 그 변화를 '감시'하고 있다가 즉시 콜백함수를 실행

## computed와 watch 
- 공통점 : 데이터의 변화를 감지하고 처리
- 동작 : 
    - Computed : 의존하는 데이터 속성의 계산된 값을 반환
    - Watchers : 특정 데이터 속성의 변화를 감시하고 작업을 수행(side-effects)
- 사용 목적 : 
    - Computed : 계산한 값을 캐싱하여 재사용 중복 계산 방지
    - Watchers : 데이터 변화에 따른 특정 작업을 수행
- 사용 예시 :
    - Computed : 연산 된 길이, 필터링 된 목록 계산 등
    - Watchers : DOM 변경, 다른 비동기 작업 수행, 외부 API와 연동 등

--

# Lifecycle Hooks
- Vue 컴포넌트가 생성되고, DOM에서 마운트되고, 업데이트 되고, 소멸되는 각 생애 주기 단계에서 실행되도록 제공하는 함수

# Lifecycle Hooks Diagram
- 컴포넌트의 생애 주기 중간 중간에 함수를 제공

# 주요 Lifecycle Hooks
- 생성단계 / 마운트 단계 / 업데이트 단계 / 소멸 단계 등 다양한 단계 존재
- 가장 일반적으로 사용되는 것은 onMounted, onUpdated, onUnmounted


## 주요 Lifecycle Hooks : Mounting
- Vue 컴포넌트 인스턴스가 초기 렌더링 및 DOM 요소 생성이 완료된 후 특정 로직을 수행하기

## 주요 Lifecycle Hooks : Updated
- 반응형 데이터의 변경으로 인해 컴포넌트의 DOM이 업데이트 된 후 특정 로직을 수행하기
