#1.Swift의 기초

##1. 스위프트의 명명법/콘솔로그/문자열 보간법

### 이름짓기 규칙
* 카멜케이스를 활용
* 대소문자를 구분

### 콘솔로그

* print
  * 단순 문자열 출력
* dump
  * 인스턴스의 자세한 설명 출력

### 문자열 보간 법

* 프로그램 실행중 문자열내의 변수또는 상수의 실질값을 표현하기위함
* \(여기)()
```swift
ex)
let age: Int =10;
print("안녕하세요 저는 \(age+5)살 입니다!")

```
## 2. 상수와 변수

```swift
//상수 선언의 취급 let
//변수 선언의 취급은 var로 명명한다.

//상수의 선언
let age: Int=10
//변수의 선언
var age: Int=10

//하지만 상수와 변수에서 타입이 명확한 자료의 값이라면 자료형 명시를 생략 가능하다.

let age = 10;
var name = "홍길동"

let constant: String = "상수는 변경이 불가능하지만"
var constant: String = "변수는 변경이 가능합니다"
constant = "이렇게요"
/////////////////////////////////////////////////

//상수는 값의 초기화없이 선언 되었을때는 최초한번은 값의 변경이 
//가능하다 이때는 상수명과 타입을 명시해주어야한다.

let age: Int;
let a : Int = 10;
let b : Int = 20;
age = a+b
// 이이후에 age의 값 변경이 불가능해진다.

//변수도 마찬가지로 최초선언시에 값의 초기화 없이 사용가능하다.

var name: String
//하지만 값의 초기화없이 사용하려 한다면 문제를 발생시킨다.
//print(name) 

name = "ddddd"
//이제는 가능해진다.
print(name)
```

### 3.기본 데이터 자료

### Bool
```swift
var data  = true // 가능
data  = 0 // 불가능
data  = 1 // 불가능
```

### Character
```swift
//유니코드를 사용하기 때문에 유니코드 그림도 가능하다. 하지만 여러개의
//문자를 사용하려 들면 String 취급을 받기 때문에 사용이 불가능하다.
//Character를 사용하려면 "(자료)" 형태로 취급해야한다.
var data: Character  = "a" // 가능
data  = "aaaa" // 불가능
```

## 4. Any,AnyObject,nil 

```swift
//Any = 어떤 자료형이든 수용할수가 있는 타입
//Any = 어떤 클래스 라도 수용할수가 있는 타입
//nil = 아무것도 없음을 뜻함(null)
```
### Any
```swift
var data : Any = "어떤것도 수용가능합니다"
data = 123.12

//하지만 반대의 경우는 불가능하다.

var db : Double = 123.12
//db = data 불가능


```
### AnyObject
```swift

class SomeClass{}

var someClass: AnyObject = SomeClass()

// someClass = 1234.4321 // AnyObject타입에 클래스가 아닌 다른 타입을 넣는것은 불가능.

```

### nil

```swift
// someAny는 Any 타입이고, someAnyObject는 AnyObject 타입이기 때문에 nil을 할당할 수 없습니다.
var someAny: Any = 100
var someAnyObject: AnyObject = SomeClass()

// nil을 다루는 방법은 옵셔널 파트에서 다룹니다.
someAny = nil         // 컴파일 오류발생
someAnyObject = nil   // 컴파일 오류발생
```

##  5. 컬렉션 타입(Array, Dictionary, Set) 

### 1.Array

```swift
// 1. Array 선언 및 생성
var integers: Array<Int> = Array<Int>()

// 위와 동일한 표현
// var integers: Array<Int> = [Int]()
// var integers: Array<Int> = []
// var integers: [Int] = Array<Int>()
// var integers: [Int] = [Int]()
// var integers: [Int] = []
// var integers = [Int]()


// 2. Array 활용
integers.append(1)
integers.append(100)

// Int 타입이 아니므로 Array에 추가할 수 없습니다
//integers.append(101.1)

print(integers)	// [1, 100]

// 멤버 포함 여부 확인
print(integers.contains(100)) // true
print(integers.contains(99)) // false

// 멤버 교체
integers[0] = 99

// 멤버 삭제
integers.remove(at: 0) // 99삭제
integers.removeLast() // 100 삭제
integers.removeAll() // 모든것이 삭제지만 아무것도 삭제안됨

// 멤버 수 확인
print(integers.count)

// 인덱스를 벗어나 접근하려면 익셉션 런타임 오류발생
//integers[0]


// 3. 불변 Array: let을 사용하여 Array 선언
let immutableArray = [1, 2, 3]

// 수정이 불가능한 Array이므로 멤버를 추가하거나 삭제할 수 없습니다
//immutableArray.append(4)
//immutableArray.removeAll()
```

