# Swift 데이터타입



````swift
import swift

// 불리언 타입
var someBool: Bool = true
// 정수 타입
var someInt: Int = -100
// 부호가 없는 정수
var someUInt: UInt = 100
// Float 타입
var someFloat: Float = 3.14
// Double 타입
var someDouble: Double = 3.14
// 문자 (한글자)
var someCharacter: Character = "가"
// 문자열 (String) (+를 통해 문자를 합칠 수 있음)
var someString: String = "문자열"

// 데이터타입 간의 자료 교환은 불가능 하다고 생각하면 될듯.

// Any 타입
var someAny: Any = 100
someAny = "모든타입 가능"
someAny = 111.11
// Any를 다른 타입의 값으로 옮기는 것은 불가능

// AnyObject (클래스 인스턴스만 가능)
class SomeClass {}
var someAnyObject: AnyObject = SomeClass()

// nil(null ,none , 빈값)
// someAny = nil (불가능)
// someAnyObject = nil (불가능)

````

