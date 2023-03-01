# Swift Fundamentals Hands-on Guide

Use the below playground to do some hands-on
https://swiftfiddle.com
```
import Foundation

func greet(_ something: String) -> String {
  let greeting = "Hello, " + something + "!"
  return greeting
}

// Prints "Hello, World!"
print(greet("World"))

// Prints "Hello, Swift!"
print(greet("Swift"))


//Variable
var avenger="Iron Man"
avenger="Hulk"

//Const
let baseLocation : String = "Avengers Tower"
baseLocation="New Avengers Facility" //Throws error


//Control statements
let infinityStones = 6
if infinityStones == 6 {
    print("Thanos has all six Infinity Stones!")
} else {
    print("Thanos is missing some stones.")
}

//Guard
func snap() {
    guard infinityStones == 6 else {
        print("Can't snap without all six Infinity Stones!")
        return
    }
    
    print("SNAP! You just wiped out half the universe.")
}

//Function
func addNumbers(num1: Int, num2: Int?) -> Int {
    return num1 + num2
}


//Switch case statements
switch avenger {
case ironMan:
    print("Iron Man has his armor!")
case captainAmerica:
    print("Captain America has his shield!")
case thor:
    print("Thor has his hammer!")
case hulk:
    print("Hulk has his strength!")
case blackWidow:
    print("Black Widow has her agility!")
case hawkeye:
    print("Hawkeye has his bow and arrows!")
default:
    print("Unknown Avenger!")
}

//Struct and Class
struct InfinityStone {
    var name: String
    var color: String
    var power: String
    
    // init(){

    // }

    func activate() {
        print("The \(name) Infinity Stone has been activated!")
    }
}


let timeStone = InfinityStone(name: "Time", color: "Green", power: "Time Manipulation")
timeStone.activate()  // prints "The Time Infinity Stone has been activated!"


class Avenger {
    var name: String
    var weapon: String
    
    init(name: String, weapon: String) {
        self.name = name
        self.weapon = weapon
    }
    deinit()
    {

    }
    
    func attack() {
        print("\(name) attacks with \(weapon)!")
    }
}

// Can be inherited
// Can have de-init==> Destructor
class SuperSoldier: Avenger {
    var serum: String
    
    init(name: String, weapon: String, serum: String) {
        self.serum = serum
        super.init(name: name, weapon: weapon)
    }
    
    override func attack() {
        print("\(name) attacks with \(weapon) and \(serum)!")
    }
}


let captainAmerica = SuperSoldier(name: "Captain America", weapon: "Shield", serum: "Super Soldier Serum")
print(captainAmerica.name)  // prints "Captain America"
captainAmerica.attack()


//Protocol
protocol Superhero {
    var name: String { get }
    var power: String { get }
    
    func attack()
    {
       print("\(name) attacks with repulsor rays!")
    }
}

struct IronMan: Superhero {
    var name: String
    var power: String
    
    // func attack() {
    //     print("\(name) attacks with repulsor rays!")
    // }
}


let ironManInstance= IronMan()
ironManInstance.attack()

//Protocol extension
extension Superhero {
    func attack() {
        print("\(name) attacks with their \(power)!")
    }
}

//Protocol inheritance
protocol EnhancedSuperhero: Superhero {
    var enhancements: [String] { get }
    
    func useEnhancements()
}


//Concurrency

func disableDrones() async {
    // Code to disable Thanos' army of drones
}

func trackInfinityStones() async -> String {
    // Code to locate the Infinity Stones
    return "Location of the Infinity Stones: [latitude, longitude]"
}


//Tasks are similar to 
func saveUniverse() async -> String {
    let disableDronesTask = Task { await disableDrones() }
    let trackInfinityStonesTask = Task { await trackInfinityStones() }
    
    let locationOfInfinityStones = await trackInfinityStonesTask.value
    await disableDronesTask.value
    
    return "The universe has been saved! The location of the Infinity Stones is: \(locationOfInfinityStones)"
}

```

# Some practice questions to make hands dirty

    Protocol Hands-On:

Assemble a team of superheroes by defining a Superhero protocol that includes properties for name and power, and a method for attack(). Then, create two structs that conform to this protocol: IronMan and CaptainAmerica. Implement the attack() method for each struct, with Iron Man attacking with "repulsor rays" and Captain America attacking with his "shield".

    Functions Hands-On:

The Avengers need your help in determining the number of Infinity Stones that they possess. Create a function called countStones() that takes in a dictionary of Infinity Stones as the input, and returns the total number of stones. Each Infinity Stone in the dictionary should be represented as a key-value pair with the name of the stone as the key and a boolean indicating whether or not it is present as the value. For example, the input dictionary may look like this:

let infinityStones = ["Power Stone": true, "Space Stone": false, "Reality Stone": true, "Soul Stone": true, "Time Stone": false, "Mind Stone": true]

The function should return the total number of stones (in this case, 4).

    Concurrency Hands-On:

Thanos is attacking Earth and the Avengers need to disable his army of drones and track the location of the Infinity Stones to save the universe. Use async/await to create two functions: disableDrones() and trackInfinityStones(). The disableDrones() function should contain the code to disable Thanos' army of drones, and the trackInfinityStones() function should contain the code to locate the Infinity Stones. Create a third function called saveUniverse() that calls both disableDrones() and trackInfinityStones() using tasks to run them concurrently. The function should return a string indicating that the universe has been saved and the location of the Infinity Stones.

