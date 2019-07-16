# Enumerations lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.


## Question 1

a) Define an enumeration called `iOSDeviceType` with member values `iPhone`, `iPad`, `iWatch`. Create a variable called `myDevice` and assign it one member value.

b) Adjust your code above so that `iPhone` and `iPad` have associated values of type String which represents the model number, eg: `iPhone("6 Plus")`. Use a switch case and let syntax to print out the model number of each device.

```
//a


enum IosDeviceType {
 case iPhone(String)
 case iPad(String)
 case iWatch
}

var myDevice = IosDeviceType.iWatch

print(myDevice)


//b

var iPhoneDetails = IosDeviceType.iPhone("6")
var iPadDetails = IosDeviceType.iPad("Mini 5")


switch iPhoneDetails {
 case .iPhone(let iPhoneModel):
  print("iPhone: \(iPhoneModel)")
 default:
  print("")
}

switch iPadDetails {
 case .iPad(let iPadModel):
  print("iPad: \(iPadModel)")
 default:
  print("")
}
```

## Question 2

a) Write an enum called `Shape` and give it cases for `triangle`, `rectangle`, `square`, `pentagon`, and `hexagon`.

b) Write a method inside `Shape` that returns how many sides the shape has. Create a variable called `myFavoritePolygon` and assign it to one of the shapes above, then print out how many sides it has.

c) Re-write `Shape` so that each case has an associated value of type Int that will represent the length of the sides (assume the shapes are regular polygons so all the sides are the same length) and write a method inside that returns the perimeter of the shape.

```
//a

//enum Shape: Int {
//    case triangle = 3
//    case square = 4
//    case rectangle = 8 //4
//    case pentagon = 5
//    case hexagon = 6
//}

//b

//var myFavoritePolygon = Shape.hexagon.rawValue
//print(myFavoritePolygon)

//c

enum Shape {
 case triangle (Int)
 case square (Int)
 case rectangle (Int)
 case pentagon (Int)
 case hexagon (Int)

func findPerimeter() -> Int {
 switch self {
case .triangle(let length):
 return length * 3
case .square(let length):
 return length * 4
case .rectangle(let length):
 return length * 4
case .pentagon(let length):
 return length * 5
case .hexagon(let length):
 return length * 6
}
 }
}

var lengthOfMyFavoritePolygon = Shape.hexagon(13).findPerimeter()
print(lengthOfMyFavoritePolygon)
```
## Question 3

Write an enum called `OperatingSystem` and give it cases for `windows`, `mac`, and `linux`. Create an array of 10 `OperatingSystem` objects where each one is set to a random operating system. Then, iterate through the array and print out a message depending on the operating system.

```
enum OperatingSystem {
 case windows
 case mac
 case linux
}

var osArray = [OperatingSystem.windows, OperatingSystem.mac, OperatingSystem.linux, OperatingSystem.windows, OperatingSystem.mac, OperatingSystem.linux, OperatingSystem.windows,OperatingSystem.mac,OperatingSystem.linux,OperatingSystem.windows]

for i in osArray {
 switch i {
  case OperatingSystem.windows:
   print("Windows")
  case OperatingSystem.mac:
   print("Mac")
  case OperatingSystem.linux:
   print("Linux")
 }
}
```

## Question 4

You are working on a game in which your character is exploring a grid-like map. You get the original location of the character and the steps he will take.

- A step .up will increase the y coordinate by 1.
- A step .down will decrease the y coordinate by 1.
- A step .right will increase the x coordinate by 1.
- A step .left will decrease the x coordinate by 1.
- Print the final location of the character after all the steps have been taken.

```swift
enum Direction {
    case up
    case down
    case left
    case right
}

var location = (x: 0, y: 0)
var steps: [Direction] = [.up, .up, .left, .down, .left]


enum Direction {
 case up
 case down
 case left
 case right
}

var location = (x: 0, y: 0)
var steps: [Direction] = [.up, .up, .left, .down, .left]

for i in steps {
  if i == .up {
   location.1 += 1
  }
  if i == .down {
   location.1 -= 1
  }
  if i == .left {
   location.0 -= 1
  }
  if i == .right {
  location.0 += 1
   }
}

print(location)
```

## Question 5

a) Define an enumeration named `HandShape` with three members: `.rock`, `.paper`, `.scissors`.

b) Define an enumeration named `MatchResult` with three members: `.win`, `.draw`, `.lose`.

c) Write a function called `match` that takes two `HandShapes` and returns a `MatchResult`. It should return the outcome for the first player (the one with the first hand shape).

Hint: Rock beats scissors, paper beats rock, scissor beats paper

