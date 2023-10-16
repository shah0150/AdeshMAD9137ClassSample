```swift
import SwiftUI

struct Country: Identifiable, Decodable {
    let id = UUID()
    let name: String
    let capital: String
    let population: Int
    let region: String
}

struct ContentView: View {
    @State private var countries: [Country] = []
    @State private var isLoading = false
    @State private var error: Error?

    var body: some View {
        NavigationView {
            ScrollView {
                LazyVGrid(columns: [GridItem(.flexible(minimum: 150, maximum: 200), spacing: 16)], spacing: 16) {
                    ForEach(countries) { country in
                        CountryCard(country: country)
                    }
                }
                .padding()
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

struct CountryCard: View {
    var country: Country

    var body: some View {
        VStack {
            Text(country.name)
                .font(.title)
                .fontWeight(.bold)
                .padding(.bottom, 5)

            Text("Capital: \(country.capital)")
                .font(.subheadline)
                .foregroundColor(.gray)
                .padding(.bottom, 2)

            Text("Population: \(country.population)")
                .font(.subheadline)
                .foregroundColor(.gray)
                .padding(.bottom, 2)

            Text("Region: \(country.region)")
                .font(.subheadline)
                .foregroundColor(.gray)
                .padding(.bottom, 2)
        }
        .frame(maxWidth: .infinity)
        .padding()
        .background(Color.white)
        .cornerRadius(10)
        .shadow(radius: 5)
    }
}
```
