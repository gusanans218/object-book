### **객체의 메시지와 협력**

- **메시지**
    - 객체 간 협력의 유일한 의사소통 수단
- **메시지 전송**
    - 한 객체가 다른 객체에게 도움을 요청하는 행위
    - 구성 요소: **메시지 수신자, 오퍼레이션명, 인자**
- **메서드**
    - 메시지를 수신했을 때 실행되는 함수 또는 프로시저
    - 동일한 메시지라도 객체 타입에 따라 실행되는 메서드가 달라질 수 있음(다형성)
- **퍼블릭 인터페이스**
    - 객체가 외부에 공개하는 메시지의 집합
- **오퍼레이션**
    - 퍼블릭 인터페이스에 포함된 메시지로, 추상적인 행동의 표현
- **시그니처**
    - 메서드의 이름과 파라미터 목록

---

### **좋은 인터페이스란?**

1. **최소한의 인터페이스**
    - 필요한 메시지만 노출
2. **추상적인 인터페이스**
    - 구현 세부사항을 숨기고 높은 수준의 추상화 제공

---

### **디미터 법칙**

- **목적**
    - 객체의 내부 구조에 강하게 결합되지 않도록 협력 경로 제한
- **원칙**
    - 묻지 말고 시켜라(Don’t ask, just tell)"
    - **부끄럼타는 코드** 작성:
        - 불필요한 정보를 외부에 노출하지 않음
        - 낮은 결합도 유지
- **위반의 결과**
    - **기차 충돌**: 클래스 내부 구현이 외부에 노출됨
    - 인터페이스와 구현의 분리 원칙 위반

---

### **명령-쿼리 분리 원칙**

- **명령(Command)**:
    - 상태를 변경할 수 있지만 상태를 반환하지 않음
- **쿼리(Query)**:
    - 상태를 반환할 수 있지만 상태를 변경하지 않음
- 질문이 답변을 수정하지 않도록 설계

---

### **메서드의 이름 짓기**

1. **작업 방법을 나타내는 이름**
    - 메서드가 "어떻게" 수행되는지를 표현
2. **의도를 드러내는 이름**
    - "무엇"을 하는지 드러내는 방식

---

### **다형성과 오퍼레이션**

- 다형성: 동일한 오퍼레이션 호출에 대해 객체 타입에 따라 다른 메서드가 실행됨

---

### **소프트웨어 설계의 철학**

- 법칙은 존재하지 않으며, 원칙을 맹신하지 말 것
- 원칙의 적절성과 부적절성을 판단할 수 있는 **안목**을 길러야 함