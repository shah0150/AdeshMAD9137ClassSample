```swift
// Struct representing a book
struct Book {
    var title: String
    var author: String
    var publicationYear: Int
}

// Class representing library
class Library {
    var books: [Book]
    
    init(books: [Book]){
        self.books = books
    }
    
    // Method to add a book to the library
    func addBook(_ book: Book){
        books.append(book)
    }
    
    // Method to search for books by author
    
    func searchBooks(byAuthor author: String) -> [Book]{
        return books.filter {
            $0.author == author
        }
    }
}

let book1 = Book(title: "Atomic Habits", author: "James Clear", publicationYear: 2019)
let book2 = Book(title: "1984", author: "George Orwell", publicationYear: 1949)

let library = Library(books: [book1, book2])

library.addBook(Book(title: "Flutter", author: "Steve G.", publicationYear: 2024))

let booksBySteve = library.searchBooks(byAuthor: "Steve G.")

for book in booksBySteve{
    print("\(book.title) by \(book.author)")
}

```