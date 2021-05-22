# コンテナビュー

## スタック

* `HStack`：水平方向に並べる
* `VStack`：垂直方向に並べる
* `ZStack`：重ねて表示

```swift
import SwiftUI
struct ContentView: View {
    var body: some View {
        VStack {
            Text("A")
            Text("B")
            Text("C")
        }
    }
}
```

## フォーム

UITableViewみたいな感じ

NavigationViewと組み合わせて使うことが多い

```swift
import SwiftUI

struct ContentView: View {
    
    @State private var textField = ""
    @State private var secureField = ""
    @State private var toggleState = false
    @State private var pickerSelected = 0
    
    var body: some View {
        
        NavigationView {
            Form {
                Text("This is a text")
                TextField("Text Field", text: $textField)
                SecureField("Secure Field", text: $secureField)
                Toggle(isOn: $toggleState, label: {
                    Text("Toggle")
                })
                Picker(selection: $pickerSelected, label: Text("Picker"), content: {
                    Text("Item 1").tag(0)
                    Text("Item 2").tag(1)
                    Text("Item 3").tag(2)
                })
            }
        }
        
    }
}
```

### Section

`Form`ビューの中で、`Section`ビューを使ってセクションを分けられる。

`header`引数には画像などのビューも指定できる

```swift
Form {
    Section(header: HStack {
        Image(systemName: "person.crop.circle")
        Text("Account Data")
    }) {
        Text("aaa")
        Text("bbb")
        Text("ccc")
    }
}
```

## カスタムビュー

デベロッパーが独自に作成するSwiftUIのビューは全てカスタムビューであり、

プロジェクトを作成する時からある`ContentView`もカスタムビューである。

`command`キーを押しながら部品をクリックすると、カスタムビュー(SubView)として抽出できる。

これでコードの階層を浅くできる。

```swift
struct ContentView: View {
    var body: some View {
        VStack {
            subView01()
            subView02()
        }
    }
}
struct subView01: View {
    var body: some View {
        HStack {
            Image(systemName: "trash")
            Image(systemName: "trash")
        }
    }
}

struct subView02: View {
    var body: some View {
        HStack {
            Text("aaa")
            Text("bbb")
        }
    }
}
```

