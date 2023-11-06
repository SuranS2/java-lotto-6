**2주 차 공통 피드백**

README.md를 상세히 작성한다
미션 저장소의 README.md는 소스코드에 앞서 해당 프로젝트가 어떠한 프로젝트인지 마크다운으로 작성하여 소개하는 문서이다.
해당 프로젝트가 어떠한 프로젝트이며, 어떤 기능을 담고 있는지 기술하기 위해서 마크다운 문법을 검색해서 학습해 보고 적용해 본다.

기능 목록을 재검토한다
기능 목록을 클래스 설계와 구현, 함수(메서드) 설계와 구현과 같이 너무 상세하게 작성하지 않는다. 클래스 이름,
함수(메서드) 시그니처와 반환값은 언제든지 변경될 수 있기 때문이다.
너무 세세한 부분까지 정리하기보다 구현해야 할 기능 목록을 정리하는 데 집중한다. 정상적인 경우도 중요하지만, 예외적인 상황도 기능 목록에 정리한다.
특히 예외 상황은 시작 단계에서 모두 찾기 힘들기 때문에 기능을 구현하면서 계속해서 추가해 나간다.

기능 목록을 업데이트한다
README.md 파일에 작성하는 기능 목록은 기능 구현을 하면서 변경될 수 있다.
시작할 때 모든 기능 목록을 완벽하게 정리해야 한다는 부담을 가지기보다 기능을 구현하면서 문서를 계속 업데이트한다.
죽은 문서가 아니라 살아있는 문서를 만들기 위해 노력한다.

값을 하드 코딩하지 않는다
문자열, 숫자 등의 값을 하드 코딩하지 마라. 상수(static final)를 만들고 이름을 부여해 이 변수의 역할이 무엇인지 의도를 드러내라.
구글에서 "java 상수"와 같은 키워드로 검색해 상수 구현 방법을 학습하고 적용해 본다.

구현 순서도 코딩 컨벤션이다
클래스는 상수, 멤버 변수, 생성자, 메서드 순으로 작성한다.

class A {
상수(static final) 또는 클래스 변수

    인스턴스 변수

    생성자

    메서드
}

변수 이름에 자료형은 사용하지 않는다
변수 이름에 자료형, 자료 구조 등을 사용하지 마라.

String carNameList = Console.readLine();
String[] arrayString = carNameList.split(",");

한 함수가 한 가지 기능만 담당하게 한다
함수 길이가 길어진다면 한 함수에서 여러 일을 하려고 하는 경우일 가능성이 높다. 아
래와 같이 한 함수에서 안내 문구 출력, 사용자 입력, 유효값 검증 등 여러 일을 하고 있다면 이를 적절하게 분리한다.

public List<String> userInput() {
System.out.println("경주할 자동차 이름을 입력하세요(이름은 쉼표(,)를 기준으로 구분).");
String userInput = Console.readLine().trim();
String[] splittedName = userInput.split(",");
for (int index = 0; index < splittedName.length; index++) {
if (splittedName.length < 1 || splittedName.length > 5) {
throw new IllegalArgumentException("[ERROR] 자동차 이름은 1자 이상 5자 이하만 가능합니다.");
}
}
return Arrays.asList(splittedName);
}

함수가 한 가지 기능을 하는지 확인하는 기준을 세운다
만약 여러 함수에서 중복되어 사용되는 코드가 있다면 함수 분리를 고민해 본다.
또한, 함수의 길이를 15라인을 넘어가지 않도록 구현하며 함수를 분리하는 의식적인 연습을 할 수 있다.

테스트를 작성하는 이유에 대해 본인의 경험을 토대로 정리해본다
단지 기능을 점검하기 위한 목적으로 테스트를 작성하는 것은 아니다.
테스트를 작성하는 과정을 통해서 나의 코드에 대해 빠르게 피드백을 받을 수 있을 뿐만 아니라
학습 도구(학습테스트를 통해 JUnit 학습하기.pdf)로도 활용할 수 있다. 이런 경험을 통해 테스트에 대해 어떤 유용함을 느꼈는지 알아본다.

처음부터 큰 단위의 테스트를 만들지 않는다
테스트의 중요한 목적 중 하나는 내가 작성하는 코드에 대해 빠르게 피드백을 받는 것이다.
시작부터 큰 단위의 테스트를 만들게 된다면 작성한 코드에 대한 피드백을 받기까지 많은 시간이 걸린다.
그래서 문제를 작게 나누고, 그 중 핵심 기능에 가까운 부분부터 작게 테스트를 만들어 나간다.

큰 단위의 테스트
자동차경주를 시작해서 사용자가 이름, 진행 횟수를 입력하면, 게임을 진행한 후 그 결과를 알려준다.

