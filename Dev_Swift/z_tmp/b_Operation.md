# 非同期処理②

## Operation, OperationQueueクラスを用いる方法

```swift
import Foundation

/// - Operation: タスクとその情報
/// - OperationQueue: タスクを実行するキュー
class MyTask: Operation {
    let number: Int
    init(number: Int) { self.number = number }

    override func main() {
        Thread.sleep(forTimeInterval: 1.0)
        guard !isCancelled else {return}    // タスクがキャンセルされる時の対応
        print(number)
    }
}

let queue = OperationQueue()
queue.name = "my queue"
queue.maxConcurrentOperationCount = 2   // 並行に実行するタスクの最大数
queue.qualityOfService = .userInitiated

var tasks = [MyTask]()
for i in 0..<10 {
    tasks.append(MyTask(number: i))
    // tasks[i].addDependency(task[j])　を使うことで、task[j]が終わってからtask[i]が実行される
}

queue.addOperations(tasks, waitUntilFinished: false)
print("タスクが追加された")
tasks[6].cancel()       // タスクをキャンセル
```
