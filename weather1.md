
```swift
import SwiftUI

struct WeatherView: View {
    var body: some View {
        VStack {
            Text("Today's Weather")
                .font(.title)
                .fontWeight(.bold)
                .padding(.bottom, 20)
            
            HStack {
                Image(systemName: "cloud.sun.fill")
                    .font(.system(size: 60))
                    .foregroundColor(.orange)
                
                VStack(alignment: .leading) {
                    Text("San Francisco, CA")
                        .font(.headline)
                    Text("Sunny")
                        .font(.subheadline)
                }
            }
            
            Spacer()
            
            ZStack {
                RoundedRectangle(cornerRadius: 10)
                    .fill(Color.blue)
                    .frame(height: 60)
                
                HStack {
                    Image(systemName: "thermometer.sun.fill")
                        .font(.system(size: 30))
                        .foregroundColor(.white)
                    Text("72°F")
                        .font(.headline)
                        .foregroundColor(.white)
                    Spacer()
                    Image(systemName: "drop.fill")
                        .font(.system(size: 30))
                        .foregroundColor(.white)
                    Text("40%")
                        .font(.headline)
                        .foregroundColor(.white)
                }
                .padding()
            }
            .padding(.horizontal, 20)
        }
        .padding()
    }
}

struct WeatherView_Previews: PreviewProvider {
    static var previews: some View {
        WeatherView()
    }
}
```
