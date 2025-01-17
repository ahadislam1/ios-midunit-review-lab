## Mid Unit-1 Review


## Strings

1. **Given a String, return a String with each letter uppercased**

Input: `Hello, there`

Output: `HELLO, THERE`

answer:
```swift
func stringUppercased1(_ str: String) -> String {
    str.uppercased()
}
```
2. **Given a String, return a String alternating between uppercase and lowercase letters**


Input: `Hello, there`

Output: `HeLlO, tHeRe`

answer:
```swift
func everyOtherLetter (_ str: String) -> String {
    var alternatingString = String()
    for (x, y) in str.enumerated() {
        if x % 2 == 0 {
            alternatingString += y.uppercased()
        } else {
            alternatingString += y.lowercased()
        }
    }
    return alternatingString
}
```
3. **Given a String, return a String with all occurrences of a given letter removed**

Input: `Hello, there`

Output: `Hllo, thr`

answer:
```swift
func removeCharacterFromString (char: Character, str: String) -> String {
    return str.filter( { $0 != char })
}
```

## Arrays


1. **Given an array of type [Int], return the largest element**

Input: `[1,5,2,4,1,4]`

Output: `5`

answer:
```swift
func largestInt (_ arr: [Int]) -> Int {
    var largestNum = arr[0]
    for num in arr {
        if num > largestNum {
            largestNum = num
        }
    }
    return largestNum
}
```

2. **Given an array of type [Int], return the smallest element**

Input: `[1,5,2,4,1,4]`

Output: `1`

```swift
func SmallestInt(_ arr: [Int] ) -> Int {
    return arr.sorted()[0]
}
```

3. **Given an array of type [Int], return its sum**

Input: `[1,5,2,4,1,4]`

Output: `17`
```swift
func sumOfIntArray(_ arr: [Int] ) -> Int {
    return arr.reduce(0, +)
}
```
4. **Given an array of type [Double], return its average**

Input: `[3,4.5,7.5,2,1]`

Output: `3.6`

```swift
func averageOfDoubleArray(_ arr: [Double]) -> Double {
    var sum = Double()
    for num in arr {
        sum += num
    }
    return sum / Double(arr.count)
}
```

5. **Given an array of type [Double] and a Double, return the sum of all numbers in the array greater than a given number**

Input: `[3,4.5,7.5,2,1], 3`

Output: `12`

answer:
```swift
func sumOfAllDoublesGreaterThanNumber(_ number: Double, _ arr: [Double]) -> Double {
    var sum =  0.0
    for num in arr {
        if num > number {
            sum += num
        }
    }
    return sum
}
```

6. **Given an array of type [Double], return the product of all the elements**

Input: `[3,4.5,7.5,2,1]`

Output: `202.5`

answer:
```swift
func productOfAllDoubles(_ arr: [Double]) -> Double {
    return arr.reduce(0, *)
}
```

7. **Given an array of type [Int], return the second smallest value in the array**

Input: `[3,6,1,9,4,8]`

Output: `3`
answer:

```swift
func secondSmallestInteger(_ arr: [Int]) -> Int {
    var smallestInt = arr[0]
    var secondSmallestInt = arr[1]
    for num in arr {
        if num < smallestInt {
            smallestInt = num
        }
        if num > smallestInt && num < secondSmallestInt {
            secondSmallestInt = num
        }
    }
    return secondSmallestInt
}
```
## Optionals

1. **Given an array of type [String?] return an array of [String] removing all nil values**

Input: `[nil, "We", "come", nil, "in", "peace"]`

Output: `["We", "come", "in", "peace"]`

answer:
```swift
func stringWithNoNil(_ arr:[String?]) -> [String] {
    arr.compactMap({$0})
}
```

2. **Given an array of type [String?]? return an array of [String] removing all nil values**

Input: `nil`

Output: `[]`

answer:
```swift
func arrayStringWithNoNil(_ arr:[String?]?) -> [String] {
    var goodArr = [String]()
    if let unwrappedArr = arr {
        for string in unwrappedArr {
            if let str = string {
                goodArr.append(str)
            }
        }
    }
    return goodArr
}
```

