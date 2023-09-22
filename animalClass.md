```swift
class Animal{
    var species: String
    
    init(species: String){
        self.species = species
    }
    
    func makeSoung(){
        print("Animal makes a sound")
    }
}

class Dog:Animal{
    var breed: String
    
    init(species: String, breed:String){
        self.breed = breed
        super.init(species: species)
    }
    
     func makeSound(){
        print("Dog barks")
    }
}

let dog = Dog(species: "Canine", breed: "Golden Retriever")
dog.makeSound()
```