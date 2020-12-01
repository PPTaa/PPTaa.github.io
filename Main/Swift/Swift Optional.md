# Swift Optional(옵셔널)

값이 있을수도 있고 없을 수도 있음

### 옵셔널이 필요한 이유 

> nil의 가능성을 명시적으로 표현
>
> 전달받은 값이 옵셔널이 아니라면 nil체크를 하지 않아도 됨

```swift
import swift

// 선언
let optionalValue: Optional<Int> = nil
let optionalValue: Int? = nil 

func someFunc(OptionalParam: Int?){
    // ...
}
func someFunc(nomalParam: Int){
    // ...
}

someFunc(OptionalParam : nil)
// someFunc(nomalParam : nil) 불가능
```

### Optional ?, !

##### ! (Implicitly Unwrapped Optional) : 암시적 추출 옵셔널

```swift
var optionalValue Int! = 100
switch optionalValue {
case .none:
	print("nil")
case .some(let value):
	print("value is \(value)")
} 
// 기존 변수처럼 사용가능
// nil 할당 가능
// 잘못된 접근으로 인한 런타임 오류 발생
```

##### ? (Optional) : 일반적인 옵셔널

```swift
var optionalValue Int? = 100
switch optionalValue {
case .none:
	print("nil")
case .some(let value):
	print("value is \(value)")
} 
// nil 할당 가능
// 기존 변수처럼 사용이 불가(타입이 다르기 때문에 연산이 불가능)
```



### Optional Unwrapping

- Optional Binding : 옵셔널 바인딩 (옵셔널의 값을 꺼내오는 방법중 하나, nil체크를 하며 안전한 값을 추출한다.)

##### if - let 방식의 옵셔널 바인딩 (추천방식!)

```swift
func printName(_ name: String){
    print(name)
}

var myName: String? = nil

if let name: String = myName {
    print(name)
} else {
    print("myName == nil")
}

// 한번에 여러개의 바인딩도 가능
var myName: String? = nil
var yourName: String? = "Lee"

if let myname = myName, let yourname = yourName {
    print(myname, yourname)
} else {
    print("myName == nil or yourName == nill")
}
```

- Force Unwrapping : 강제 추출(옵셔널의 값을 강제로 추출한다.) 

```swift
func printName(_ name: String){
    print(name)
}

var myName: String? = "Lee"
printName(myName!) // Lee
myName = nil
printName(myName!) // nil값이므로 런타임 오류 발생

var yourName: String! = nil
print(yourName) // nil값이므로 런타임 오류 발생
```

