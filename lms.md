```swift
import SwiftUI

struct Book: Identifiable {
    let id = UUID()
    let title: String
    let author: String
}

struct ContentView: View {
    @State private var library = [
        Book(title: "Book 1", author: "Author 1"),
        Book(title: "Book 2", author: "Author 2"),
        Book(title: "Book 3", author: "Author 3")
    ]
    
    @State private var newTitle = ""
    @State private var newAuthor = ""
    
    var body: some View {
        NavigationView {
            List {
                ForEach(library) { book in
                    Text("\(book.title) by \(book.author)")
                }
                .onDelete(perform: deleteBook)
            }
            .navigationBarTitle("Library")
            .navigationBarItems(trailing: Button(action: addBook) {
                Image(systemName: "plus")
            })
            
            Form {
                Section(header: Text("Add a New Book")) {
                    TextField("Title", text: $newTitle)
                    TextField("Author", text: $newAuthor)
                    Button(action: addBook) {
                        Text("Add Book")
                    }
                }
            }
        }
    }
    
    func addBook() {
        if !newTitle.isEmpty && !newAuthor.isEmpty {
            let newBook = Book(title: newTitle, author: newAuthor)
            library.append(newBook)
            newTitle = ""
            newAuthor = ""
        }
    }
    
    func deleteBook(at offsets: IndexSet) {
        library.remove(atOffsets: offsets)
    }
}

@main
struct LibraryManagementApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```
