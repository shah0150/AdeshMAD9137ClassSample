```swift
import SwiftUI

// Create a struct to represent the data model
struct Country: Identifiable, Codable {
    let id = UUID()
    let name: String
    let capital: String
    let population: Int
}

// Create a SwiftUI view that fetches and displays data
struct ContentView: View {
    @State private var countries: [Country] = []
    @State private var isLoading = false
    @State private var error: Error?

    var body: some View {
        NavigationView {
            List {
                if isLoading {
                    ProgressView()
                } else if !countries.isEmpty {
                    ForEach(countries) { country in
                        VStack(alignment: .leading) {
                            Text("Name: \(country.name)")
                                .font(.headline)
                            Text("Capital: \(country.capital)")
                            Text("Population: \(country.population)")
                        }
                    }
                } else {
                    Text("No data available")
                }
            }
            .navigationBarTitle("Countries")
        }
        .onAppear(perform: fetchData)
    }

    func fetchData() {
        isLoading = true
        error = nil
        if let url = URL(string: "https://raw.githubusercontent.com/shah0150/data/main/countries_data.json") {
            URLSession.shared.dataTask(with: url) { data, response, error in
                DispatchQueue.main.async {
                    isLoading = false
                    if let data = data {
                        do {
                            countries = try JSONDecoder().decode([Country].self, from: data)
                        } catch {
                            self.error = error
                        }
                    } else if let error = error {
                        self.error = error
                    }
                }
            }.resume()
        }
    }
}

struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}

```