### 2.Dictionary

```swift
// 1. Dictionary의 선언과 생성
// Key가 String 타입이고 Value가 Any인 빈 Dictionary 생성
var anyDictionary: Dictionary<String, Any> = [String: Any]()

// 위와 동일한 표현
// var anyDictionary: Dictionary <String, Any> = Dictionary<String, Any>()
// var anyDictionary: Dictionary <String, Any> = [:]
// var anyDictionary: [String: Any] = Dictionary<String, Any>()
// var anyDictionary: [String: Any] = [String: Any]()
// var anyDictionary: [String: Any] = [:]
// var anyDictionary = [String: Any]()


// 2. Dictionary 활용
// 키에 해당하는 값 할당
anyDictionary["someKey"] = "value"
anyDictionary["anotherKey"] = 100

print(anyDictionary) // ["someKey": "value", "anotherKey": 100]

// 키에 해당하는 값 변경
anyDictionary["someKey"] = "dictionary"
print(anyDictionary) ["someKey": "dictionary", "anotherKey": 100]

// 키에 해당하는 값 제거
anyDictionary.removeValue(forKey: "anotherKey")
anyDictionary["someKey"] = nil
print(anyDictionary)


// 3. 불변 Dictionary: let을 사용하여 Dictionary 선언
let emptyDictionary: [String: String] = [:]
let initalizedDictionary: [String: String] = ["name": "yagom", "gender": "male"]

// 불변 Dictionary이므로 값 변경 불가
//emptyDictionary["key"] = "value"

// 키에 해당하는 값을 다른 변수나 상수에 할당하고자 할 때는 옵셔널과 타입 캐스팅 파트에서 다룹니다
// "name"이라는 키에 해당하는 값이 없을 수 있으므로 String 타입의 값이 나올 것이라는 보장이 없습니다.
// 컴파일 오류가 발생합니다
// let someValue: String = initalizedDictionary["name"]
```

### 3.Set 

```swift
// 1. Set 생성 및 선언
var integerSet: Set<Int> = Set<Int>()

// insert : 새로운 멤버 입력
// 동일한 값은 여러번 insert해도 한번만 저장됩니다.
integerSet.insert(1)
integerSet.insert(99)
integerSet.insert(99)
integerSet.insert(99)
integerSet.insert(100)

print(intigerSet) // {100, 99, 1}

// contains: 멤버 포함 여부 확인
print(integerSet.contatins(1)) // true
print(integerSet.contains(2)) // false

// remove: 멤버 삭제
integerSet.remove(99) // {100, 1}
integerSet.removeFirst() // {1}

// count: 멤버 개수
integerSet.count // 1


// 2. Set의 활용
// 멤버의 유일성이 보장되기 때문에 집합 연산에 활용하면 유용합니다.
let setA: Set<Int> = [1, 2, 3, 4, 5]
let setB: Set<Int> = [3, 4, 5, 6, 7]

// 합집합
let union: Set<Int> = setA.union(setB)
print(union) // [2, 4, 5, 6, 7, 3, 1]

// 합집합 오름차순 정렬
let sortedUnion: [Int] = union.sorted()
print(sortedUnion) // [1, 2, 3, 4, 5, 6, 7]

// 교집합
let intersection: Set<Int> = setA.intersection(setB)
print(intersection) // [5, 3, 4]

// 차집합
let subtracting: Set<Int> = setA.subtracting(setB)
print(subtracting) // [2, 1]
```

## 7. 함수 기본

### 1. 함수 선언의 기본형태

```swift
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 ...) -> 반환타입 {
    /* 함수 구현부 */
    return 반환값
}

// 예)
// sum이라는 이름을 가지고 
// a와 b라는 Int 타입의 매개변수를 가지며 
// Int 타입의 값을 반환하는 함수
func sum(a: Int, b: Int) -> Int {
    return a + b
}
```


