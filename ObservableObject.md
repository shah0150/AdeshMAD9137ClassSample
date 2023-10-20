```swift
import SwiftUI

struct ContentView: View {
    
    @StateObject private var vm = PeopleModel()
    
    
  var body: some View {
      VStack{
          if vm.isLoading {
              ProgressView()
              Text("Loading...")
                  .padding()
          }
          else {
              Text(vm.people.isEmpty ? "No Users" : "Managed to get \(vm.people.count) users")
          }
          Button(action: vm.fetchPeople) {
              Text("Get Data")
          }
      }
  }
}

#Preview {
    ContentView()
}
```
