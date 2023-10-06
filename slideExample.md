```swift
//
//  week52.swift
//  Week5
//
//  Created by Adesh Shah on 2023-10-03.
//

import SwiftUI

struct week52: View {
    @State var sliderValue: Double = 10
    @State var color: Color = .red
    var body: some View {
//        VStack {
//            Text("Rating")
//            Text(
//                String(format: "%.0f", sliderValue)
//            )
//            .foregroundStyle(color)
////            Slider(value: $sliderValue)
//            Slider(value: $sliderValue, in: 0...100, step: 1.0, onEditingChanged: { _ in
//                color = .green
//            })
//            .accentColor(.red)
//            
//           
//            
//        }
//        Text("\(sliderValue)")
        Text(String(format: "%.0f", sliderValue))
            .foregroundColor(color)
        Slider(value: $sliderValue, in: 0...255, step: 1, onEditingChanged: { _ in color = .green }).accentColor(.red)
    }
}

#Preview {
    week52()
}
```
