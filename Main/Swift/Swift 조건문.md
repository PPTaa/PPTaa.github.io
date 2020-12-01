# Swift 조건문

### if - else 구문

```swift
import swift

// if condition {
//     statement
// } else if condition {
//     statement
// } else {
//     statement
// }

if someInt < 100 {
    print("100 미만")
} else if someInt>100{
    print("100 초과")
} else {
    print("100")
}
```

### switch 구문

````swift
import swift

// 정수타입 외의 대부분의 기본타입들을 사용할 수 있음
// default 가 없으면 동작을 안함
// break는 기본적으로 작동
// switch value {
// case pattern:
//     code
// default:
//     code
// }

switch someInt {
case 0:
    print("0")
case 1..<100: // ..< 이상, 미만
    print("1~99")
case 100:
    print("100")
case 101...Int.max: // ... 이상, 이하
    print("over 100")
default:
    print("unknown")
}
````