```
//a

enum HandShape {
 case rock
 case paper
 case scissors
}


//b

enum MatchResult {
 case win
 case draw
 case lose
}

//c

func match(firstPlayer: HandShape, secondPlayer: HandShape) -> MatchResult {
 switch firstPlayer {
  case .rock:
   switch secondPlayer {
    case .scissors:
     return MatchResult.win
    case .paper:
     return MatchResult.lose
    case .rock:
     return MatchResult.draw
    }
  case .scissors:
   switch secondPlayer {
    case .paper:
     return MatchResult.win
    case .rock:
     return MatchResult.lose
    case .scissors:
     return MatchResult.draw
    }
  case.paper:
   switch secondPlayer {
    case .rock:
     return MatchResult.win
    case .scissors:
     return MatchResult.lose
    case .paper:
     return MatchResult.draw
   }
  }
}

var hero = HandShape.scissors
var villain = HandShape.paper

print(match(firstPlayer: hero, secondPlayer: villain))
```


## Question 6

a) You are given a `CoinType` enumeration which describes different coin values. Print the total value of the coins in the array `moneyArray` which contains tuples of type (`quantity`, `CoinType`).

```swift
enum CoinType: Int {
    case penny = 1
    case nickle = 5
    case dime = 10
    case quarter = 25
}

var moneyArray:[(Int,CoinType)] = [(10,.penny),
                                   (15,.nickle),
                                   (3,.quarter),
                                   (20,.penny),
                                   (3,.dime),
                                   (7,.quarter)]

```

b) Write a method in the `CoinType` enum that returns an Int representing how many coins of that type you need to have a dollar. Then, create an instance of `CoinType` set to `.nickle` and use your method to print out how many nickels you need to have to make a dollar.

```
//a

var total = 0

for i in moneyArray {
total += i.0 * i.1.rawValue
}

print("There are \(total) cents total")


//b

enum CoinType2 {
 case penny
 case nickle
 case dime
 case quarter

func coinsToMakeADollar(coin:CoinType2) -> Int {
  switch coin {
   case .penny:
    return 100
   case .nickle:
    return 20
   case .dime:
    return 10
   case .quarter:
    return 4
  }
 }
}

var nickle = CoinType2.nickle

print(nickle.coinsToMakeADollar(coin: nickle))
```

## Question 7

a) Write an enum called `DayOfWeek` to represent the days of the week with a raw value of type String.

b) Given the array `poorlyFormattedDays`, write code that will produce an array of enums that match the days.

`let poorlyFormattedDays = ["MONDAY", "wednesday", "Sunday", "monday", "Tuesday", "WEDNESDAY", "thursday", "SATURDAY", "tuesday", "FRIDAy", "Wednesday", "Monday", "Friday", "sunday"]`

c) Write a method in `DayOfWeek` called `isWeekend` that determines whether a day is part of the weekend or not and write code to calculate how many week days appear in `poorlyFormattedDays`.

```
//a

enum DaysOfTheWeek: String {
 case monday = "monday"
 case tuesday = "tuesday"
 case wednesday = "wednesday"
 case thursday = "thursday"
 case friday = "friday"
 case saturday = "saturday"
 case sunday = "sunday"
}
```

## Question 8

a) Create an enum called `MetroLine` with cases for the colors of the metro train lines. Create an instance of `MetroLine`.

b) Modify your enum so that each case has an associated value of either Character or Int that will represent the train on that line. Create a new instance of `MetroLine` and give it an appropriate train letter or number.

c) Write code that prints the train letter or number of your instance of `MetroLine`.

```
//a & b

enum MetroLines {
 case red (Int)
 case green (Int)
 case blue (String)
 case orange  (String)
 case yellow (String)
}

var myTrain = MetroLines.green(4)


//c

switch myTrain {
 case .red(let number):
  print(number)
 case .green(let number):
  print(number)
 case .blue(let char):
  print(char)
 case .orange(let char):
  print(char)
 case .yellow(let char):
  print(char)
}
```

## Question 9

a) Think of your own example of something that can be modeled as an enum and write it. Remember that enums allow you to create instances of a defined list of cases.

b) Add a method to your enum.... try to have the method make sense.

```
enum Substances {
 case alcohol
 case blueSky
 case heroin
 case devilsLettuce

func checkSafety() -> Bool {
 switch self {
  case .alcohol:
 return true
  case .blueSky:
 return false
  case .heroin:
 return false //af
  case .devilsLettuce:
 return true
  }
 }
}

var isMaryJaneSafe = Substances.devilsLettuce.checkSafety()

print(isMaryJaneSafe)
```
