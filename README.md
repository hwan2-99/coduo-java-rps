# 미션 - 가위바위보 게임

# 🔍 진행 방식

- 미션은 기능 요구 사항, 프로그래밍 요구 사항 두 가지로 구성되어 있다.
- 두 개의 요구 사항을 만족하기 위해 노력한다.
- 기능 요구 사항에 기재되지 않은 내용은 스스로 판단하여 구현한다.
- 기능 구현을 완료한 뒤 아래 가이드에 따라 테스트를 실행했을 때 모든 테스트가 성공하는지 확인한다.

## 테스트 실행 가이드

- 터미널에서 java -version을 실행하여 Java 버전이 17인지 확인한다. Eclipse 또는 IntelliJ IDEA와 같은 IDE에서 Java 17로 실행되는지 확인한다.
- 터미널에서 Mac 또는 Linux 사용자의 경우 ./gradlew clean test 명령을 실행하고, Windows 사용자의 경우 gradlew.bat clean test 또는 ./gradlew.bat
  clean test 명령을 실행할 때 모든 테스트가 아래와 같이 통과하는지 확인한다.

```aiignore
BUILD SUCCESSFUL in 0s
```

# 🚀 기능 요구 사항

이 게임에서는 컴퓨터와 가위바위보 대결을 펼치게 됩니다. 게임의 규칙과 진행 방식은 다음과 같습니다.

사용자는 컴퓨터와 가위바위보 게임을 진행하며 정해진 횟수만큼 컴퓨터를 이기면 승리합니다. 컴퓨터는 무작위로 가위, 바위, 보 중 하나를 선택하고, 사용자는 가위, 바위, 보 중 하나를 입력해 승패를 가립니다.

- 사용자는 게임에서 이겨야 할 횟수를 선택합니다. 이 횟수는 최대 5회 이하로 설정할 수 있습니다.
- 게임이 시작되면, 매 입력마다 컴퓨터는 무작위로 가위, 바위, 보 중 하나를 선택합니다.
- 사용자는 가위, 바위, 보 중 하나를 선택하여 입력합니다.
- 컴퓨터와 사용자의 선택을 비교하여 승패를 가립니다. 승패 규칙은 다음과 같습니다.
    - 가위 vs 보 → 가위 승리
    - 바위 vs 가위 → 바위 승리
    - 보 vs 바위 → 보 승리
    - 만약 같은 선택을 하면 무승부로 처리됩니다.
- 사용자가 이겨야 하는 횟수만큼 승리하면 게임이 종료됩니다.
- 만약 사용자가 잘못된 입력을 하면 예외가 발생하며, 게임은 즉시 종료됩니다.
    - 예외는 `IllegalArgumentException`을 발생시킵니다.

## 입출력 요구 사항

### 입력

게임에서 이겨야 할 횟수 입력

```aiignore
승리를 위한 횟수를 입력하세요: 3
```

가위, 바위, 보 중 하나의 문자열 입력

```aiignore
가위, 바위, 보 중 하나를 입력하세요: 가위
```

### 출력

게임 시작 문구 출력

```aiignore
가위바위보 게임을 시작합니다.
```

각 차수별 실행 결과

```aiignore
# 컴퓨터가 승리한 경우
상대방은 가위를 제출했습니다. 상대방이 승리했습니다!

# 사용자가 승리한 경우
상대방은 가위를 제출했습니다. 당신이 승리했습니다!

# 무승부인 경우
상대방은 가위를 제출했습니다. 무승부입니다!
```

게임 승리 문구 출력

```aiignore
가위바위보 게임을 승리했습니다! 게임 종료
```

### 프로그램 실행 결과 예시

```aiignore
가위바위보 게임을 시작합니다.

승리를 위한 횟수를 입력하세요: 1

가위, 바위, 보 중 하나를 입력하세요: 가위
상대방은 바위를 제출했습니다. 상대방이 승리했습니다!

가위, 바위, 보 중 하나를 입력하세요: 보
상대방은 보를 제출했습니다. 무승부입니다!

가위, 바위, 보 중 하나를 입력하세요: 바위
상대방은 가위를 제출했습니다. 당신이 승리했습니다!

가위바위보 게임을 승리했습니다! 게임 종료
```

# 🎯 프로그래밍 요구 사항

## 구현 환경

- JDK 17 버전에서 실행 가능해야 한다.
- 프로그램 실행의 시작점은`Application`의`main()`이다.
- `build.gradle`파일을 변경할 수 없고, 외부 라이브러리를 사용하지 않는다.
- 프로그램 종료 시`System.exit()`를 호출하지 않는다.
- 프로그램 구현이 완료되면`ApplicationTest`의 모든 테스트가 성공해야 한다.
- 프로그래밍 요구 사항에서 달리 명시하지 않는 한 기본 제공되는 파일, 패키지 이름을 수정하거나 이동하지 않는다.
- 프로그램 구현이 완료되면 ApplicationTest의 모든 테스트가 성공해야 한다.

## Code Style

- indent(인덴트, 들여쓰기) depth를 3이 넘지 않도록 구현한다. 2까지만 허용한다.
    - 예를 들어 while문 안에 if문이 있으면 들여쓰기는 2이다.
    - 힌트: indent(인덴트, 들여쓰기) depth를 줄이는 좋은 방법은 함수(또는 메서드)를 분리하면 된다.
- 3항 연산자를 쓰지 않는다.
- 함수(또는 메서드)의 길이가 15라인을 넘어가지 않도록 구현한다.
    - 함수(또는 메서드)가 한 가지 일만 잘 하도록 구현한다.
- else 예약어를 쓰지 않는다.
    - 힌트: if 조건절에서 값을 return하는 방식으로 구현하면 else를 사용하지 않아도 된다.
    - else를 쓰지 말라고 하니 switch/case로 구현하는 경우가 있는데 switch/case도 허용하지 않는다.

## 라이브러리

- `java.rps.util.coduo` 패키지에 존재하는 `RandomTool` 및 `Console` 클래스의 메서드를 사용해서 미션을 구현해야 한다.
    - 가위, 바위, 보 중 하나의 선택지를 랜던으로 추출하기 위해 `RandomTool`의 `pickRSP()`를 활용한다.
        - "rock", "scissors", "paper" 중 하나의 문자열이 랜덤하게 반환된다.
    - 사용자의 입력을 받기위해 `Console`의 `input()`을 활용한다.
        - 사용자의 입력을 문자열 값으로 받아 반환한다.
        - 모든 사용자 입력은 해당 클래스를 사용해 구현한다.

```java
final String randomRSP = RandomTool.pickRSP();
final String input = Console.input();
```
