//
//  BinUI.swift
//  Week5
//
//  Created by Adesh Shah on 2023-10-05.
//
```swift
import SwiftUI

struct BinUI: View {
    
    @State var backgroundColor: Color = Color.red
    
    var body: some View {
        ZStack{
            backgroundColor
                .ignoresSafeArea()
            contentLayer
        }
}
    
    var contentLayer: some View{
        VStack{
            Text("Color Change")
                .font(.largeTitle)
            Button(action: {
                btnPressed()
            }, label: {
                Text("Change Color")
                    .foregroundColor(.white)
                    .padding()
                    .background(.black)
                    .cornerRadius(10)
            })
        }
    }
    
    func btnPressed(){
        backgroundColor = .indigo
    }
}

#Preview {
    BinUI()
}

```
