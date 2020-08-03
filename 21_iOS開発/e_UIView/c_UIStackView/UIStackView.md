# UIStackView

## UIStackViewクラス

[UIStackView](https://developer.apple.com/documentation/uikit/UIStackView)
水平方向に並べる`Horizontal Stack View`と垂直方向に並べる`Vertical Stack View`を組み合わせると、
複雑なレイアウトも可能になる

### 継承関係

```swift
class UIStackView : UIView    // : UIResponder : NSObject
```

### コンストラクタ

```swift
init()
init(frame: CGRect)
init(coder: NSCoder)
```

### クラス定義

```swift
open class UIStackView : UIView {

    /* UIStackView enforces that all views in the arrangedSubviews list
     must be subviews of the UIStackView.
        Thus, when a view is added to the arrangedSubviews, UIStackView
     adds it as a subview if it isn't already. And when a view in a
     UIStackView's arrangedSubviews list receives -removeFromSuperview
     it is also removed from the arrangedSubviews.

     Please note that this is a convenience initializer and cannot be overridden in Swift.
     */
    public convenience init(arrangedSubviews views: [UIView]) // Adds views as subviews of the receiver.

    open var arrangedSubviews: [UIView] { get }

    /* Add a view to the end of the arrangedSubviews list.
     Maintains the rule that the arrangedSubviews list is a subset of the
     subviews list by adding the view as a subview of the receiver if
     necessary.
        Does not affect the subview ordering if view is already a subview
     of the receiver.
     */
    open func addArrangedSubview(_ view: UIView)

    /* Removes a subview from the list of arranged subviews without removing it as
     a subview of the receiver.
        To remove the view as a subview, send it -removeFromSuperview as usual;
     the relevant UIStackView will remove it from its arrangedSubviews list
     automatically.
     */
    open func removeArrangedSubview(_ view: UIView)

    /*
     Adds the view as a subview of the container if it isn't already.
        Updates the stack index (but not the subview index) of the
     arranged subview if it's already in the arrangedSubviews list.
     */
    open func insertArrangedSubview(_ view: UIView, at stackIndex: Int)

    /* A stack with a horizontal axis is a row of arrangedSubviews,
    and a stack with a vertical axis is a column of arrangedSubviews.
     */
    open var axis: NSLayoutConstraint.Axis

    /* The layout of the arrangedSubviews along the axis
     */
    open var distribution: UIStackView.Distribution

    /* The layout of the arrangedSubviews transverse to the axis;
     e.g., leading/trailing edges in a vertical stack
     */
    open var alignment: UIStackView.Alignment

    /* Spacing between adjacent edges of arrangedSubviews.
     Used as a strict spacing for the Fill distributions, and
     as a minimum spacing for the EqualCentering and EqualSpacing
     distributions. Use negative values to allow overlap.

     On iOS 11.0 or later, use UIStackViewSpacingUseSystem (Swift: UIStackView.spacingUseSystem)
     to get a system standard spacing value. Setting spacing to UIStackViewSpacingUseDefault
     (Swift: UIStackView.spacingUseDefault) will result in a spacing of 0.

     System spacing between views depends on the views involved, and may vary across the
     stack view.

     In vertical stack views with baselineRelativeArrangement == YES, the spacing between
     text-containing views (such as UILabels) will depend on the fonts involved.
     */
    open var spacing: CGFloat

    /* Set and get custom spacing after a view.

     This custom spacing takes precedence over any other value that might otherwise be used
     for the space following the arranged subview.

     Defaults to UIStackViewSpacingUseDefault (Swift: UIStackView.spacingUseDefault), where
     resolved value will match the spacing property.

     You may also set the custom spacing to UIStackViewSpacingUseSystem (Swift: UIStackView.spacingUseSystem),
     where the resolved value will match the system-defined value for the space to the neighboring view,
     independent of the spacing property.

     Maintained when the arranged subview changes position in the stack view, but not after it
     is removed from the arrangedSubviews list.

     Ignored if arrangedSubview is not actually an arranged subview.
     */
    @available(iOS 11.0, *)
    open func setCustomSpacing(_ spacing: CGFloat, after arrangedSubview: UIView)

    @available(iOS 11.0, *)
    open func customSpacing(after arrangedSubview: UIView) -> CGFloat

    /* Baseline-to-baseline spacing in vertical stacks.
        The baselineRelativeArrangement property supports specifications of vertical
     space from the last baseline of one text-based view to the first baseline of a
     text-based view below, or from the  top (or bottom) of a container to the first
     (or last) baseline of a contained text-based view.
        This property is ignored in horizontal stacks. Use the alignment property
     to specify baseline alignment in horizontal stacks.
        Defaults to NO.
     */
    open var isBaselineRelativeArrangement: Bool

    /* Uses margin layout attributes for edge constraints where applicable.
        Defaults to NO.
     */
    open var isLayoutMarginsRelativeArrangement: Bool
}
```