3. **Given an array of type [Int?] return the sum of all non-nil values.  Use guard statements in your solution.**

Input: `[4, nil, 9, 5, nil]`

Output: `18`

answer:
```swift
func sumOfIntOptionals(_ arr:[Int?]) -> Int {
    var sum = 0
    for num in arr {
        guard let number = num else {
            continue
        }
        sum += number
    }
    return sum
}
```

4. **Given an array of type [Int?]? return the sum of all non-nil values.  Use guard statements in your solution.**

Input: `nil`

Output: `0`

5. **Given an array of type [Int?] and an optional Int, return the sum of all values not equal to the given number.  If the given number is nil, return the sum of all non-nil values.**

Input: `[1, 1, nil, 3, 5, nil, 1, nil, 3, 5, nil, 5, nil, 3], 1`

Output: `24`

answer:
```swift
func sumOfIntOptionalsInOptionalArray(_ arr: [Int?]?) -> Int {
    guard let goodArray = arr else {
        return 0
    }
    var sum = 0
    for num in goodArray {
        guard let number = num else {
            continue
        }
        sum += number
    }
    return sum
}
```

## Dictionaries

1. **Given an array of type [String], return a copy of the array with all duplicate values removed**

Input: `["apple", "apple", "banana", "banana", "banana", "cake", "cake"]`

Output: `["apple", "banana", "cake"]`

answer:
```swift
func uniqueArray(_ arr: [String]) -> [String] {
    return Array(Set(arr))
}
```

2. **Given a String, find the most frequently occurring letter**

Input: `Never trust a computer you can't throw out a window ~ Steve Wozniak`

Output: `t`

answer:
```swift
func freqOccuringLetter(_ str: String) -> Character {
    var letterDict = [Character: Int]()
    var letterHighestCount = 0
    var letterHighestUsed: Character = "a"
    for letter in str where letter != " " {
        letterDict[letter] = (letterDict[letter] ?? 0) + 1
    }
    for (key, value) in letterDict {
        if value > letterHighestCount {
            letterHighestCount = value
            letterHighestUsed = key
        }
    }
    return letterHighestUsed
}
```
3. **Given an array of type [Int], return a copy of the array that contains only elements that appear at least twice**

Input: `[1,1,2,3,3,3,4,5,6,6,7]`

Output: `[1,3,6]`
```swift
func integersAppearedTwice(_ arr: [Int]) -> [Int] {
    var integerDict = [Int: Int]()
    var twiceArray = [Int]()
    for num in arr {
        integerDict[num] = (integerDict[num] ?? 0) + 1
        if integerDict[num] == 2 {
            twiceArray.append(num)
        }
    }
    return twiceArray
}
```
4. **Given a String, find the second most frequently occurring letter in a string**

Input: `Never trust a computer you can't throw out a window ~ Steve Wozniak`

Output `o`

```swift
func secondMostFreqOccurringLetterInAString(_ str: String) -> Character {
    var letterDict = [Character: Int]()
    var mostFreqOccurringCharCount = 0
    var mostFreqOccurrngChar: Character = " "
    var secondMostFreqOcurringCharCount = 0
    var secondMostFreqOcurringChar: Character = "a"
    for char in str where char != " " {
        letterDict[char] = (letterDict[char] ?? 0) + 1
    }
    for (key, value) in letterDict {
        if value > mostFreqOccurringCharCount {
            mostFreqOccurringCharCount = value
            mostFreqOccurrngChar = key
        }
        if value > secondMostFreqOcurringCharCount && value < mostFreqOccurringCharCount {
            secondMostFreqOcurringCharCount = value
            secondMostFreqOcurringChar = key
        }
    }
    return secondMostFreqOcurringChar
}
```
## Closures

1. **Given an array of type [String], return an array that contains the Strings sorted alphabetically with capital letters first (Swift will do that part automatically)**

Input: `["Never", "trust", "a", "computer", "you", "can't", "throw", "out", "a", "window"]`

