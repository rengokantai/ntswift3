#Deinitialization
A deinitializer is called immediately before a class instance is deallocated.Deinitializers are only available on class types.

##How Deinitialization Works
Superclass deinitializers are inherited by their subclasses, 
and the superclass deinitializer is called automatically at the end of a subclass deinitializer implementation.  


using instance=nil to deinit.  
Ex:
```
class Bank {
    static var coinsInBank = 10_000
    static func distribute(coins numberOfCoinsRequested: Int) -> Int {
        let numberOfCoinsToVend = min(numberOfCoinsRequested, coinsInBank)
        coinsInBank -= numberOfCoinsToVend
        return numberOfCoinsToVend
    }
    static func receive(coins: Int) {
        coinsInBank += coins
    }
}

class Player {
    var coinsInPurse: Int
    init(coins: Int) {
        coinsInPurse = Bank.distribute(coins: coins)
    }
    func win(coins: Int) {
        coinsInPurse += Bank.distribute(coins: coins)
    }
    deinit {
        Bank.receive(coins: coinsInPurse)
    }
}
```
impl
```
var playerOne: Player? = Player(coins: 100) //player 100 bank 9900
playerOne!.win(coins: 2_000)  //player 2100 bank 7900
playerOne = nil //bank 10000
```
