# WeatherKitSampleData
Sample weather data for developing with WeatherKit

## Usage

###### Create a static var in a `Weather` extension to load the sample data.

```swift
extension Weather {
    static var sample: Weather {
        print("loading preview data...")
       
        let data: Data

        guard let file = Bundle.main.url(forResource: "weather", withExtension: "json")
        else {
            fatalError("Couldn't find weather.json in main bundle.")
        }
        
        do {
            data = try Data(contentsOf: file)
        } catch {
            fatalError("Couldn't load weather.json from main bundle:\n\(error)")
        }
        
        do {
            return try JSONDecoder().decode(Weather.self, from: data)
        } catch {
            fatalError("Couldn't parse weather.json as \(Weather.self):\n\(error)")
        }
    }
}
```

###### Access the sample data

```swift
Weather.sample
```
