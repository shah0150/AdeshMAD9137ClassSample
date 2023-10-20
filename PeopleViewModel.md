```swift
import Foundation

class PeopleModel: ObservableObject {
    // @published will tell our swift UI that this property might actually change and will also read, write and react to.
    @Published var people: [String] = []
    @Published var isLoading: Bool = false
    
    func fetchPeople(){
        isLoading = true
// https://www.hackingwithswift.com/example-code/system/how-to-run-code-after-a-delay-using-asyncafter-and-perform
        
        DispatchQueue.main.asyncAfter(deadline: .now() + 1) {
            self.people = ["Adesh", "Steve", "Tony", "SuCheng"]
            self.isLoading = false
        }
    }
    
}
```