### 2. 반환 값이 없는 함수

```swift
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 ...) -> Void {
    /* 함수 구현부 */
    return
}

// 예)
func printMyName(name: String) -> Void {
    print(name)
}

// 반환 값이 없는 경우, 반환 타입(Void)을 생략해 줄 수 있습니다
func printYourName(name: String) {
    print(name)
}
```
### 3. 매개변수가 없는 함수

```swift
func 함수이름() -> 반환타입 {
    /* 함수 구현부 */
    return 반환값
}

// 예)
func maximumIntegerValue() -> Int {
    return Int.max
}
```

### 4. 매개변수와 반환값이 없는 함수



```swift
func 함수이름() -> Void {
    /* 함수 구현부 */
    return
}

// 함수 구현이 짧은 경우
// 가독성을 해치지 않는 범위에서
// 줄바꿈을 하지 않고 한 줄에 표현해도 무관합니다
func hello() -> Void { print("hello") }


// 반환 값이 없는 경우, 반환 타입(Void)을 생략해 줄 수 있습니다
func 함수이름() {
    /* 함수 구현부 */
    return
}

func bye() { print("bye") }
```

### 5. 함수의 호출



```swift
sum(a: 3, b: 5) // 8

printMyName(name: "yagom") // yagom

printYourName(name: "hana") // hana

maximumIntegerValue() // Int의 최댓값

hello() // hello

bye() // bye
```

## 8. 함수 고급

### 1. 매개변수 기본 값

```swift
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 = 매개변수 기본값 ...) -> 반환타입 {
    /* 함수 구현부 */
    return 반환값
}

func greeting(friend: String, me: String = "yagom") {
    print("Hello \(friend)! I'm \(me)")
}

// 매개변수 기본값을 가지는 매개변수는 호출시 생략할 수 있습니다
greeting(friend: "hana") // Hello hana! I'm yagom
greeting(friend: "john", me: "eric") // Hello john! I'm eric
```
### 2. 전달인자 레이블(Argument Label)

```swift
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 ...) -> Void {
    /* 함수 구현부 */
    return
}

// 예)
func printMyName(name: String) -> Void {
    print(name)
}

// 반환 값이 없는 경우, 반환 타입(Void)을 생략해 줄 수 있습니다
func printYourName(name: String) {
    print(name)
}
```
### 3. 가변 매개변수

```swift
//func 함수이름(매개변수1이름: 매개변수1타입, 전달인자 레이블 매개변수2이름: 매개변수2타입...) -> 반환타입 {
//    /* 함수 구현부 */
//    return
//}

func sayHelloToFriends(me: String, friends: String...) -> String {
    return "Hello \(friends)! I'm \(me)!"
}
print(sayHelloToFriends(me: "yagom", friends: "hana", "eric", "wing"))
// Hello ["hana", "eric", "wing"]! I'm yagom!

print(sayHelloToFriends(me: "yagom"))
// Hello []! I'm yagom!
```

### 4. 데이터 타입으로서의 함수
```swift
var someFunction: (String, String) -> Void = greeting(to:from:)
someFunction("eric", "yagom") // Hello eric! I'm yagom

someFunction = greeting(friend:me:)
someFunction("eric", "yagom") // Hello eric! I'm yagom


// 타입이 다른 함수는 할당할 수 없습니다 - 컴파일 오류 발생
//someFunction = sayHelloToFriends(me: friends:)


func runAnother(function: (String, String) -> Void) {
    function("jenny", "mike")
}

// Hello jenny! I'm mike
runAnother(function: greeting(friend:me:))

// Hello jenny! I'm mike
runAnother(function: someFunction)
```

## 8. 조건문

### 1. if-else 구문

```swift


//if-else의 사용
let someInteger = 100

if someInteger < 100 {
    print("100 미만")
} else if someInteger > 100 {
    print("100 초과")
} else {
    print("100")
} // 100

// 스위프트의 조건에는 항상 Bool 타입이 들어와야 합니다.
// someInteger는 Bool 타입이 아닌 Int 타입이기 때문에
// 컴파일 오류가 발생합니다.
//if someInteger { }
```

