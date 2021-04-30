# Timer

## 簡単なサンプルコード

```swift
var count = 0
var timer: Timer? = Timer.scheduledTimer(withTimeInterval: 1.0, repeats: true, block: { timer in
	count += 1
	print("\(count) FIRE!!!")
})
RunLoop.main.add(timer!, forMode: .default)
RunLoop.main.run()

sleep(20)
timer?.invalidate()
timer = nil
```

## Timerの生成

* `TimeInterval型の引数`：実行の時間間隔。単位は秒。
* `repeats`：falseの場合、１回実行した後に、タイマーが自動的に無効になる
* `block`：実行するクロージャ
* `selector`：実行する関数

```swift
class func scheduledTimer(withTimeInterval: TimeInterval, repeats: Bool, block: (Timer) -> Void) -> Timer
class func scheduledTimer(timeInterval: TimeInterval, target: Any, selector: Selector, userInfo: Any?, repeats: Bool) -> Timer
class func scheduledTimer(timeInterval: TimeInterval, invocation: NSInvocation, repeats: Bool) -> Timer

init(timeInterval: TimeInterval, repeats: Bool, block: (Timer) -> Void)
init(timeInterval: TimeInterval, target: Any, selector: Selector, userInfo: Any?, repeats: Bool)
init(timeInterval: TimeInterval, invocation: NSInvocation, repeats: Bool)
init(fire: Date, interval: TimeInterval, repeats: Bool, block: (Timer) -> Void)
init(fireAt: Date, interval: TimeInterval, target: Any, selector: Selector, userInfo: Any?, repeats: Bool)
```

## CLIでの利用

iOSアプリなどでは、Timerをそのまま使えるが、

Command Line Toolの中でTimerを使う場合、`RunLoop`を使う必要がある。

```swift
RunLoop.main.add(タイマー名, forMode: .default)
RunLoop.main.run()
```

[参考：Scheduled Timer won't fire](https://stackoverflow.com/questions/45021881/scheduled-timer-wont-fire)

[参考：When Would You Use a Run Loop?](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/Multithreading/RunLoopManagement/RunLoopManagement.html#//apple_ref/doc/uid/10000057i-CH16-SW24)

