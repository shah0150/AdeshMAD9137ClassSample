//
//  ContentView.swift
//  Week5
//
//  Created by Adesh Shah on 2023-10-02.
//
```swift
import SwiftUI

struct ContentView: View {
private let mails = Mail.preview
 @State var searchString = ""
    var body: some View {
        NavigationView{
            List(mails){ mail in
                NavigationLink(destination: Text("Hello, I am new destination")) {
                    VStack(alignment: .leading){
                        HStack{
                            Text(mail.sender)
                                .font(.title2)
                                .fontWeight(.medium)
                            Spacer()
                            Text(mail.time)
                                .font(.subheadline)
                                .foregroundColor(.gray)
                        }
                        Text(mail.subject)
                        
                        Text(mail.content)
                            .fontWeight(.light)
                            .foregroundColor(.gray)
                    }
                }
            }
            .listStyle(.inset)
            .searchable(text: $searchString)
            .navigationTitle("Inbox")
            .toolbar{
                ToolbarItem(placement: .primaryAction){
                    EditButton()
                }
                ToolbarItemGroup(placement: .bottomBar){
                    Image(systemName: "line.3.horizontal.decrease.circle")
                        .foregroundColor(/*@START_MENU_TOKEN@*/.blue/*@END_MENU_TOKEN@*/)
                    Spacer()
                    Text("Updated Just Now")
                        .font(.footnote)
                    Spacer()
                    Image(systemName: "square.and.pencil")
                        .foregroundColor(/*@START_MENU_TOKEN@*/.blue/*@END_MENU_TOKEN@*/)
                }
            }
        }
        
        }
    }


#Preview {
    ContentView()
}
```
