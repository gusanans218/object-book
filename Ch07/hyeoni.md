# 07. 객체 분해

### 추상화와 분해
- 추상화: 문제를 해결하는 데 필요한 핵심 요소만 남기고 불필요한 정보를 제거하는 과정
- 분해: 큰 문제를 해결 가능한 작은 단위로 나누는 작업
- 두 기법은 복잡성을 줄이고 문제 해결을 용이하게 함

---

### 프로시저 추상화와 데이터 추상화
- 프로시저 추상화: 로직을 재사용하고 중복을 방지하는 기능 기반의 추상화 기법
- 데이터 추상화: 데이터와 연관된 연산을 묶어 외부로부터 데이터를 보호하고 변경에 안정적인 설계를 제공함

---

### 하향식 접근법의 한계
- 초기 설계에서 구현 중심으로 진행되며, 변경에 취약하고 유연성이 떨어짐
- 비즈니스 로직과 UI의 강한 결합, 실행 순서의 고정으로 인해 재사용성과 유지보수성이 저하됨

---

### 정보 은닉과 모듈화
- 자주 변경되는 부분과 안정적인 부분을 분리하고, 퍼블릭 인터페이스로만 접근 가능하게 설계
- 모듈은 높은 응집도와 낮은 결합도를 통해 변경 관리와 재사용성을 향상시킴

---

### 모듈의 장점과 한계
- 모듈 내부 변수가 변경돼도 모듈 내부만 영향을 미침
- 비즈니스 로직과 사용자 인터페이스에 대한 관심사 분리를 분리함
- 전역 변수와 전역 함수를 제거함으로써 네임스페이스 오염을 방지함

---

### 추상 데이터 타입(ADT)과 객체지향(OOP)
- ADT: 데이터를 기반으로 타입을 정의하고 데이터의 조작을 보호
- OOP: 다형성과 상속을 통해 프로시저를 추상화하며, 변경에 강한 설계를 가능하게 함

---