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


## 變數

使用 `let` 宣告常數，`var` 則為宣告變數。在編譯時期並不需要有明確的值，但您只能為它賦值一次。也就是說您可以使用常數來宣告一個數值，並且在許多地方來使用它。

~~~
var myVariable = 42
myVariable = 50
let myConstant = 42
~~~

在賦值給常數與變數時，您必須給予相同的型別。然而，您並不用每次都有明確寫入型別，當您在宣告常數或變數時賦值，編譯器會自動判斷其型別。在上面的範例中，編譯器判斷 `myVariable` 是一個整數(integer), 因為它的初使值是整數。

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

數值永遠不會隱含轉換成另一種型別。如果您需要轉型，請用強制轉型。

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

使用中括號 [] 来來創建陣列與 Dictionary，並且在中括號裡使用 index 與 key 來存取其數值。

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

使用 if 和 switch 語句來進行條件操作，for-in，for，while，do-while 語句則是用來操作迴圈。描述條件和迴圈的括號可以省略，但是整體語句的大括號則不可省略。

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

在 if 語句中，條件必須為布林表1式(Bool)--這意味著像是 `if score { ... }` 的語句會造成錯誤，`score` 並不會隱含地與 0 來做比較。

您可以一起使用 `if` 與 `let` 來處理空值的情況。此種變數為 Optional。一個 Optional 值可能代表了一個具體的數值或遺失值的 nil。我們須在型別之後加上 `?` 來標示此為 Optional 值。

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
把 optionalName 賦予空值，則問候語會變成如何？當 optionalName 為 nil 時加上 else 語句，並幫問候語賦予不同的值。
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

Use .. to make a range that omits its upper value, and use ... to make a range that includes both values.

## Functions and Closures

Use func to declare a function. Call a function by following its name with a list of arguments in parentheses. Use -> to separate the parameter names and types from the function’s return type.

func greet(name: String, day: String) -> String {
    return "Hello \(name), today is \(day)."
}
greet("Bob", "Tuesday")
EXPERIMENT

Remove the day parameter. Add a parameter to include today’s lunch special in the greeting.

Use a tuple to return multiple values from a function.

func getGasPrices() -> (Double, Double, Double) {
    return (3.59, 3.69, 3.79)
}
getGasPrices()
Functions can also take a variable number of arguments, collecting them into an array.

「func sumOf(numbers: Int...) -> Int {
    var sum = 0
    for number in numbers {
        sum += number
    }
    return sum
}
sumOf()
sumOf(42, 597, 12)
EXPERIMENT

Write a function that calculates the average of its arguments.

Functions can be nested. Nested functions have access to variables that were declared in the outer function. You can use nested functions to organize the code in a function that is long or complex.

func returnFifteen() -> Int {
    var y = 10
    func add() {
        y += 5
    }
    add()
    return y
}
returnFifteen()
Functions are a first-class type. This means that a function can return another function as its value.

func makeIncrementer() -> (Int -> Int) {
    func addOne(number: Int) -> Int {
        return 1 + number
    }
    return addOne
}
var increment = makeIncrementer()
increment(7)
A function can take another function as one of its arguments.」

「func hasAnyMatches(list: Int[], condition: Int -> Bool) -> Bool {
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
Functions are actually a special case of closures. You can write a closure without a name by surrounding code with braces ({}). Use in to separate the arguments and return type from the body.

~~~
numbers.map({
    (number: Int) -> Int in
    let result = 3 * number
    return result
    })
~~~

~~~
EXPERIMENT
Rewrite the closure to return zero for all odd numbers.
~~~

You have several options for writing closures more concisely. When a closure’s type is already known, such as the callback for a delegate, you can omit the type of its parameters, its return type, or both. Single statement closures implicitly return the value of their only statement.

>numbers.map({ number in 3 * number })

You can refer to parameters by number instead of by name—this approach is especially useful in very short closures. A closure passed as the last argument to a function can appear immediately after the parentheses.

>sort([1, 5, 3, 12, 2]) { $0 > $1 }



(待續)
