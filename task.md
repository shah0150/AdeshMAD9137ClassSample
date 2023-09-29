```swift
import SwiftUI

struct ContentView: View {
    @State private var tasks = ["Buy groceries", "Write code", "Walk the dog"]
    @State private var newTask = ""

    var body: some View {
        NavigationView {
            VStack {
                List {
                    ForEach(tasks, id: \.self) { task in
                        Text(task)
                    }
                    .onDelete(perform: deleteTask)
                }

                HStack {
                    TextField("New Task", text: $newTask)
                        .textFieldStyle(RoundedBorderTextFieldStyle())
                    
                    Button(action: addTask) {
                        Text("Add")
                    }
                }
                .padding()
            }
            .navigationBarTitle("To-Do List")
        }
    }

    func addTask() {
        if !newTask.isEmpty {
            tasks.append(newTask)
            newTask = ""
        }
    }

    func deleteTask(at offsets: IndexSet) {
        tasks.remove(atOffsets: offsets)
    }
}
```
struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}
