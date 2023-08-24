dart에서 property를 선언할 때는 타입을 사용해서 정의한다.

```dart
class Player {
final String name = 'jisoung';
final int age = 17;
void sayName(){
// class method안에서는 this를 쓰지 않는 것을 권장한다.
print("Hi my name is $name")
}
}

void main(){
// new를 꼭 붙이지 않아도 된다.
var player =Player();
}
```
