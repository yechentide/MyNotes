# コントロール

### Text

```swift
Text("文字列")
```

### TextField

```swift
import SwiftUI
struct ContentView: View {
    @State private var user = ""
    var body: some View {
        TextField("Enter the username", text: $user)
			.textFieldStyle(RoundedBorderTextFieldStyle())
			.padding()
    }
}
```

### SecureField

```swift
import SwiftUI
struct ContentView: View {
    @State private var pass = ""
    var body: some View {
        SecureField("Enter the pass", text: $pass)
			.textFieldStyle(RoundedBorderTextFieldStyle())
			.padding()
    }
}
```

### Button

```swift
Button(action: /*@START_MENU_TOKEN@*/{}/*@END_MENU_TOKEN@*/, label: {
	Text("Login")
})
Button(action: /*@START_MENU_TOKEN@*/{}/*@END_MENU_TOKEN@*/, label: {
	Image(systemName: "questionmark.circle")		// SF Symbols
})
```

### Toggle

```swift
import SwiftUI
struct ContentView: View {
    @State private var buttonState = true
    var body: some View {
        Toggle(isOn: $buttonState, label: {
			Text("Remember password")
		})
    }
}
```

### Picker

```swift
import SwiftUI
struct ContentView: View {
    @State private var selectedTag = 0
    var body: some View {
        Picker(selection: $selectedTag, label: Text("A Picker"), content: {
			Text("*").tag(0)
			Text("A").tag(1)
			Text("B").tag(2)
			Text("C").tag(3)
		})
    }
}
```

### DatePicker

```swift
import SwiftUI
struct ContentView: View {
    @State private var date = Date()
    var body: some View {
        DatePicker(selection: $date, label: {Text("Date Label")})
    }
}
```

### Slider

```swift
import SwiftUI
struct ContentView: View {
    @State private var sliderValue: Float = 0.5
    var body: some View {
        Slider(value: $sliderValue)
    }
}
```

### Stepper

```swift
import SwiftUI
struct ContentView: View {
    @State private var stepperValue = 3
    var body: some View {
        Stepper(value: $stepperValue, in: 1...9, label: {Text("Label \(self.stepperValue)")})
    }
}
```

