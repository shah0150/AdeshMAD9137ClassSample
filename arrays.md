```swift
var numbers: [Int] = [2, 4, 8, 10, 12, 3, 5, 9]
var fruits: [String] =  ["apple", "banana", "cherry"]

let emptyArray = [String]()
emptyArray.isEmpty

fruits[2]

numbers.count
fruits.count

fruits.append("grapes")

fruits.insert("dragon fruit", at: 1)

fruits.remove(at: 4)

let hasGrapes = fruits.contains("grapes")

fruits.sort()

numbers.sorted(by: >)

let celsius: [Double] = [0.0, 10.0, 21.33, 33]

let fahrenheit = celsius.map{ $0 * 9/5 + 32 }


let sum = numbers.reduce(1, *)

numbers.filter{ $0 < 5}


let now = 2023
let years = [1993, 2003, 2013, 2023]

let yearsSum = years.filter({ $0 >= 2003 }).map({ now - $0 }).reduce(0, +)

print("Adesh is \(yearsSum) years's old")
```