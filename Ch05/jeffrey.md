# 5. 책임 할당하기
데이터 중심 설계로 인해 발생하는 문제점을 해결할 수 있는 가장 기본적인 방법은 **책임에 초점**을 맞추는 것.

## 책임 주도 설계

어떤 객체에게 어떤 책임을 할당할지를 결정하기가 쉽지 않다. **책임 할당 과정은 일종의 트레이드 오프 활동**.

책임 중심 설계로의 전환을 위해서 아래 두가지 원칙을 따라야 한다.

### 데이터보다 행동을 먼저 결정

1. 이 객체가 **수행해야 하는 책임은 무엇인가**를 결정한다.
2. 이 책임을 **수행하는 데 필요한 데이터는 무엇인가**를 결정한다.

즉, **책임을 먼저 결정한 후**에 **객체의 상태를 결정**해야 한다.

### 협력이라는 문맥 안에서 책임을 결정

- 책임의 품질은 **협력에 적합한 정도**로 결정된다.
- 책임은 객체의 입장이 아닌 **객체가 참여하는 협력에 적합**해야 한다.
    - 메시지 전송자에게 적합한 책임을 의미.
        
        → 메시지 수신자는 메시지를 처리할 책임을 할당 받게 된다.
        
- 메시지를 결정한 후에 객체를 선택해야 한다.
    - 메시지가 존재하기 때문에, 그 메시지를 처리할 객체가 필요한 것.

<br>

## 책임 할당을 위한 GRASP (General Responsibility Assignment Software Pattern) 패턴

### 도메인 개념에서 출발하기

- 설계 시작 전에 도메인에 대한 개략적인 모습을 그려보는 것이 유용
- 어떤 책임을 할당할 때 가장 먼저 고민해야 하는 유력한 후보가 **도메인 개념**
- 시작 단계에서는 개념들의 의미와 관계가 정확하거나 완벽할 필요가 없다. 단지 **출발점이 필요**한 것일 뿐.
- 도메인 개념 정리에 시간을 많이 들이지 말고, **우선 빠르게 설계와 구현을 진행**하자.

### 정보 전문가에게 책임을 할당하라

책임 주도 설계의 첫 단계는 제공해야 하는 기능을 책임으로 생각하는 것. 책임을 부여할 객체를 선택하는 것으로 설계를 시작.

1. `영화를 예매하는 것` 을 책임으로 간주하면, 책임을 수행하는 데 필요한 메시지를 결정한다.
2. 메시지를 전송할 객체는 무엇을 원하는지 확인
    - 영화를 예매하는 것. 따라서 메시지 이름은 `예매하라` 가 적절
3. 메시지를 수신할 적합한 객체 찾기

### **INFORMATION EXPERT  패턴**

- **책임을 수행할 정보를 알고 있는 객체에게 책임을 할당**하는 것
- 정보를 알고 있는 객체만이 책임을 어떻게 수행할지 스스로 결정할 수 있기 때문이다.
- 객체는 자신이 소유하고 있는 정보(데이터 X)와 관련된 작업만 수행.
- 필요한 **정보를 저장하고 있을 필요는 없고**, 정보를 제공할 수 있는 다른 객체를 알고 있거나 필요한 정보를 계산해서 제공할 수도 있다.

### LOW COUPLING 패턴

의존성을 낮추고 변화의 영향을 줄이며 재사용성을 증가시키기 위해 설계의 전체적인 **결합도가 낮게 유지**되도록 책임을 할당.

### HIGH COHESION 패턴

복잡성을 관리할 수 있는 수준으로 유지하기 위해 **높은 응집도를 유지**할 수 있게 책임을 할당.

### CREATOR 패턴

- **객체를 생성할 책임**을 어떤 객체에게 할당할지에 대한 지침을 제공.
- 생성되는 객체와 연결되거나 관련될 필요가 있는 객체에 해당 객체를 생성할 책임을 맡기는 것
- **생성 책임을 할당해야할 객체 조건**
    - 객체를 포함하거나 참조한다
    - 객체를 기록한다
    - 객체를 긴밀하게 사용한다
    - 객체를 초기화하는 데 필요한 데이터를 가지고 있다
- 이미 결합된 객체 사이의 관계를 이용하기에 낮은 결합도를 유지할 수 있다.

### POLYMORPHISM 패턴

- 객체의 타입에 따라 변하는 행동이 있다면 타입을 분리하고 변화하는 행동을 각 타입의 책임으로 할당
- 타입을 명시적으로 정의하고 각 타입에 다형적으로 행동하는 책임을 할당
- 타입에 따라 여러 대안들을 수행하는 **조건적인 논리를 사용하지 말고** 다형성을 이용해 새로운 변화를 다루기 쉽게 확장하는 것을 권고

### PROTECTED VARIATIONS

- 변화가 예상되는 불안정한 지점들을 식별하고 그 주위에 안정된 인터페이스를 형성하도록 책임을 할당
- 책임 할당의 관점에서 캡슐화를 설명한 패턴.
- 캡슐화해야 하는 것은 변경. **변경이 될 가능성이 높다면 캡슐화**하라.

