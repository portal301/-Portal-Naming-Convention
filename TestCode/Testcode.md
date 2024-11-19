# Test Code 

## Objective
소프트웨어 개발에서 테스트 코드는 단순한 버그 검출 도구 이상의 가치를 지닙니다. 코드의 품질을 보장하고, 개발 속도를 높이며, 코드 리팩토링 및 유지보수를 안전하게 수행할 수 있도록 돕는 중요한 역할을 합니다. 그러나 많은 개발자들이 테스트 코드 작성의 필요성을 인식하면서도, 실제로 어떻게 작성해야 하는지에 대한 구체적인 지침을 가지지 못한 경우가 많습니다. 이에 따라, 일관된 테스트 코드를 작성하는 것이 어렵게 느껴질 수 있습니다.

이 문서에서는 파이썬(Python)을 예로 들어, 테스트 코드를 작성하는 방법과 이를 통해 보다 안정적이고 신뢰성 있는 애플리케이션을 개발할 수 있는 방안을 제시합니다. 테스트 코드를 작성하는 과정에서 사용할 수 있는 다양한 컨벤션과 패턴, 그리고 모범 사례를 소개하여, 테스트 코드가 단순한 "필수 작업"이 아닌, 개발 프로세스의 핵심 요소로 자리잡을 수 있도록 하는 것이 이 문서의 목표입니다.

테스트 코드는 코드의 현재 상태를 검증하고, 이후의 변경이 의도치 않은 영향을 미치는 것을 방지하기 위해 필수적입니다. 또한, 코드의 내부 구조와 동작 방식을 이해하는 데 중요한 가이드라인이 될 수 있으며, 신규 개발자나 팀 구성원이 프로젝트에 빠르게 적응할 수 있도록 돕습니다. 이러한 이유로, 체계적이고 효율적인 테스트 코드를 작성하는 것은 소프트웨어 개발에서 큰 가치를 가지며, 코드의 가독성과 유지보수성을 향상시키는 핵심 요소로 자리 잡고 있습니다.

이 문서를 통해 테스트 코드의 기본 원칙과 방법을 이해하고, 다양한 테스트 시나리오를 통해 실제 프로젝트에 적용할 수 있는 테스트 코드 작성법을 익히게 될 것입니다. 이를 통해 궁극적으로, 코드의 안정성을 높이고 프로젝트의 성공적인 개발을 지원할 수 있을 것입니다.


## 테스트 코드 작성 시점

테스트 코드 작성 시점은 소프트웨어 개발의 전략과 워크플로우에 따라 다양하게 결정될 수 있습니다. 올바른 시점에 테스트 코드를 작성하면 개발 효율성을 높이고, 오류를 사전에 방지하며, 코드의 품질을 보장할 수 있습니다. 테스트 코드를 언제 작성할지에 대한 결정은 프로젝트의 성격, 개발 팀의 문화, 그리고 개발자의 습관에 따라 달라질 수 있지만, 일반적으로 다음과 같은 시점들을 고려할 수 있습니다.

### 개발 전: 테스트 주도 개발(TDD)
테스트 주도 개발(Test-Driven Development, TDD)은 테스트 코드를 먼저 작성하고 그 테스트를 통과하기 위한 최소한의 기능을 구현하는 개발 방법론입니다. TDD는 다음의 순환 과정을 반복하며 개발이 이루어집니다:

**테스트 작성**: 먼저, 원하는 기능의 테스트 코드를 작성하여, 예상 동작을 정의합니다.

**테스트 실행**: 테스트가 실패하는 것을 확인합니다. (이 시점에는 아직 기능이 구현되지 않았기 때문에 당연히 실패합니다.)
기능 구현: 테스트를 통과할 수 있도록 최소한의 코드를 작성합니다.

**리팩토링**: 기능이 정상적으로 동작하고 테스트가 통과하면, 코드를 리팩토링하여 가독성 및 성능을 개선합니다.

이 방법론의 가장 큰 장점은 개발자가 명확한 목표(테스트)를 가지고 코딩을 시작한다는 점과, 코드가 기대한 대로 동작하는지 즉시 확인할 수 있다는 점입니다. 또한, 기능의 변경이 있을 때 빠르게 리팩토링을 수행할 수 있으며, 코드의 품질과 일관성을 높일 수 있습니다.

#### TDD를 적용할 때의 이점:

명확한 요구사항 정의 및 기능 명세
코드의 안정성 확보 및 리팩토링 용이성 증가
결함 및 버그 발생 가능성 감소

