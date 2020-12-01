# Swift 클래스

### 구조체vs클래스

> 구조체 : 값타입
>
> 클래스 : 참조타입 (다중상속이 되지않음)

### 클래스 선언

```swift
// class 이름 {
//     구현부
// }
class Sample {
    // 인스턴스 프로퍼티
    var mutableProperty: Int = 100 // 가변 프로퍼티
    let immutableProperty: Int = 100 // 불변 프로퍼티
    
    static var typeProperty: Int = 100 // 타입 프로퍼티
    
    // 인스턴스 메소드
    func instanceMethod(){
        print("instanceMethod")
    }
    
    // 타입 메소드
    // 재정의 불가 타입메소드 - static
    static func typeMethod(){
        print("typeMethod - static")
    }
    
    // 재정의 가능 타입메소드 - static
    class func classMethod(){
        print("typeMethod - class")
    }
}
```

### 클래스 사용

```swift
var mutableReference: Sample = Sample()

mutableReference.mutableProperty = 200
// mutableReference.immutableProperty = 200 불변이라 불가

let immutableReference: Sample = Sample()

immutableReference.mutableProperty = 200 // 가능
// immutableReference.immutableProperty = 200 불변이라 불가

Sample.typeProperty = 200
Sample.typeMethod() // typeMethod - static
```

### 클래스 예시

```swift
class School {
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

let kimchi: School = School()
kimchi.student = "LEE"
kimchi.selfIntroduce() // 저는 LEE 이고, Math과목을 듣습니다.
```

