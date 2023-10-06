
//
//  ParentView.swift
//  Week5
//
//  Created by Adesh Shah on 2023-10-05.
//
```swift
import SwiftUI

struct ParentView: View {

    @State var backgroundColor: Color = Color.green
      var body: some View {
          ZStack{
              backgroundColor.ignoresSafeArea()
              
              ExtractedView(backgroundColor: $backgroundColor)
          }
      }
}

#Preview {
    ParentView()
}

struct ExtractedView: View {
    
    @Binding var backgroundColor: Color

    var body: some View {
        Button(action: {
            backgroundColor = .yellow
        }, label: {
            /*@START_MENU_TOKEN@*/Text("Button")/*@END_MENU_TOKEN@*/.foregroundColor(.white).padding().background(.black).cornerRadius(10)
        })
    }
}
```