#### TDD의 적용이 어려운 경우:

초기 개발 단계에서 요구사항이 빈번하게 변경되는 경우
복잡한 시스템 또는 기존 시스템의 변경 작업에서 테스트 작성이 어려운 경우

### 개발 중: 기능 개발 및 구현과 동시에 테스트 작성
모든 기능을 사전에 정의하기 어려운 경우, 개발과 테스트 코드를 병행하여 작성할 수 있습니다. 기능을 하나씩 구현하면서, 해당 기능을 검증하는 테스트 코드를 함께 작성합니다. 이 접근 방식은 다음과 같은 단계로 이루어질 수 있습니다:

1. 기능의 일부분을 개발한 후, 해당 기능을 테스트할 수 있는 단위 테스트(Unit Test)를 작성합니다.
2. 테스트 코드를 실행하여 기능이 올바르게 동작하는지 확인합니다.
3. 필요한 경우, 추가적인 테스트 케이스(예외 상황, 경계 값 등)를 작성하여 더 높은 커버리지를 확보합니다.

이 방법은 TDD만큼 엄격하지 않으면서도, 개발자에게 필요한 시점에 테스트 코드를 작성할 수 있는 유연성을 제공합니다. 특히, 새로운 기능을 빠르게 개발하고자 할 때 효과적입니다.

#### 개발 중 테스트 코드 작성의 이점:

기능 단위로 테스트가 이루어지므로, 각 기능의 완성도를 개별적으로 확인 가능

기능 추가 또는 변경 시 즉각적으로 검증 가능

개발 속도와 코드 안정성의 균형 유지

#### 주의할 점:

테스트 코드 작성이 뒤로 미뤄질 가능성이 있음

개발자마다 테스트의 범위와 깊이에 차이가 생길 수 있음

### 개발 후: 기능 구현 완료 후 테스트 코드 작성
모든 기능을 구현한 뒤, 테스트 코드를 작성하여 전체 기능의 일관성을 검증할 수 있습니다. 이 접근 방식은 초기 개발 시에는 빠르게 코드를 작성할 수 있지만, 다음과 같은 단점이 있을 수 있습니다:

1. 기능이 복잡해질수록 테스트 코드 작성이 부담스러워질 수 있습니다.
2. 기능이 이미 구현되어 있기 때문에, 테스트 코드가 빠뜨리는 경우가 생길 수 있습니다.
3. 이미 작성된 코드를 테스트할 때, 일부 코드가 테스트하기 어려운 구조로 설계되었을 가능성이 높아, 리팩토링을 해야 할 수도 있습니다.
#### 개발 후 테스트 코드 작성의 이점:

1. 빠르게 기능을 구현할 수 있음
2. 전체 시스템 테스트 및 통합 테스트에 용이
#### 개발 후 테스트 코드 작성의 단점:

1. 코드 커버리지가 낮아질 가능성 있음
2. 작성된 기능이 의도한 대로 동작하지 않는 경우, 버그를 찾는 데 많은 시간이 소요될 수 있음
3. 테스트 코드 작성이 미뤄지거나 생략될 가능성이 큼
### 버그 발생 시: 버그 재현 및 수정 전 테스트 작성
버그가 발생한 경우, 해당 버그를 재현할 수 있는 테스트 코드를 먼저 작성하는 것이 좋습니다. 이를 통해 다음과 같은 장점을 얻을 수 있습니다:

버그가 수정된 후에도 동일한 문제가 발생하지 않는지 지속적으로 확인할 수 있습니다.
수정한 코드가 기존 기능에 영향을 미치지 않는지 확인할 수 있습니다.
#### 버그 수정 시 테스트 코드 작성의 이점:

1. 버그 수정 여부를 정확히 검증할 수 있음
2. 동일한 문제가 재발하지 않도록 방지
#### 단점:

특정 문제를 재현하기 어려운 경우, 테스트 코드 작성이 힘들 수 있음

### 리팩토링 또는 코드 변경 시: 기존 테스트 코드 보완
리팩토링 또는 기존 코드에 대한 수정 작업을 수행할 때, 기존 테스트 코드를 재검토하고 필요한 경우 테스트 케이스를 추가하는 것이 좋습니다. 이를 통해 코드 변경이 기존 기능에 어떤 영향을 미치는지 확인할 수 있습니다.

리팩토링 작업 시 테스트 코드가 이미 작성되어 있다면, 안심하고 코드를 변경할 수 있습니다. 리팩토링 전후에 테스트가 일관되게 통과하는지 확인함으로써 코드의 안정성을 유지할 수 있습니다.