### 2. switch 구문
```swift
switch 구문의 기본 형태
switch 비교값 {
case 패턴:
    /* 실행 구문 */
default:
    /* 실행 구문 */
}
switch 구문의 사용
// 범위 연산자를 활용하면 더욱 쉽고 유용합니다
switch someInteger {
case 0:
    print("zero")
case 1..<100:
    print("1~99")
case 100:
    print("100")
case 101...Int.max:
    print("over 100")
default:
    print("unknown")
} // 100

// 정수 외의 대부분의 기본 타입을 사용할 수 있습니다
switch "yagom" {
case "jake":
    print("jake")
case "mina":
    print("mina")
case "yagom":
    print("yagom!!")
default:
    print("unknown")
} // yagom!!
``` 

## 9 반복문

### 1. for-in 구문
```swift
for-in 구문 기본 형태
for item in items {
    /* 실행 구문 */
}
for-in 구문의 사용
var integers = [1, 2, 3]
let people = ["yagom": 10, "eric": 15, "mike": 12]

for integer in integers {
    print(integer)
}

// Dictionary의 item은 key와 value로 구성된 튜플 타입입니다
for (name, age) in people {
    print("\(name): \(age)")
}
```
### 2. while 구문
```swift
while 구문의 기본 형태
while 조건 {
    /* 실행 구문 */
}
while 구문의 사용
while integers.count > 1 {
    integers.removeLast()
}
```


### 3. repeat-while 구문
```swift
기존 언어의 do-while 구문과 형태/동작이 유사합니다.
repeat-while 구문의 기본 형태
repeat {
    /* 실행 구문 */
} while 조건
repeat-while 구문의 사용
repeat {
    integers.removeLast()
} while integers.count > 0
```

## 10 옵셔널

### 1. 옵셔널이란??
```swift
// someOptionalParm에 nil이 할당 될 수 있다.
func someFunction(someOptionalParam: Int?) {
       // ....
}

/// someOptionalParm에 nil이 할당 될 수 없다.
func someFunction(someOptionalParam: Int) {
       // ....
}

someFunction(someOptionalParam: nil)
// someFunction(someParam: nil) 
```
### 2. 옵셔널을 쓰는 이유????

* 명시적 표현
          1. nil의 가능성을 코드만으로 표현가능
          2. 문서/주석 작성 시간 절약

* 안전한 사용
          1. 전달받은 값이 옵셔널이 아니라면 nil 체크를 하지 않고 사용가능
          2. 예외 상황을 최소화 하는 안전한 코딩
          3. 효율적 코딩

### 3. 옵셔널 문법과 선언

* 옵셔널 문법과 선언
```swift
옵셔널 문법 = enum + generics (수업 후반에 다시 배울거에요)
옵셔널 선언
enum Optional<Wrapped>: ExpressibleByNiliteral {
         case none
         case some(Wrapped)
}

let optionalValue: Optional<Int> = nil
let optionalValue: Int? =nil
```

* 옵셔널 표현
  * 1. 느낌표(!)를 이용한 암시적 추출 옵셔널 
```swift
// Implicitly Unwrapped Optional
var implicitlyUnwrappedOptionalValue: Int! = 100

switch implicitlyUnwrappedOptionalValue {
case .none:
    print("This Optional variable is nil")
case .some(let value):
    print("Value is \(value)")
}

// 기존 변수처럼 사용 가능
implicitlyUnwrappedOptionalValue = implicitlyUnwrappedOptionalValue + 1

// nil 할당 가능
implicitlyUnwrappedOptionalValue = nil

// 잘못된 접근으로 인한 런타임 오류 발생
//implicitlyUnwrappedOptionalValue = implicitlyUnwrappedOptionalValue + 1
```
  * 2. 물음표(?)를 이용한 옵셔널
```swift
// Optional
var optionalValue: Int? = 100

switch optionalValue {
case .none:
    print("This Optional variable is nil")
case .some(let value):
    print("Value is \(value)")
}

// nil 할당 가능
optionalValue = nil

// 기존 변수처럼 사용불가 - 옵셔널과 일반 값은 다른 타입이므로 연산불가
//optionalValue = optionalValue + 1
```