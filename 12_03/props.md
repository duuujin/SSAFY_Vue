# Props
- 부모 컴포넌트로부터 자식 컴포넌트로 데이터를 전달하는데 사용되는 사용자 지정 특성

# Props 특징
- 부모의 데이터가 업데이트되면 자식에게 전달되지만, 그 반대는 불가능
- 즉, 자식 컴포넌트 내부에서 props를 변경하려고 시도해서는 안되며 불가능
- 또한 부모 컴포넌트가 업데이트 될 때마다 이를 사용하는 자식 컴포넌트의 모든 props가 최신 값으로 업데이트 됨
- -> 부모 컴포넌트에서만 변경하고 이를 내려 받는 자식 컴포넌트는 자연스럽게 갱신

# one-Way Data Flow
- 모든 props는 자식 속성과  부모 속성 사이에 하향식 단방향 바인딩을 형성
- 단방향인 이유
    - 하위 컴포넌트가 실수로 상위 컴포넌트의 상태를 변경하여 앱에서의 데이터 흐름을 이해하기 어렵게 만드는 것을 방지하기 위함(무한 루프, 디버깅 난이도 상승)
    - 데이터 흐름의 '일관성' 및 '예측 가능성'을 높이는 것이 목표

# Props 세부사항
1. Props Name Casing (Props 이름 컨벤션)
2. Static Props 와 Dynamic Props


## Props Name Casing
- 부모 템플릿에서 전달 시 (HTML 속성) -> kebab-case(my-msg)
- 자식 스크립트에서 선언시 (JavaScript) -> camelCase(myMsg)

## Static props & Dynamic props
- 지금까지 작성한 것은 Static(정적) props
- v-bind를 사용하여 동적으로 할당된 props를 사용할 수 있음

