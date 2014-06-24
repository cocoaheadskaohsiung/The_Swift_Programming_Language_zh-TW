# Swift 簡易教學

學習一個新程式語言大家做常寫的第一個程式應該就是在螢幕上印出 `Hello, World`。
在 Swift 中只需要一行程式碼：
```c
println("Hello, world")
```
如果您用過 C 或 Objective-C 進行程式開發，您應該會覺得上述的 Swift 語法相當熟悉，上述的範例中這一行程式碼已經是一個完整可獨立執行的程式。
您不需要 import `譯注1` 其他的函式庫或是額外的輸入/輸出字串處理 `譯注2`。您不需要使用 main function, 程式碼撰寫點會自動被當成程式入口點。同時您也不需要為每句程式結尾加上分號。

    譯注1: Objective-C 使用 #import "xxxxx.h" 來宣告使用其他函式庫的物件或函式 C 則使用 #include "xxxxx.h"

    譯注2: 可以參見章節[字串與字元]()

本章會透過一系列範例來讓你對 Swift 撰寫有初步了解，如果你有什麼不理解的地方也不用擔心——任何本章介绍的内容都會在往後章節中詳細講解。

>
NOTE
>
>為了更佳的體驗，請在 Xcode 中打開 Playgrounds。Playgrounds 可以讓您编辑程式碼的同時看到運行的結果。[Open Playground](https://developer.apple.com/library/prerelease/ios/documentation/swift/conceptual/swift_programming_language/GuidedTour.playground.zip)


## 簡易數值

使用 `let` 宣告常數，`var` 則為宣告變數。常數在編譯時期並不需要有明確的值，但您只能為它賦值一次。也就是說您可以使用常數來宣告一個數值，並且在許多地方來使用它。

~~~
var myVariable = 42
myVariable = 50
let myConstant = 42
~~~

在賦值給常數與變數時，您必須給予其相同的型別。然而，您並不用每次都有明確寫入型別，當您在宣告常數或變數時賦值，編譯器會自動判斷其型別。在上面的範例中，編譯器判斷 `myVariable` 是一個整數(integer), 因為它的初使值是整數。

如果初始值無法提供足夠的訊息(或沒有初使值)，那您必須在變數後加上冒號宣告其型別。

~~~
let implicitInteger = 70
let implicitDouble = 70.0
let explicitDouble: Double = 70
~~~

~~~
練習
宣告一個常數其型別為 Float 並給予初始值為 4。
~~~

數值永遠不會隱含轉換成另一種型別。如果您需要轉型，請給予明確的型別。

~~~
let label = "The width is"
let width = 94
let widthLabel = label + String(width)
~~~

~~~
練習
删除最後一行中的 String，請問顯示的錯誤是什麼？
~~~

有一更簡易的方式可把數值轉換成字串：把數值寫到小括號中，並在小括號前加上反斜線。例如：

~~~
let apples = 3
let oranges = 5
let appleSummary = "I have \(apples) apples."
let fruitSummary = "I have \(apples + oranges) pieces of fruit."
~~~

~~~
練習
使用 \() 來把一個浮點數轉換成字串，並且寫上包含某人名字的問候語
~~~

使用中括號 `[]` 来建立陣列 (array) 與字典 (Dictionary)，並且在中括號裡使用 index 與 key 來存取其數值。

~~~
var shoppingList = ["catfish", "water", "tulips", "blue paint"]
shoppingList[1] = "bottle of water"

var occupations = [
    "Malcolm": "Captain",
    "Kaylee": "Mechanic",
]
occupations["Jayne"] = "Public Relations"
~~~

請使用初使化語法來創建陣列與 Dictionary

~~~
let emptyArray = String[]()
let emptyDictionary = Dictionary<String, Float>()
~~~

如果型別可被判斷出來，您可使用 `[]` 和 `[:]` 來建立空陣列與空 Dictionary --就像您宣告變數或為函式傳參數的時候一樣

~~~
shoppingList = []   // Went shopping and bought everything.
~~~

## 流程控制

使用 `if` 和 `switch` 語句來進行條件操作，`for-in`，`for`，`while`，`do-while` 語句則是用來操作迴圈。描述條件和迴圈的括號可以省略，但是整體語句的大括號則不可省略。

~~~
let individualScores = [75, 43, 103, 87, 12]
var teamScore = 0
for score in individualScores {
    if score > 50 {
        teamScore += 3
    } else {
        teamScore += 1
    }
}
teamScore
~~~

在 if 語句中，條件必須為布林表示(Bool)--這意味著像是 `if score { ... }` 的語句會造成錯誤，`score` 並不會隱含地與 0 來做比較。

您可以一起使用 `if` 與 `let` 來處理空值的情況。此種變數為 Optional。一個 Optional 值可能代表了一個具體的數值或遺失值的 nil。我們需在型別之後加上 `?` 來標示此為 Optional 值。

~~~
var optionalString: String? = "Hello"
optionalString == nil
 
var optionalName: String? = "John Appleseed"
var greeting = "Hello!"
if let name = optionalName {
    greeting = "Hello, \(name)"
}
~~~

~~~
練習
把 optionalName 賦予空值，則 greeting 會變成如何？當 optionalName 為 nil 時加上 else 語句，並幫 greeting 賦予不同的值。
~~~

如果 Optional 值為空值，條件會判斷為 false，大括號中的程式碼會被跳過。如果不是空值，則會賦值給 `let` 之後的常數，此時大括號中的程式片段就可使用此變數。

'switch' 可支援任何型式的資料以及各種比較式的操作--不限只有整數或測試兩數是否相等。

~~~
let vegetable = "red pepper"
switch vegetable {
case "celery":
    let vegetableComment = "Add some raisins and make ants on a log."
case "cucumber", "watercress":
    let vegetableComment = "That would make a good tea sandwich."
case let x where x.hasSuffix("pepper"):
    let vegetableComment = "Is it a spicy \(x)?"
default:
    let vegetableComment = "Everything tastes good in soup."
}
~~~

~~~
練習
嘗試移除 default case，會顯示什麼樣的錯誤？
~~~

程式執行到有符合 `switch case` 的條件後，程式會離開 'switch' 語句，並不會繼續往下執行，所以不需要在每個 `case` 結尾後加上 `break`。  

你可以使用 `for-in` 來訪問 Dictionary 裡的每個項目，這需要兩個變數來代表 `key-value`。

~~~
let interestingNumbers = [
    "Prime": [2, 3, 5, 7, 11, 13],
    "Fibonacci": [1, 1, 2, 3, 5, 8],
    "Square": [1, 4, 9, 16, 25],
]
var largest = 0
for (kind, numbers) in interestingNumbers {
    for number in numbers {
        if number > largest {
            largest = number
        }
    }
}
largest
~~~

~~~
練習
加上另外的變數來記錄哪種類型的數值是最大的。
~~~

使用 `while` 來反覆執行一段程式直到條件不滿足為止。迴圈的條件可以寫在開頭也可以放到結尾，寫在結尾的情形是為了確保迴圈至少會被執行一次。

~~~
var n = 2
while n < 100 {
    n = n * 2
}
n
 
var m = 2
do {
    m = m * 2
} while m < 100
m
~~~

你可以在迴圈使用 `..` 來表示範圍，也可以使用傳統寫法。以下範例的兩種迴圈是一樣的： 

~~~
var firstForLoop = 0
for i in 0..3 {
    firstForLoop += i
}
firstForLoop
 
var secondForLoop = 0
for var i = 0; i < 3; ++i {
    secondForLoop += 1
}
secondForLoop
~~~

以上例來說使用 `..` 迴圈總共執行的 `i` 分別為 i = 0, i = 1, i = 2, 如果您想使用的傳統寫法為 i <= 3, 那請您使用 `...` 

## 函式 Functions 與 Closures

使用 `func` 來宣告函式。使用名稱和參數來呼叫函式。使用 `->` 於參數型別與名稱之後來指定函式回傳值。

~~~
func greet(name: String, day: String) -> String {
    return "Hello \(name), today is \(day)."
}
greet("Bob", "Tuesday")
~~~

~~~
練習
移除 `day` 參數，增加一個參數來表示今天的午飯。
~~~

swift 函式也能支援同時有多個回傳值

~~~
func getGasPrices() -> (Double, Double, Double) {
    return (3.59, 3.69, 3.79)
}
getGasPrices()
~~~

函式也可使用陣列方式夾帶多參數。

~~~
func sumOf(numbers: Int...) -> Int {
    var sum = 0
    for number in numbers {
        sum += number
    }
    return sum
}
sumOf()
sumOf(42, 597, 12)
~~~

~~~
練習
請寫一個函式來計算其所有參數的平均數。
~~~

swift 也支援巢狀寫法(nested function)。巢狀函式可以存取外部函式的變數。你可以使用巢狀函式來重構一個過長或複雜的函式。

~~~
func returnFifteen() -> Int {
    var y = 10
    func add() {
        y += 5
    }
    add()
    return y
}
returnFifteen()
~~~

函式屬於第一級的類別，意味著函式也可以被當作另一個函式的回傳值。

~~~
func makeIncrementer() -> (Int -> Int) {
    func addOne(number: Int) -> Int {
        return 1 + number
    }
    return addOne
}
var increment = makeIncrementer()
increment(7)
~~~

函式也可以當作參數傳給另一個函式

~~~
func hasAnyMatches(list: Int[], condition: Int -> Bool) -> Bool {
    for item in list {
        if condition(item) {
            return true
        }
    }
    return false
}
func lessThanTen(number: Int) -> Bool {
    return number < 10
}
var numbers = [20, 19, 7, 12]
hasAnyMatches(numbers, lessThanTen)
~~~

函式其實是一種特殊的 closures。你可以使用大括號 `{}` 來創建出一個沒有名稱的 closure 。使用 `in` 於函式主體與回傳值之間。

~~~
numbers.map({
    (number: Int) -> Int in
    let result = 3 * number
    return result
    })
~~~

~~~
練習
請重寫一個 closure, 對所有的奇數回傳 0。
~~~

有很多種更簡易的方式可用來建立 closures。當一個 closure 的型別為已知時，好比像委派的 callback，你可以忽略其參數型別或回傳值型別。單一語句的 closures 會將其值直接回傳。

~~~
numbers.map({ number in 3 * number })
~~~

你可以透過參數位置而非參數名稱來引用參數--這個方法使用於簡短的 clousers 會很實用。當一個 closure 作為最後一個參數傳給函式時，可以直接接在函式的括號之後。

~~~
sort([1, 5, 3, 12, 2]) { $0 > $1 }
~~~


## 物件 Object 與類別 Class

我們可以使用 `class` 接著其命名來建立一個類別。類別中屬性的宣告就和宣告變數與常數相同，唯一的區別是其中的上下文。同樣地，方法與函式的宣告也相同。

~~~
class Shape {
    var numberOfSides = 0
    func simpleDescription() -> String {
        return "A shape with \(numberOfSides) sides."
    }
}
~~~

~~~
練習
使用 `let` 來增加一個常數屬性，並再加上可接受其他參數的方法。
~~~

要創建一個類別的實體只需在類別名稱後面加上括號，並且使用 `.` 來存取實體的屬性與方法。

~~~
var shape = Shape()
shape.numberOfSides = 7
var shapeDescription = shape.simpleDescription()
~~~

此版本的 `Shape` 類別缺少了一些重要的東西：一個建構函式來初始化。這時我們可以使用 `init` 來初始化。

~~~
class NamedShape {
    var numberOfSides: Int = 0
    var name: String
    
    init(name: String) {
        self.name = name
    }
    
    func simpleDescription() -> String {
        return "A shape with \(numberOfSides) sides."
    }
}
~~~

請注意 `self` 如何被用來區分建構函式內的屬性與參數。當您建立一個實體並要傳入參數時，請使用傳參數給函式的方式一樣傳給建構函式。每個屬性不論在宣告(例如 numberOfSides )或初始化(例如 name )時都必需要賦值。 

如果您需要解除配置(deallocated)時清除一些資料，請使用 `deinit` 來建立解構函式

定義一個子類別時使用 `:` 接著其父類別名稱。定義類別時不一定需要一個標準的 root 父類別名稱，因此您可以將其省略。

子類別如果要覆寫父類方法時，需使用 `override` 作為標記，如果未加上就覆寫父類別方法，編譯器將會回傳錯誤。編譯器也會檢查 `override` 的方法是否確實有定義於在父類別中。

~~~
class Square: NamedShape {
    var sideLength: Double
    
    init(sideLength: Double, name: String) {
        self.sideLength = sideLength
        super.init(name: name)
        numberOfSides = 4
    }
    
    func area() ->  Double {
        return sideLength * sideLength
    }
    
    override func simpleDescription() -> String {
        return "A square with sides of length \(sideLength)."
    }
}
let test = Square(sideLength: 5.2, name: "my test square")
test.area()
test.simpleDescription()
~~~

~~~
練習
定義另一個名為 Circle 的子類別，其建構函式包含 radius 與 name 兩參數，並實作 area 與 describe 方法。
~~~

另外屬性有簡單的存取方式，稱為 `getter` 與 `setter`

~~~
class EquilateralTriangle: NamedShape {
    var sideLength: Double = 0.0
    
    init(sideLength: Double, name: String) {
        self.sideLength = sideLength
        super.init(name: name)
        numberOfSides = 3
    }
    
    var perimeter: Double {
    get {
        return 3.0 * sideLength
    }
    set {
        sideLength = newValue / 3.0        
    }
    }
    
    override func simpleDescription() -> String {
        return "An equilateral triagle with sides of length \(sideLength)."
    }
}
var triangle = EquilateralTriangle(sideLength: 3.1, name: "a triangle")
triangle.perimeter
triangle.perimeter = 9.9
triangle.sideLength
~~~

在 `setter` 中，新值的名稱自動被稱為 `newValue`，您可以在之後給予明確的名稱。

請注意 EquilateralTriangle 類別的建構函式有三個步驟：

  1. 在子類別的定義中設了屬性值
  2. 使用了父類別的建構函式
  3. 改變了父類別定義的屬性值。其他如調用方法、 getter 、 setter 也都在此階段完成

如果您不需要計算屬性，但仍需要在執行程前碼前與設置新值之後，請使用 `willSet` 與 `didSet`。例如下例中的 square 的 sideLength 會與 triangle 的 sideLength 會保持一致。

~~~
class TriangleAndSquare {
    var triangle: EquilateralTriangle {
    willSet {
        square.sideLength = newValue.sideLength
    }
    }
    var square: Square {
    willSet {
        triangle.sideLength = newValue.sideLength
    }
    }
    init(size: Double, name: String) {
        square = Square(sideLength: size, name: name)
        triangle = EquilateralTriangle(sideLength: size, name: name)
    }
}
var triangleAndSquare = TriangleAndSquare(size: 10, name: "another test shape")
triangleAndSquare.square.sideLength
triangleAndSquare.triangle.sideLength
triangleAndSquare.square = Square(sideLength: 50, name: "larger square")
triangleAndSquare.triangle.sideLength
~~~

類別中的方法與函式有一個重要的分別。函式的參數名稱只在函式的內部使用，但方法的參數名稱會使用於調用方法時(第一個參數除外)。在預設情況中，方法的參數名稱和它在方法內部的名稱一樣，不過在使用於方法內部時，您也可以為其定義第二個名稱。

~~~
class Counter {
    var count: Int = 0
    func incrementBy(amount: Int, numberOfTimes times: Int) {
        count += amount * times
    }
}
var counter = Counter()
counter.incrementBy(2, numberOfTimes: 7)
~~~

當處理 optional 值時，您可以用 `?` 在方法、屬性與子腳本前。如果 `?` 之前是 `nil`，在 `?` 之後的東西都會被忽略，而且整段式子都會回傳 `nil`。否則，所有的 optional 值都會被解開，在 `?` 之後的都會被執行。在這兩種情況下，整個表達式都會是個 optional 值。

~~~
let optionalSquare: Square? = Square(sideLength: 2.5, name: "optional square")
let sideLength = optionalSquare?.sideLength
~~~

## 列舉 Enumerations 與 結構 Structures

使用 `enum` 來建立列舉(enumeration)。就如同類別與其他命名型別一樣，列舉也能包含方法。

~~~
enum Rank: Int {
    case Ace = 1
    case Two, Three, Four, Five, Six, Seven, Eight, Nine, Ten
    case Jack, Queen, King
    func simpleDescription() -> String {
        switch self {
        case .Ace:
            return "ace"
        case .Jack:
            return "jack"
        case .Queen:
            return "queen"
        case .King:
            return "king"
        default:
            return String(self.toRaw())
        }
    }
}
let ace = Rank.Ace
let aceRawValue = ace.toRaw()
~~~

~~~
練習
請嘗試寫一個函式，依照它們的原始值來比較兩者的排列值
~~~

在上述的範列中，列舉中的原始值型別為 `Int`, 所以您只需要定義給第一個原始值。剩下的原始值就會按照順序賦值。你也可以使用字串或浮點數來作為列舉的原始值。

始用 `toRaw` 和 `fromRaw` 函式在原始值與列舉值間進行轉換。

~~~
if let convertedRank = Rank.fromRaw(3) {
    let threeDescription = convertedRank.simpleDescription()
}
~~~

列舉的成員值是實際值，並不是原始值的另一種表示。事實上，如果原始值是無義意的，您就不需要另外提供。

~~~
enum Suit {
    case Spades, Hearts, Diamonds, Clubs
    func simpleDescription() -> String {
        switch self {
        case .Spades:
            return "spades"
        case .Hearts:
            return "hearts"
        case .Diamonds:
            return "diamonds"
        case .Clubs:
            return "clubs"
        }
    }
}
let hearts = Suit.Hearts
let heartsDescription = hearts.simpleDescription()
~~~

~~~
練習
為 Suit 加一個 color 方法，對 spades 與 clubs 回傳 "black", 對 hearts 與 diamonds 回傳 "red"。 
~~~

上述中，請注意有兩種可引用列舉中的 Hearts 成員：為 hearts 賦值成常數時，列舉成員 `Suit.Hearts` 需要全名來引用，因為常數沒有明確的型別。在 switch 中，列舉成員可使用 .Hearts 引用，因為它已經知道是一個 suit。在任何情形下，對於已知的型別您可以使用縮寫。

使用 `struct` 來建立結構(structure)。Structure 支援許多與類別相同的行為，包含方法與初使化。兩者有一個最大的不同點在於 structure 是傳值，類別是傳的是參考。

~~~
struct Card {
    var rank: Rank
    var suit: Suit
    func simpleDescription() -> String {
        return "The \(rank.simpleDescription()) of \
        (suit.simpleDescription())"
    }
}
let threeOfSpades = Card(rank: .Three, suit: .Spades)
let threeOfSpadesDescription = threeOfSpades.simpleDescription()
~~~

~~~
練習
為 Card 寫一個方法能建立一整副撲克牌，而且每張牌的 rank 與 suit 能對應起來。
~~~

一個列舉成員的實體可以有實體值。相同的列舉成員的實體可以有不一樣的值。當您建立時即可傳入值。實體值與原始值是不同的：列舉成員的原始值對所有的實體都是相同地，當您定義列舉時所提供的原始值。

例如，考慮到從伺服器取得日出與日落時間，伺服器會回應正常或錯誤訊息。

~~~
enum ServerResponse {
    case Result(String, String)
    case Error(String)
}
 
let success = ServerResponse.Result("6:00 am", "8:09 pm")
let failure = ServerResponse.Error("Out of cheese.")
 
switch success {
case let .Result(sunrise, sunset):
    let serverResponse = "Sunrise is at \(sunrise) and sunset is at \(sunset)."
case let .Error(error):
    let serverResponse = "Failure...  \(error)"
}
~~~

~~~
練習
為 ServerResponse 加上第三種 case 給 switch 。
~~~

注意日出與日落時間是如何從伺服器取得成給 switch case 配對的值


## 協議 Protocols 與 擴展 Extensions

使用 `protocol` 來宣告協議 (protocol)。

~~~
protocol ExampleProtocol {
    var simpleDescription: String { get }
    mutating func adjust()
}
~~~

類別、列舉與結構全都實作協議。

~~~
class SimpleClass: ExampleProtocol {
    var simpleDescription: String = "A very simple class."
    var anotherProperty: Int = 69105
    func adjust() {
        simpleDescription += "  Now 100% adjusted."
    }
}
var a = SimpleClass()
a.adjust()
let aDescription = a.simpleDescription
 
struct SimpleStructure: ExampleProtocol {
    var simpleDescription: String = "A simple structure"
    mutating func adjust() {
        simpleDescription += " (adjusted)"
    }
}
var b = SimpleStructure()
b.adjust()
let bDescription = b.simpleDescription
~~~

~~~
練習
請寫一個實作此協議的列舉。
~~~

請注意在上例中，我們使用 `mutating` 於來標示一個會修改結構的方法。在 SimpleClass 中我們卻不使用 `mutating` ，因為方法本來就會經常修改類別本身。

使用 `extension` 來為已存在的類型擴展功能，例如像新的方法和屬性。您可使用 `extension` 來改寫在其他地方已宣告之型別，甚至是從 library 或 framework 所引用的。

~~~
extension Int: ExampleProtocol {
    var simpleDescription: String {
    return "The number \(self)"
    }
    mutating func adjust() {
        self += 42
    }
}
7.simpleDescription
~~~

~~~
練習
幫 Double 型別寫一個 extension，使其擁有絕對值 (absoluteValue) 的屬性。
~~~

您可以使用 protocol 名稱如同其他型別的命名--例如，創造一個物件集合使其擁有不同的型別，但所有的物件都需遵循一份相同的 protocol。當您處理一個型別屬於 protocol 的值時，protocol 外的方法皆不可使用。

~~~
let protocolValue: ExampleProtocol = a
protocolValue.simpleDescription
// protocolValue.anotherProperty  // Uncomment to see the error
~~~

即使 protocolValue 於 runtime 的型別是 SimpleClass, 編譯器仍會把它當成 ExampleProtocol。這意味著你不能使用類別實作 protocol 之外的方法與屬性。

## 泛型 Generics

泛型寫法為在 `<>` 中加入函式或型別。

~~~
func repeat<ItemType>(item: ItemType, times: Int) -> ItemType[] {
    var result = ItemType[]()
    for i in 0..times {
        result += item
    }
    return result
}
repeat("knock", 4)
~~~

您也可以為類別、列舉與結構加上泛型

~~~
// Reimplement the Swift standard library's optional type
enum OptionalValue<T> {
    case None
    case Some(T)
}
var possibleInteger: OptionalValue<Int> = .None
possibleInteger = .Some(100)
~~~

使用 `where` 於型別之後來限縮泛型--例如限定實作某個協議，限定兩種相同型名，限定類別繼承之某一父類別。

~~~
func anyCommonElements <T, U where T: Sequence, U: Sequence, T.GeneratorType.Element: Equatable, T.GeneratorType.Element == U.GeneratorType.Element> (lhs: T, rhs: U) -> Bool {
    for lhsItem in lhs {
        for rhsItem in rhs {
            if lhsItem == rhsItem {
                return true
            }
        }
    }
    return false
}
anyCommonElements([1, 2, 3], [3])
~~~

~~~
練習
改寫 anyCommonelements 函式使其回傳之陣列包含兩序列的共同元素。
~~~

為了簡單起見，您可以忽略 `where` ，只需在冒號後面寫上協議或類別名稱。`<T: Equatable>` 與 `<T where T: Equatable>` 這兩種寫法是相同的。