# 非同期処理③

## Threadクラスを用いる方法

```swift
import Foundation

class MyThread: Thread {
    override func main() {
        print("executed.")
    }
}
let thread = MyThread()
thread.start()
```
