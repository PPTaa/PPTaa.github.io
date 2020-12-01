# Swift 컬렉션 타입


### Array
````swift
import swift

// 빈 Array 선언
var intArray: Array<Int> = Array<Int>()
intArray.append(1)
intArray.append(100)
// intArray.append(111.11)

// Array에 있는가?
intArray.contains(100)
intArray.contains(10)

// Array에서 삭제   
intArray.remove(at: 0)
intArray.removeLast() // 마지막 요소
intArray.removeAll()

// Array요소 수
intArray.count

//빈 Array생성
var doubles: Array<Double> = [Double]()
var strings: Array<String> = [String]()
var characters: Array<Characters> = []

// let 으로 선언하면 Array 변경이 불가능
````

### Dictionary
````swift
import swift
// Key = String, Value = Any
var anyDictionary: Dictionary<String, Any> = [String: Any]()
anyDictionary["key"] = "value"
anyDictionary["key example"] = "value example"

// dictionary key의 값 제거
anyDictionary.removeValue(forKey: "key")
anyDictionary["key example"] = nil

// 빈 dictionary 선언
let emptyDict : [String:String] = [:]
let startDict : [String:String] = ["first":"1", "second":"2"]
````

### Set
````swift

// 빈 int set생성
var integerSet: Set<Int> = Set<Int>()

integerSet.insert(1)
integerSet.insert(11)
integerSet.insert(12)
integerSet.insert(100)
integerSet.insert(99)
integerSet.insert(99)
integerSet.insert(1)

inintegerSet
// set에 요소가 있는지
integerSet.contains(1)
integerSet.contains(10)

// set에서 요소 삭제
integerSet.remove(1)
integerSet.removeFirst()

// set의 요소 개수
integerSet.count

// set의 활용
let setA: Set<Int> = [1,2,3,4,5]
let setB: Set<Int> = [4,5,6,7,8]
// 합집합
let union: Set<Int> = setA.union(setB)
// 정렬
let sortedUnion: [Int] = union.sorted()
// 교집합
let intersection: Set<Int> = setA.intersection(setB)
// 차집합
let subtracting: Set<Int> = setA.subtracting(setB)

````