## Given-When-Then 방식으로 테스트 코드 작성하기
**Given-When-Then**은 BDD(Behavior-Driven Development)에서 테스트 시나리오를 작성할 때 사용하는 형식으로, 테스트의 가독성을 높이고 논리적인 흐름을 명확히 표현하는 데 유용합니다. 이 접근 방식은 테스트의 각 단계가 어떤 맥락에서, 어떤 동작을 수행하고, 어떤 결과를 기대하는지를 명확히 구분하여 표현합니다.

### Given-When-Then의 구성 요소
#### Given (주어진 상황)
테스트를 수행하기 위해 설정된 조건이나 상태를 설명합니다.

* 테스트에 필요한 사전 데이터 또는 객체를 준비합니다.
* 테스트의 초기 상태를 설정하거나, 특정 조건을 정의합니다.
#### When (특정 동작이 발생했을 때)
테스트하고자 하는 핵심 동작을 설명합니다.

* 함수나 메서드를 호출하거나, 이벤트를 발생시킵니다.
* 어떤 액션을 수행했을 때 어떤 변화가 일어나는지 기술합니다.
#### Then (그 결과)
기대하는 결과를 확인하는 단계로, 특정 동작이 발생한 후의 상태나 출력을 검증합니다.

* 특정 값이 기대한 대로 반환되는지 확인합니다.
* 예외가 발생하는지, 상태가 올바르게 변경되었는지를 검증합니다.

### 예시
```
import pytest

# 간단한 Account 클래스 정의
class Account:
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.balance = balance

    def deposit(self, amount):
        if amount <= 0:
            raise ValueError("Deposit amount must be positive.")
        self.balance += amount

    def withdraw(self, amount):
        if amount > self.balance:
            raise ValueError("Insufficient funds.")
        self.balance -= amount

# Given-When-Then을 사용한 테스트 코드
def test_account_deposit():
    """
    Given: 계좌가 초기 잔고 0으로 생성되었을 때
    When: 100의 금액을 입금하면
    Then: 계좌 잔고가 100이 되어야 한다.
    """
    # Given
    account = Account("Alice")

    # When
    account.deposit(100)

    # Then
    assert account.balance == 100

def test_account_withdrawal():
    """
    Given: 계좌가 초기 잔고 100으로 생성되었을 때
    When: 50의 금액을 출금하면
    Then: 계좌 잔고가 50이 되어야 한다.
    """
    # Given
    account = Account("Bob", balance=100)

    # When
    account.withdraw(50)

    # Then
    assert account.balance == 50

def test_account_overdraft():
    """
    Given: 계좌가 초기 잔고 50으로 생성되었을 때
    When: 100의 금액을 출금하려고 하면
    Then: 잔고가 부족하여 ValueError 예외가 발생해야 한다.
    """
    # Given
    account = Account("Charlie", balance=50)

    # When & Then
    with pytest.raises(ValueError, match="Insufficient funds."):
        account.withdraw(100)
```
### Given-When-Then 방식의 장점
* 가독성 향상: 테스트 코드를 읽는 사람이 시나리오를 쉽게 이해할 수 있도록 흐름을 명확히 표현합니다.
* 명확한 구조: 각 테스트 케이스가 특정 상황에서 발생하는 동작과 그 결과를 명확하게 구분하여 작성할 수 있습니다.
* 기능 중심의 테스트: 특정 기능이나 행위(behavior)에 초점을 맞춰, 명세서 또는 요구사항과 테스트 코드가 일치하는 구조를 만듭니다.
* 테스트 의도 전달 용이: 테스트의 목적이 무엇인지, 어떤 시나리오를 다루고 있는지를 쉽게 이해할 수 있도록 설명해 줍니다.

### Given-When-Then 적용 시 고려사항
* 단계 간 중복 방지: Given, When, Then 각 단계가 중복되거나 모호하지 않도록 명확히 구분해야 합니다.
* 단일 When 원칙: 하나의 테스트 케이스는 가능하면 단일한 When 동작을 테스트하는 것이 좋습니다. 복잡한 동작이 여러 개 포함되면 테스트 케이스가 불명확해질 수 있습니다.
* 간결한 표현: 각 단계는 간결하고 이해하기 쉽게 작성해야 합니다. 과도한 설정이나 복잡한 조건은 테스트의 가독성을 떨어뜨릴 수 있습니다.