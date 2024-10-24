# java-racingcar-precourse
## 기능 요구 사항
초간단 자동차 경주 게임을 구현한다.
- 주어진 횟수 동안 n대의 자동차는 전진 또는 멈출 수 있다.
- 각 자동차에 이름을 부여할 수 있다. 전진하는 자동차를 출력할 때 자동차 이름을 같이 출력한다.
- 자동차 이름은 쉼표(,)를 기준으로 구분하며 이름은 5자 이하만 가능하다.
- 사용자는 몇 번의 이동을 할 것인지를 입력할 수 있어야 한다.
- 전진하는 조건은 0에서 9 사이에서 무작위 값을 구한 후 무작위 값이 4 이상일 경우이다.
- 자동차 경주 게임을 완료한 후 누가 우승했는지를 알려준다. 우승자는 한 명 이상일 수 있다.
- 우승자가 여러 명일 경우 쉼표(,)를 이용하여 구분한다.
- 사용자가 잘못된 값을 입력할 경우 IllegalArgumentException을 발생시킨 후 애플리케이션은 종료되어야 한다.

## 기능 목록
### <Model (도메인)>
**1. Car 클래스**
- 자동차의 이름과 현재 위치를 관리.
- 전진하는 메서드 (move)를 구현하여 랜덤 값에 따라 자동차의 위치를 업데이트.
  
**2. RacingGame 클래스**
- 자동차 리스트와 시도 횟수를 관리.
- 각 라운드에서 자동차의 이동을 처리하는 메서드 (playRound) 구현.
- 최대 위치를 가진 자동차를 찾아 우승자를 결정하는 메서드 (getWinners) 구현.
- 남은 시도 횟수를 확인하는 메서드 (hasMoreTrials) 구현.

### <View (입출력)>
**1. InputView 클래스**
- 사용자로부터 자동차 이름을 입력받는 메서드 (inputCarNames) 구현.
- 사용자로부터 시도 횟수를 입력받는 메서드 (inputTrialCount) 구현.
- 사용자에게 입력 요청 메시지를 출력하는 기능 포함.

**2. OutputView 클래스**
- 각 라운드에서 자동차의 현재 위치를 출력하는 메서드 (printRoundResult) 구현.
- 최종 우승자를 출력하는 메서드 (printWinners) 구현.

### <Controller (컨트롤러)>
**1. RacingGameController 클래스**
- 게임의 전체 흐름을 관리.
- 사용자 입력을 받고, 입력 검증을 수행한 후, 게임을 시작하는 메서드 (start) 구현.
- 라운드 진행을 관리하고 결과를 뷰를 통해 출력하는 메서드 (playGame, printWinners) 구현.

### <Validator (검증)>
**1. InputValidator 클래스**
- 사용자 입력값 검증:
  - 자동차 이름의 형식 및 길이 검증. (이름은 쉼표로 구분, 5자 이하)
  - 시도 횟수의 유효성 검증 (0 이상의 정수여야 함).

## 프로그래밍 요구 사항 1
- JDK 21 버전에서 실행 가능해야 한다.
- 프로그램 실행의 시작점은 Application의 main()이다.
- build.gradle 파일은 변경할 수 없으며, 제공된 라이브러리 이외의 외부 라이브러리는 사용하지 않는다.
- 프로그램 종료 시 System.exit()를 호출하지 않는다.
- 프로그래밍 요구 사항에서 달리 명시하지 않는 한 파일, 패키지 등의 이름을 바꾸거나 이동하지 않는다.
- 자바 코드 컨벤션을 지키면서 프로그래밍한다.
- 기본적으로 Java Style Guide를 원칙으로 한다.

## 프로그래밍 요구 사항 2
- indent(인덴트, 들여쓰기) depth를 3이 넘지 않도록 구현한다. 2까지만 허용한다.
  - 예를 들어 while문 안에 if문이 있으면 들여쓰기는 2이다.
  - 힌트: indent(인덴트, 들여쓰기) depth를 줄이는 좋은 방법은 함수(또는 메서드)를 분리하면 된다.
- 3항 연산자를 쓰지 않는다.
- 함수(또는 메서드)가 한 가지 일만 하도록 최대한 작게 만들어라.
- JUnit 5와 AssertJ를 이용하여 정리한 기능 목록이 정상적으로 작동하는지 테스트 코드로 확인한다.
  - 테스트 도구 사용법이 익숙하지 않다면 아래 문서를 참고하여 학습한 후 테스트를 구현한다.
    - JUnit 5 User Guide
    - AssertJ User Guide
    - AssertJ Exception Assertions
    - Guide to JUnit 5 Parameterized Tests
#### 라이브러리
- camp.nextstep.edu.missionutils에서 제공하는 Randoms 및 Console API를 사용하여 구현해야 한다.
  - Random 값 추출은 camp.nextstep.edu.missionutils.Randoms의 pickNumberInRange()를 활용한다.
  - 사용자가 입력하는 값은 camp.nextstep.edu.missionutils.Console의 readLine()을 활용한다.
##### 사용 예시
- 0에서 9까지의 정수 중 한 개의 정수 반환
  - Randoms.pickNumberInRange(0, 9);
