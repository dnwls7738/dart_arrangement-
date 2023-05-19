# dart_arrangement

## var

dart에서는 변수를 var 키워드 또는 명시적 타입을 사용해 만든다
당연한 말이지만 다른 타입의 변수는 서로 대입할 수 없다.
보통 함수나 메소드 내부에 '지역변수' 를 지정할 때는 var를 사용
클래스에서 '변수' 나 '프로퍼니' 를 선언할 때는 명시적 타입을 사용
var를 사용하는게 dart 스타일가이드의 권장 방식


## dynamic

dart는 '여러 타입을 가질 수 있는' dynamic 타입을 지원한다.
만약 변수를 선언할 떄 아무런 값을 지정하지 않거나, 타입을 선언하지 않으면 자동적으로 dynamic 타입을 가진다.
대표적으로 타입을 알기가 힘들 때 사용 (예시로 json을 작업할 때)
하지만 dynamic 타입은 다양한 타입을 가질 수 있기 때문에 '정말 필요할 때만' 사용


## nullable variables

null safety는 개발자가 null 값을 참조할 수 없게 하는 것이다.

다음 코드를 보자.
```dart
bool isEmpty(String string) => string.length == 0;

main(){
isEmpty(null);
}
```
다음과 같은 코드는 어떻게 실행될까?

정답은 NoSuchMethodError를 실행한다. 왜 이렇게 실행될까?
바로 String을 보내야 할 곳에 null을 보냈기 때문이다.
null에는 length라는 속성이 없기 때문이기도 하다.

이와 같은 에러는 컴파일러에서 잡을 수 있는 에러가 아니다.
이런 상황이 발생하지 않도록 null를 삭제하기에는 null 값은 유용하다.

그럼 어떻게 null 값을 참조하는 것을 dart는 어떻게 보호할까?
dart에서는 변수가 null이 될 수 있음을 명확히 표시해야한다.

다음 코드를 보자

```dart
void main(){
String name = "woo";
name = null;
}
```

이 코드는 에러가 난다. name이 null 값을 참조할 수 있다고 알려주지 않고 null 값을 참조하기 때문이다.

그러면 다음 코드를 보자.

```dart
void main(){
String? name = "woo";
name = null;
}
```

이 코드는 에러가 나지 않는다. 차이점이 보이는가? 바로 `?`를 사용해 이 변수에는 null이 참조될 수 있음을 알려주는 것이다. 만약 `?`를 붙인 변수는 이 변수가 null인지 아닌지 확인해야 한다.

```dart
void main(){
String? name = "woo";
name = null;
if(nico != null){
nico.isNotEmpty;
}


## final variables

만약 한 번 정의된 변수를 수정을 하지 못하게 하고 싶다면 어떻게 해야할까?
dart에서는 final을 사용하면 된다.
```dart
final name = "woo"
```
자바스크립트의 'const'와 정확하게 일치하는 키워드다.


## late variables

late는 final 혹은 var 앞에 붙이는 수식어다.
late는 초기 데이터 없이 선언을 할 수 있게 해준다.

```dart
void main(){
late final String name;

name = "woo";
// 에러!
name = 16
}
```

late 변수는 값을 할당되기 전에는 접근할 수 없다.
late 변수는 data fetching을 할 때 매우 유용하게 사용된다.
왜냐하면 fianl 키워드를 혼자 사용하면 바로 선언을 해야하지만 late 키워드를 사용한다면 선언이 아닌 할당을 하더라도 그 변수의 수정을 막을 수 있기 때문이다.


## constant variables

dart의 상수는 자바스크립트와 다르다.
자바스크립트의 상수는 dart의 fianl과 같다.
dart의 const는 compoile-time constant를 만들어 준다.
const와 fianl의 가장 큰 차이점은 컴파일이 되는 시점에 그 값을 알 수 있는지 없는지의 차이다.

예를 들어 fetchApi를 하는 변수는 컴파일하는 시점에 그 변수를 알 수가 없다.

```dart
// 컴파일하는 시점에는 API의 값을 알 수 없다
const API = fetchAPI()
```

위 코드의 경우에는 const가 아닌 final이 더 적합하다.

final를 쓰는 대표적인 경우는
API fetching, 사용자가 화면에서 입력해야하는 값 등이 있다.

const를 쓰는 대표적인 경우는
max_allowed_price와 같은 상수에 쓰인다.
