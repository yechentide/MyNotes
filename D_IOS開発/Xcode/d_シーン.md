## シーン



### セグエでシーンを移動

`control`を押しながら、ボタンから目標シーンまで線を引っ張る

トランジション：

* Cover Vertical（デフォルト。下から登場）
* Flip Horizontal（左右回転して登場）
* Cross Dissolve（中心から出てくる）
* Partial Curl（紙をめくるような動き）



### コードでシーンを移動

```swift
@IBAction func gotoTreePage(_ sender: Any) {
	// 移動先のビューコントローラを参照する
	let nextVC = self.storyboard?.instantiateViewController(withIdentifier: "treePage")
	// トランジションの映像効果を指定する
	nextVC?.modalTransitionStyle = .flipHorizontal
	// シーンを移動する
	present(nextVC!, animated: true, completion: nil)
}
@IBAction func backButton(_ sender: Any) {
	// 現在のシーンを閉じて元のシーンに戻る
	self.dismiss(animated: true, completion: nil)
}
```



### ナビゲーションコントローラ

複数のシーンが樹木のように枝分かれしたアプリを作れる

storyboardでview controllerを選択し、EditorメニューのEmbed In > Navigation Controllerを選ぶ



### タブバーコントローラ

複数のビューコントローラを並列的に管理して切り替える