작은 단위의 테스트
무작위 값이 4 이상이면 자동차가 전진한다.
무작위 값이 3 이하이면 자동차가 전진하지 않는다.

**1주 차 공통 피드백**
요구사항을 정확히 준수한다

커밋 메시지를 의미 있게 작성한다

git을 통해 관리할 자원에 대해서도 고려한다

.class 파일은 java 코드가 있으면 생성할 수 있다. 따라서 .class 파일은 굳이 git을 통해 관리하지 않아도 된다.

Pull Request를 보내기 전 브랜치를 확인한다

기능 구현 작업을 fork된 Repository의 main branch가 아닌, 기능 구현을 위해 새로 만든 브랜치에서 작업한 후 PR을 보낸다.
PR을 한 번 작성했다면 닫지 말고
추가 커밋을 한다
PR을 이미 한 번 보냈다면, 새로운 PR을 생성할 필요가 없다

이름을 통해 의도를 드러낸다
나 자신, 다른 개발자와의 소통을 위해 가장 중요한 활동 중의 하나가 좋은 이름 짓기이다
연속된 숫자를 덧붙이거나(a1, a2, ..., aN), 불용어(Info, Data, a, an, the) 사용하면 기계적인 이름짓기다

축약하지 않는다
의도를 드러낼 수 있다면 이름이 길어져도 괜찮다.
Order라면 shipOrder라고 메서드 이름을 지을 필요가 없다.
짧게 ship()이라고 하면 클라이언트에서는 order.ship()라고 호출하며, 간결한 호출의 표현이 된다.
- 객체 지향 생활 체조 원칙 5: 줄여쓰지 않는다 (축약 금지)
  공백도 코딩 컨벤션이다
  if, for, while문 사이의 공백도 코딩 컨벤션이다.
-
공백 라인을 의미 있게 사용한다
space와 tab을 혼용하지 않는다
의미 없는 주석을 달지 않는다
-
IDE의 코드 자동 정렬 기능을 활용한다
IntelliJ IDEA: ⌥⌘L, Ctrl+Alt+L
Eclipse: ⇧⌘F, Ctrl+Shift+F
-
Java에서 제공하는 API를 적극 활용한다
예를 들어 사용자를 출력할 때 사용자가 2명 이상이면 쉼표(,) 기준으로 출력을 위한 문자열은 다음과 같이 구현 가능하다.
List<String> members = Arrays.asList("pobi", "jason");
String result = String.join(",", members); // "pobi,jason"

배열 대신 Java Collection을 사용한다
Java Collection 자료구조(List, Set, Map 등)



1주차 코드리뷰 피드백
1. flag 보다는 isEnd 라던가 정확히 그 변수가 어떤 스위치 역할을 하는지 네이밍 해주시면 좋아보입니다!
2. 100이라는 매직넘버 대신에, 원시값을 포장하거나 enum값으로 사용하면 더욱 좋았을 것 같습니다!
3. 스트링을 인트형으로 그대로 받아버리면 예외검사나 숫자비교할때 필요한 프로세스가 너무 많아질것같습니다. ArrayList 자료형을 추천드립니다.
4. if문에서 한번에 3가지 숫자를 체크하고 있는데 분리해서 작성하는 것은 어떨까요?
5. 이중 for문을 사용하는 것 보다 stream을 사용해서 더 간결하게 표현할 수 있을 것 같아요!
6. 출력값 고려하기
7. 중복된 값을 조건에 넣을 경우. 변수를 선언해 저장해서 사용하는 것이 좀더 가독성있게될거에요.

2주차 코드리뷰 피드백
1. 상수 메시지를 담은 객체이니 다른 클래스명을 생각해보면 어떨까요?
2. 전진/스탑 메소드 메소드명
3. CLI 입출력이 아니라 파일 입출력 환경으로 바뀐다면 System.out.println()을 모두 고쳐야할 것 같습니다.
4. 이름을 변경하는 기능이 없으니 생성자에서 설정하면 어떨까요?
5. matches 내부에서 사용되는 Pattern 객체의 생성 비용이 비쌉니다. 한 번 쓰고 버려지는데, 아까우니 컴파일해서 캐싱하는 게 어떨까요?(자료 검수하는 메소드
6. Error보다 Exception 타입으로 반환하면 어떨까요? 구체적인 예외를 반환해보는 것도 좋지 않을까...합니다.
7. 외부 라이브러리 변경 가능성을 고려해서 래핑하면 어떨까요?
   collect(Collectors.toList()) 는 ArrayList
   toList() 는 Collectors.UnmodifiableList 또는 Collectors.UnmodifiableRandomAccessList (수정불가)를 반환
   모각코 답변도 감사합니다.