<br>

## 개선하기

- 하나 이상의 변경 이유를 가지는 경우, 응집도가 낮기 때문에 **변경의 이유에 따라 클래스를 분리해야 한다**.
- 서로 다른 두 개의 메서드를 가지는 클래스의 응집도는 낮아질 수밖에 없다.
- 설계를 개선하는 작업은 변경의 이유가 하나 이상인 클래스를 찾는 것으로부터 시작하는 것이 좋으며, 이러한 클래스에는 몇 가지 패턴이 존재한다.
    - 인스턴스 변수가 초기화되는 시점 살펴보기
        - 응집도가 높은 클래스는 인스턴스를 생성할 때 모든 속성을 함께 초기화.
            
            응집도가 낮은 클래스는 일부만 초기화.
            
    - 메서드들이 인스턴스 변수를 사용하는 방식 살펴보기
        - 응집도가 높은 클래스는 모든 메서드가 객체의 모든 속성을 사용
        - 응집도가 낮은 클래스는 메서드들이 사용하는 속성에 따라 그룹이 나뉜다.
- 응집도 판단
    - 클래스가 하나 이상의 이유로 변경돼야 하는 경우.
        - 변경의 이유를 기준으로 클래스 분리
    - 인스턴스를 초기화하는 시점에 서로 다른 속성들을 초기화하는 경우.
        - 초기화되는 속성의 그룹을 기준으로 클래스 분리
    - 메서드 그룹이 속성 그룹을 사용하는지 여부로 나뉘는 경우.
        - 이들 그룹을 기준으로 클래스 분리

### 도메인 모델

- 도메인 모델은 단순히 설계에 필요한 용어를 제공하는 것을 넘어 **코드의 구조에도 영향을 미친다.**
- 변경 역시 도메인 모델의 일부다.
    - 도메인 안에서 변하는 개념과 이들 사이의 관계가 투영돼 있어야 한다.
- 객체지향은 도메인의 개념과 구조를 반영한 코드를 가능하게 만들기 때문에, 도메인의 구조가 코드의 구조를 이끌어 내는 것은 자연스러울뿐만 아니라 바람직한 것이다.
- 코드의 구조가 바뀌면 도메인에 대한 관점도 함께 바뀐다
- 도메인에 포함된 개념과 관계뿐만 아니라 도메인이 요구하는 유연성도 정확하게 반영한다.
- 도메인 모델은 **구현과 밀접한 관계**를 맺어야 한다.
- **코드에 대한 가이드를 제공**할 수 있어야 하며 **코드의 변화에 발맞춰 함께 변화**해야 한다.

### 변경과 유연성

- 개발자로서 변경에 대비할 수 있는 두 가지 방법
    - 코드를 이해하고 수정하기 쉽도록 최대한 단순하게 설계하기
    - 코드를 수정하지 않고도 변경을 수용할 수 있도록 코드를 더 유연하게 만들기.
    
    → 대부분의 경우 전자가 더 좋은 방법이나,
    
    유사한 변경이 반복적으로 발생하고 있다면 복잡성이 상승하더라도 유연성을 추가하는 **두 번째 방법이 더 좋음**.
    
- 상속 대신 합성을 사용하자.

### 리팩터링

- 프로그램을 빠르게 작성한 후 완성된 코드를 객체지향적인 코드로 변경하자.
    - 아무것도 없는 상태에서 책임과 협력에 고민하기 보다는, 실행되는 코드를 얻고난 후 책임들을 올바른 위치로 이동
- 코드를 수정한 후에 겉으로 드러나는 동작이 바뀌어서는 안 된다.
    - 캡슐화를 향상시키고, 응집도를 높이고, 결합도를 낮춰야 하지만 동작은 그대로 유지

### 메서드 응집도

- 긴 메서드(Monster method)는 다양한 측면에서 유지보수에 부정적인 영향을 미친다.
    - 한눈에 파악하기 어려워 코드를 전체적으로 이해하는 데 많은 시간 소요
    - 변경이 필요할 때 수정해야할 부분을 찾기 어렵다
    - 메서드 내부 일부 로직만 수정하더라도 나머지 부분에서 버그가 발생할 확률이 높다
    - 로직의 일부만 재사용하는 것이 불가능
    - 코드 중복을 초래하기 쉽다
- 메서드가 명령문들의 그룹으로 구성되고, 각 그룹에 주석을 달아야 할 필요가 있다면 분해하자.
    - 작은 메서드들로 조합된 메서드는 마치 주석들을 나열한 것처럼 보이기 때문에 코드 이해가 쉽다.
        - 단, 이름을 잘 지었을 때 그 진가가 드러남.
    - 나눠진 메서드는 다른 메서드에서 재사용될 확률이 높다.
    - 오버라이딩이 쉽다
    - 길이보다는 메서드의 이름과 몸체의 의미적 차이다.
        - 더욱 명확하다면, 원래 코드의 길이보다 길어져도 나누자.
- 메서드를 다른 클래스로 이동시킬 때는 인자에 정의된 클래스 중 하나로 이동하는 경우가 일반적이다.