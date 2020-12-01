# Swift 반복문

### for - in 

```swift
import swift

var integers = [1,2,3]
let fruits = ["apple":10, "banana":15, "coconut":20]

// for item in items{
//     code
// }
for integer in integers {
    print(integer)
}
// dictionary 는 아이템에 튜플로 들어오게됨
for (fruit, num) in fruits {
    print("\(fruit) : \(num)")
}
```

### while

```swift
// while condition{
//    code
// }

while integers.count > 1 {
    integers.removeLast()
}

// repeat-while
// repeat {
//     code
// } while condition

repeat {
    integers.removeLast()
} while integers.count > 0
```

