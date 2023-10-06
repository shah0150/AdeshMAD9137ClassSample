```swift
struct Mail: Identifiable{
    
    let id = UUID()
    
    let sender: String
    let time: String
    let subject: String
    let content: String
    
    static let preview: [Mail] = Array(repeating: Mail(sender: "Adesh Shah", time: "11:11 AM", subject: "MAD9137 Assignment 1", content: "Please look at your brightspace for MAD9137 assignment due on October 19 at 11:59 PM"), count: 20)
    
    
}
```
