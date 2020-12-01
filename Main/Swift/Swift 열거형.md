# Swift 열거형(enum)

swift에서의 열거형은 다른 언어의 열거형과 다르게 각각의 케이스가 고유의 값으로 인식

### 열거형 선언

```swift
// enum 이름 {
//    case 이름1
//    case 이름2
//    case 이름3
//    case 이름4, 이름5, 이름6 ... 
// }
enum Weekday{
    case mon
    case tue
    case wed
    case thu, fri, sat, sun
}

enum Fruit:Int{
    case apple = 0
    case banana // 1로 자동증가
    case peach // 2로 자동증가
}

enum School:String{
    case elementary = "초"
    case middle = "중"
    case high = "고"
    case college
}

// let apple: Fruit = Fruit(rowValue: 0) nil 이 될수도 있기 때문에 옵셔널 타입이 되어 오류가뜸
let apple: Fruit? = Fruit(rowValue: 0) 
if let orange: Fruit = Fruit(rawValue: 5){
    print("rowValue:5 = \(orange)")
} else {
    print("rowValue:5 = nil 이다.")
}

var day: Weekday = Weekday.mon
day.tue
print(day)

print(Fruit.peach.rowValue) // 2
print(School.elementary.rowValue) // 초
print(School.college.rowValue) // college

// 열거형 내부에 메서드를 추가 가능
enum Weekday{
    case mon
    case tue
    case wed
    case thu, fri, sat, sun
    
    func printMessage(){
        switch self {
        case .mon, .tue, .wed, .thu:
            print("평일")
        case Weekday.fri:
            print("불금")
        case .sat, .sun:
            print("주말")
        }
    }
}

Weekday.mon.printMessage() // 평일
Weekday.sun.printMessage() // 주말

```

### 열거형 switch

```swift
// 열거형의 모든 케이스를 사용하게 되면 default가 필요없음
// 하나라도 사용하지 않으면 default가 필요함
switch day{
case .mon, .tue, .wed, .thu:
    print("평일")
case Weekday.fri:
    print("불금")
case .sat, .sun:
    print("주말")
}
```

