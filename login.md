```swift
import SwiftUI

struct ContentView: View {
    @State private var username = ""
    @State private var password = ""
    @State private var isLoginSuccessful = false
    
    var body: some View {
        NavigationView {
            VStack {
                Text("Login Form")
                    .font(.largeTitle)
                    .padding(.bottom, 20)
                
                TextField("Username", text: $username)
                    .textFieldStyle(RoundedBorderTextFieldStyle())
                    .padding()
                
                SecureField("Password", text: $password)
                    .textFieldStyle(RoundedBorderTextFieldStyle())
                    .padding()
                
                Button(action: performLogin) {
                    Text("Login")
                        .padding()
                        .background(Color.blue)
                        .foregroundColor(.white)
                        .cornerRadius(10)
                }
                .padding()
                
                NavigationLink(
                    destination: WelcomeView(username: $username),
                    isActive: $isLoginSuccessful,
                    label: { EmptyView() }
                )
            }
            .padding()
        }
    }
    
    func performLogin() {
        // You can implement your authentication logic here.
        // For simplicity, we'll consider it a success if the username and password are both "admin".
        if username == "admin" && password == "admin" {
            isLoginSuccessful = true
        }
    }
}

struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}

struct WelcomeView: View {
    @Binding var username: String
    
    var body: some View {
        VStack {
            Text("Welcome, \(username)!")
                .font(.largeTitle)
                .padding(.bottom, 20)
            
            Text("You have successfully logged in.")
                .font(.headline)
                .padding()
            
            Spacer()
        }
        .navigationBarTitle("")
        .navigationBarHidden(true)
    }
}
```
