## basic data types
기본 데이터 타입

아래 타입을 포함한 거의 대부분의 타입들이 객체로 이루어져 있다. (함수도 객체)
이것이 Dart가 진정한 객체 지향 언어로 불리는 이유이다.
```
void main() {
String name = "tom";
bool isPlay = true;
int age = 10;
double money = 52.55;
num x = 12;
num y = 1.2;
}
```


## List
List를 사용하는 2가지 방법
```
void main() {
List numbers = [1, 2, 3];
var number2 = [4, 5, 6];
}
```

List는 collection if와 collection for를 지원한다.
collection if는 List를 만들 때, if를 통해 존재할 수도 안 할 수도 있는 요소를 가지고 만들 수 있다.
```
void main() {
var giveMeFive = true;
var item = [
1,
2,
3,
if (giveMeFive) 10, // giveMeFive가 true이면 10을 넣음
];
print(item);
}
```
https://dart.dev/guides/language/language-tour#collection-operators


## String Interpolation
변수 사용하는 방법

$달러 기호를 붙이고 사용할 변수를 적어주면 된다.
만약 무언가를 계산하고 싶다면 ${ } 형태로 적어주면 된다.
```
void main(){
var name = "tom";
var age = 10;
var greeting = "hello $name, I'm ${age + 5}";
}
```


## Collection For
Collection For

Dart는 조건문(if) 및 반복(for)을 사용하여 컬렉션을 구축하는 데 사용할 수 있는 컬렉션 if 및 컬렉션 for도 제공한다.
```
void main() {
var oldFriends = ["nico", "lynn"];
var newFriends = [
"tom",
"jon",
for (var friend in oldFriends) "❤️ $friend"
];

print(newFriends); // [tom, jon, ❤️ nico, ❤️ lynn]
}
```


## Maps
Maps

일반적으로 맵은 key와 value를 연결하는 객체입니다. 키와 값 모두 모든 유형의 객체가 될 수 있다. 
각 키는 한 번만 발생하지만 동일한 값을 여러 번 사용할 수 있다.
```
var gifts = {
// Key: Value
'first': 'partridge',
'second': 'turtledoves',
'fifth': 'golden rings'
};

// Map 생성자를 사용하여 동일한 객체를 만들 수 있다.
var gifts2 = Map();
gifts2['first'] = 'partridge';
gifts2['second'] = 'turtledoves';
gifts2['fifth'] = 'golden rings';
```


## Sets
set도 두 가지 방법으로 정의할 수 있다.
1. var을 사용
var numbers = {1, 2, 3};
2. 자료형 명시
Set numbers = {1, 2, 3};

list는 대괄호를 쓰며 set은 중괄호를 쓴다는 것과 set의 요소들은 유니크하다는 것이다. list는 같은 요소가 여러개 반복될 수 있지만, 
set은 중복이 허용되지 않는다.
