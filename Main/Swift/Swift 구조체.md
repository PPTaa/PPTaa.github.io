# Swift 구조체

### 구조체 선언

```swift
// struct 이름 {
//     구현부
// }
struct Sample {
    // 인스턴스 프로퍼티
    var mutableProperty: Int = 100 // 가변 프로퍼티
    let immutableProperty: Int = 100 // 불변 프로퍼티
    
    static var typeProperty: Int = 100 // 타입 프로퍼티
    
    // 인스턴스 메소드
    func instanceMethod(){
        print("instanceMethod")
    }
    
    // 타입 메소드
    static func typeMethod(){
        print("typeMethod")
    }
}
```

### 구조체 사용

```swift
// 가변 인스턴스
var mutable: Sample = Sample()
mutable.mutableProperty = 200
// mutable.immutableProperty = 200 불변프로퍼티는 변환이 불가

// 불변 인스턴스
let mutable: Sample = Sample()

// mutable.mutableProperty = 200 불변 인스턴스이기 때문에 변환이 불가능
// mutable.immutableProperty = 200 

// 타입 프로퍼티 및 메소드
Sample.typeProperty = 300
Sample.typeMethod() // 타입 메소드

// 인스턴스에서는 타입 프로퍼티와 메소드 사용불가
// mutable.typeProperty = 300  불가

```



### 구조체 예시

```swift
struct School {
    var student : String = "Park"
    var object: String = "Math"
    
    static func selfIntroduce(){
        print("학교타입입니다.")
    }
    
    func selfIntroduce(){
        print("저는 \(student) 이고, \(object)과목을 듣습니다.")
    }
}

School.selfIntroduce() // 학교타입입니다.
var dawon: School = School()
dawon.student = "KIM"
dawon.object = "COM"
dawon.selfIntroduce() // 저는 KIM 이고, COM과목을 듣습니다.
```

