# 標準出入力

## 標準出力

### コンソールに出力

```swift
print()								// 改行
print("a", terminator: "")			// 改行しない
print("b", "b", separator: "-")		// "b-b"
```

## 標準入力

### Command Line Tool

Playgroundでは使えないので、Command Line Toolプロジェクトの中で使う

```swift
let line = readLine()!
let nums = readLine()!.split(separator: " ").map{ Int($0)! }
```
