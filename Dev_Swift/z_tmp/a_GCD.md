# 非同期処理①

## GCDを用いる方法

```swift
import Dispatch
import Foundation

// MARK: 既存のdispatch queueの取得
//let queue = DispatchQueue.main
// QoS: 実行優先度。５つのレベルがある
let queue = DispatchQueue.global(qos: .userInitiated)

// MARK: 新規のdispatch queueの生成
//let queue = DispatchQueue(label: "myTestQueue", qos: .default, attributes: [.concurrent], autoreleaseFrequency: .inherit, target: nil)
    
// MARK: dispatch queueへのタスクの追加
queue.async {
    Thread.sleep(forTimeInterval: 2.0)
    if Thread.isMainThread {
        print("メインスレッド")
    } else {
        print("not メインスレッド")
    }
}
print("hhh")
```
