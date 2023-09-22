```swift
struct Temperature {
    var celsius: Double
    
    func toFahrenheit() -> Double{
        return (celsius * 9/5) + 32
    }
}

let todayTemp = Temperature(celsius: 18.0)
var tomorrowTemp = todayTemp // copy is made
tomorrowTemp.celsius = 24.0

todayTemp.toFahrenheit()
tomorrowTemp.toFahrenheit()


// Classes

class BankAccount {
    var balance: Double
    
    init(balance: Double){
        self.balance = balance
    }
    
    func deposit(amount: Double){
        balance += amount
    }
    
    func withdraw(amount: Double){
        if balance >= amount{
            balance -= amount
        }
    }
}

let accountA = BankAccount(balance: 1000.0)
let accountB = accountA

accountA.deposit(amount: 300.0)
accountB.withdraw(amount: 600.0)

accountA.balance
accountB.balance
```