# UITextField



## 説明

キーボードからの入力を受け付ける（１行のみ）

複数行を扱うとき、Text Viewを使う



## プロパティ

* placeholder



## コードで生成

```swift
import UIKit

class ViewController: UIViewController, UITextFieldDelegate {
    
    private var myTextField: UITextField!

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        
        // UITextFieldの配置するx,yと幅と高さを設定.
        let tWidth: CGFloat = 200
        let tHeight: CGFloat = 30
        let posX: CGFloat = (self.view.bounds.width - tWidth)/2
        let posY: CGFloat = (self.view.bounds.height - tHeight)/2

        // UITextFieldを作成する.
        myTextField = UITextField(frame: CGRect(x: posX, y: posY, width: tWidth, height: tHeight))

        // 表示する文字を代入する.
        myTextField.text = "Hello TextField"

        // Delegateを自身に設定する
        myTextField.delegate = self

        // 枠を表示する.
        myTextField.borderStyle = .roundedRect

        // クリアボタンを追加.
        myTextField.clearButtonMode = .whileEditing
        
        // 入力された文字を非表示モードにする.(passwd形式)
        // myTextField.isSecureTextEntry = true

        // Viewに追加する
        self.view.addSubview(myTextField)
        
        
    }

    
    /* UITextFieldが編集された直前に呼ばれる */
    func textFieldDidBeginEditing(_ textField: UITextField) {
        print("textFieldDidBeginEditing: \(textField.text!)")
    }

    /* 改行ボタンが押された際に呼ばれる */
    func textFieldShouldReturn(_ textField: UITextField) -> Bool {
        print("textFieldShouldReturn \(textField.text!)")

        // 改行ボタンが押されたらKeyboardを閉じる処理.
        textField.resignFirstResponder()

        return true
    }
    
    /* UITextFieldが編集された直後に呼ばれる */
    func textFieldDidEndEditing(_ textField: UITextField) {
        print("textFieldDidEndEditing: \(textField.text!)")
    }
    
    // 文字数制限を
	 /*　テキストが編集された際に呼ばれる.　*/
    func textField(_ textField: UITextField, shouldChangeCharactersIn range: NSRange, replacementString string: String) -> Bool {

        // 文字数最大を決める.
        let maxLength: Int = 6
        // 入力済みの文字と入力された文字を合わせて取得.
        let str = textField.text! + string
        // 文字数がmaxLength以下ならtrueを返す.
        if str.characters.count < maxLength {
            return true
        }
        print("6文字を超えています")
        return false
    }
}
```



