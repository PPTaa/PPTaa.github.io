# Swift 함수 기본

## 기본적인 함수 선언

### 기본 함수

````swift
import swift

// func 함수 이름(매개변수1: 타입, 매개변수2: 타입) -> 리턴타입{
//    함수 구현
//    return 함수 반환
//}

func sum(a: Int, b: Int) -> Int{
    return a+b
}
````



### 반환값이 없는 함수 

````swift
// 1)
// func 함수 이름(매개변수1: 타입, 매개변수2: 타입) -> void{
//    함수 구현
//}

func printStr(Str: String) -> void{
    print(Str) 
}

// 2) void 생략가능
// func 함수 이름(매개변수1: 타입, 매개변수2: 타입) {
//    함수 구현
//}

func printStr(Str: String) {
    print(Str) 
}
````



### 매개변수가 없는 함수 

````swift
// func 함수 이름() -> Int{
//    함수 구현
//    return 함수 반환
//}

func printInt() -> Int{ 
    return Int.max
}
````



### 매개변수 반환값 둘다 없는 함수

````swift
// func 함수 이름() {
//    함수 구현
//}

func hello() { print("hello") }
````



## 함수의 호출



````swift
sum(a:1, b:6)
printStr(Str: "HelloWorld")
printInt()
hello()
````



