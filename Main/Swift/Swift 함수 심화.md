# Swift 함수 심화

### 매개변수의 기본값 부여

````swift
import swift

func greeting(friend: String, me:String="Lee"){
    print("hello \(friend) I'm \(me)")
}
greeting(friend: "tom") // hello tom I'm Lee
greeting(friend: "tom", me:"Kim") // hello tom I'm Kim
````



### 전달인자 레이블

````swift
import swift

func greeting(to friend: String, from me: String){
    print("hello \(friend) I'm \(me)")
}
greeting(to: "tom", from:"Kim") // hello tom I'm Kim
````



### 가변 매개변수

````swift
import swift

func hello(me: String, friends: String ...) -> String{
    return print("hello \(friends) I'm \(me)")
}
print(hello(me: "tom", friends:"Kim")) // hello ["Kim"] I'm tom
print(hello(me: "tom", friends:"kim", "lee", "park", "choi")) // hello ["kim", "lee", "park", "choi"] I'm tom
print(hello(me: "tom")) // hello [] I'm tom
````



### 데이터 타입으로 함수

````swift
import swift

var someFunc: (String, String) -> Void = greeting(to:from:)
someFunc("tom", "Kim") // hello tom I'm Kim
someFunc = greeting(friend:me:)
someFunc("Kim", "tom") // hello Kim I'm tom
// 리턴, 인풋타입이 다른 함수는 할당할 수 없다.

// 함수로 함수를 넘겨줄 수 도 있다.
func runAnother(function(String, String) -> Void){
    function("Kim", "Lee")
}
runAnother(function: greeting(friend:me:)) // hello Kim I'm Lee
runAnother(function: someFunc) // hello Kim I'm Lee
````

