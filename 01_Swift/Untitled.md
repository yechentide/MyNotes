# いろいろ

## Decode (Dataから別の型に変換)

### Data  -->  FixedWidthInteger

```swift
self.init(bigEndian: 
	data[data.startIndex..<(data.startIndex + length)]
	.advanced(by: 0)
	.withUnsafeBytes {
		$0.load(as: Self.self)
	})
self.init(littleEndian: nbtData.withUnsafeBytes{
	$0.load(as: Self.self)
})
```

### Data  -->  Float

```swift
self.init(bitPattern: 
	data[data.startIndex..<(data.startIndex + length)]
	.advanced(by: 0)
	.withUnsafeBytes {
        UInt32(bigEndian: $0.load(as: UInt32.self))			// Doubleの場合はUInt64.self
    })
self.init(bitPattern: nbtData.withUnsafeBytes{
	$0.load(as: UInt32.self)								// Doubleの場合はUInt64.self
})
```

### Data  -->  String

```swift
self.init(data: nbtData, encoding: .utf8)!
```

## Encode (Dataに変換)

### FixedWidthInteger  -->  Data

```swift
withUnsafeBytes(of: bigEndian) { Data($0) }
```

### Float  -->  Data

```swift
withUnsafeBytes(of: bitPattern.bigEndian) { Data($0) }
```

## プロトコル

### 整数タグ

* FixedWidthInteger

### 文字列タグ

* RawRepresentable
* Hashable

### リストタグ

* RandomAccessCollection
* RangeReplaceableCollection