Output: `["Never", "a", "a", "can\'t", "computer", "out", "throw", "trust", "window", "you"]`
```swift
func sortedString(_ str: [String]) -> [String] {
    str.sorted(by: < )
}
```

2. **Given an array of type [String], return an array that contains the Strings sorted by length**

Input: `["Never", "trust", "a", "computer", "you", "can't", "throw", "out", "a", "window"]`

Output: `["a", "a", "you", "out", "Never", "trust", "can\'t", "throw", "window", "computer"]`
```swift
func sortedStringByLength (_ arrStr: [String]) -> [String] {
    arrStr.sorted(by: { $0.count < $1.count })
}

sortedStringByLength(["Never", "trust", "a", "computer", "you", "can't", "throw", "out", "a", "window"])
```
3. **Given an array of type [String], return an array containing all Strings at least 4 characters long**

Input: `["Never", "trust", "a", "computer", "you", "can't", "throw", "out", "a", "window"]`

Output: `["Never", "trust", "computer", "can\'t", "throw", "window"]`
```swift
func arrayOfStringsCountGreaterThanFour(_ arrStr: [String]) -> [String] {
    arrStr.filter( { $0.count >= 4})
}
```
4. **Given an array of type [String], return a String containing all of the Strings from the array combined and separated by spaces.  Do this first without using the `joined(separator:) method`**

Input: `["Never", "trust", "a", "computer", "you", "can't", "throw", "out", "a", "window"]`

Output: `Never trust a computer you can't throw out a window`
```swift
func arrayOfStringsJoinedTogether (_ arrStr: [String]) -> String {
    var joinedString = ""
    for str in arrStr {
        joinedString += str + " "
    }
    joinedString.removeLast()
    return joinedString
}
```

## Enums


1. **Given an array of type [Int] and an instance of NumberType (defined below), return an array containing only all the even or odd numbers.**

```swift
enum NumberType {
    case even
    case odd
}
```

Input: `[1,2,3,4,5,6], NumberType.odd`

Output: `[1,3,5]`

```swift
func arrayOfOddOrEvenInt(_ arr: [Int],_ numberType: NumberType) -> [Int] {
    switch numberType {
    case .even:
        return arr.filter({$0 % 2 == 0 })
    case .odd:
        return arr.filter({$0 % 2 != 0 })
    }
}
```

2. **Given a String and an instance of StringType (defined below), return the String either lowercased or uppercased**

```swift
enum StringType {
    case lowercase
    case uppercase
}
```

Input: `"Design is not just what it looks like and feels like. Design is how it works", .uppercase`

Output: ``"DESIGN IS NOT JUST WHAT IT LOOKS LIKE AND FEELS LIKE. DESIGN IS HOW IT WORKS"``

```swift
func evenOrOddString( _ str: String, _ stringType: StringType) -> String {
    switch stringType {
    case .lowercase: return str.lowercased()
    case .uppercase: return str.uppercased()
    }
}
```

3. **Given an array of type [FileStatus] (defined below) and an Int, return an array containing only files that were saved more than that many times**

```swift
enum FileStatus: CustomStringConvertible {
    case unsaved
    case saved(numberOfVersions: Int)
    var description: String {
        switch self {
        case .unsaved: return "Unsaved File"
        case let .saved(numberOfVersions): return "File that has been saved \(numberOfVersions) times"
        }
    }
}
```

Input: `[FileStatus.saved(numberOfVersions: 5), FileStatus.saved(numberOfVersions: 3), FileStatus.saved(numberOfVersions: 8)], 4`

Output: `[File that has been saved 5 times, File that has been saved 8 times]`

```swift
func arrayOfFilesSaved(_ fileStatusArr: [FileStatus], num: Int) -> [FileStatus] {
    var newArrayOfFilesSaved = [FileStatus]()
    for file in fileStatusArr {
        switch file {
        case .saved(let numberOfVersions):
            if numberOfVersions > num {
                newArrayOfFilesSaved.append(file)
            }
        case .unsaved: continue
        }
    }
    return newArrayOfFilesSaved
}
```
