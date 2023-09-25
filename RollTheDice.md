```swift
import SwiftUI

struct ContentView: View {
    
    @State private var result = "0"
    var body: some View {
            VStack{
                Button("Roll the dice"){
                    result = String(Int.random(in: 1..<7))
                }
                Text(result)
                    .bold()
                    .font(.system(size: 40))
            }
            
        
    }
    }
struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}
```
