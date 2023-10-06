//
//  ExtractedFunctions.swift
//  Week5
//
//  Created by Adesh Shah on 2023-10-05.
//
```swift
import SwiftUI



struct ExtractedFunctions: View {
    var body: some View {
        ZStack{
            Color(.red).ignoresSafeArea()
            contentLayer
   
        }
    }
    var contentLayer: some View{
        HStack{
            MyItem(title: "Apples", count: 1, color: .white)
            MyItem(title: "Oranges", count: 4, color: .orange)
            MyItem(title: "bananas", count: 34, color: .yellow)
        }
    }

}

#Preview {
    ExtractedFunctions()
}

struct MyItem: View {
    
    let title: String
    let count: Int
    let color: Color
    
    var body: some View {
        VStack{
            Text("\(count)")
            Text("\(title)")
        }
        .padding()
        .background(color)
        .cornerRadius(10)
    }
}
```
