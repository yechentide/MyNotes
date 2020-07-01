# UIView





## UIView

https://developer.apple.com/documentation/uikit/UIView



### 継承関係

```swift
class UIView : UIResponder		// : NSObject
```



### コンストラクタ

```swift
init()
init(frame: CGRect)
init?(coder: NSCoder)
```



### クラス定義

```swift
open class UIView : UIResponder, NSCoding, UIAppearance, UIAppearanceContainer, UIDynamicItem, UITraitEnvironment, UICoordinateSpace, UIFocusItem, UIFocusItemContainer, CALayerDelegate {

    open class var layerClass: AnyClass { get }

    public init(frame: CGRect)

    public init?(coder: NSCoder)

    open var isUserInteractionEnabled: Bool

    open var tag: Int

    open var layer: CALayer { get }

    @available(iOS 9.0, *)
    open var canBecomeFocused: Bool { get }

    @available(iOS 9.0, *)
    open var isFocused: Bool { get }

    @available(iOS 9.0, *)
    open var semanticContentAttribute: UISemanticContentAttribute

    @available(iOS 9.0, *)
    open class func userInterfaceLayoutDirection(for attribute: UISemanticContentAttribute) -> UIUserInterfaceLayoutDirection

    @available(iOS 10.0, *)
    open class func userInterfaceLayoutDirection(for semanticContentAttribute: UISemanticContentAttribute, relativeTo layoutDirection: UIUserInterfaceLayoutDirection) -> UIUserInterfaceLayoutDirection

    @available(iOS 10.0, *)
    open var effectiveUserInterfaceLayoutDirection: UIUserInterfaceLayoutDirection { get }
}

extension UIView {
}
extension UIView {

    open var frame: CGRect

    open var bounds: CGRect

    open var center: CGPoint

    open var transform: CGAffineTransform

    @available(iOS 12.0, *)
    open var transform3D: CATransform3D

    @available(iOS 4.0, *)
    open var contentScaleFactor: CGFloat

    open var isMultipleTouchEnabled: Bool

    open var isExclusiveTouch: Bool

    open func hitTest(_ point: CGPoint, with event: UIEvent?) -> UIView?

    open func point(inside point: CGPoint, with event: UIEvent?) -> Bool

    open func convert(_ point: CGPoint, to view: UIView?) -> CGPoint

    open func convert(_ point: CGPoint, from view: UIView?) -> CGPoint

    open func convert(_ rect: CGRect, to view: UIView?) -> CGRect

    open func convert(_ rect: CGRect, from view: UIView?) -> CGRect

    open var autoresizesSubviews: Bool

    open var autoresizingMask: UIView.AutoresizingMask

    open func sizeThatFits(_ size: CGSize) -> CGSize

    open func sizeToFit()
}
extension UIView {

    open var superview: UIView? { get }

    open var subviews: [UIView] { get }

    open var window: UIWindow? { get }

    open func removeFromSuperview()

    open func insertSubview(_ view: UIView, at index: Int)

    open func exchangeSubview(at index1: Int, withSubviewAt index2: Int)

    open func addSubview(_ view: UIView)

    open func insertSubview(_ view: UIView, belowSubview siblingSubview: UIView)

    open func insertSubview(_ view: UIView, aboveSubview siblingSubview: UIView)

    open func bringSubviewToFront(_ view: UIView)

    open func sendSubviewToBack(_ view: UIView)

    open func didAddSubview(_ subview: UIView)

    open func willRemoveSubview(_ subview: UIView)

    open func willMove(toSuperview newSuperview: UIView?)

    open func didMoveToSuperview()

    open func willMove(toWindow newWindow: UIWindow?)

    open func didMoveToWindow()

    open func isDescendant(of view: UIView) -> Bool

    open func viewWithTag(_ tag: Int) -> UIView?

    open func setNeedsLayout()

    open func layoutIfNeeded()

    open func layoutSubviews()

    @available(iOS 8.0, *)
    open var layoutMargins: UIEdgeInsets

    @available(iOS 11.0, *)
    open var directionalLayoutMargins: NSDirectionalEdgeInsets

    @available(iOS 8.0, *)
    open var preservesSuperviewLayoutMargins: Bool

    @available(iOS 11.0, *)
    open var insetsLayoutMarginsFromSafeArea: Bool

    @available(iOS 8.0, *)
    open func layoutMarginsDidChange()

    @available(iOS 11.0, *)
    open var safeAreaInsets: UIEdgeInsets { get }

    @available(iOS 11.0, *)
    open func safeAreaInsetsDidChange()

    @available(iOS 9.0, *)
    open var layoutMarginsGuide: UILayoutGuide { get }

    /// This content guide provides a layout area that you can use to place text and related content whose width should generally be constrained to a size that is easy for the user to read. This guide provides a centered region that you can place content within to get this behavior for this view.
    @available(iOS 9.0, *)
    open var readableContentGuide: UILayoutGuide { get }

    @available(iOS 11.0, *)
    open var safeAreaLayoutGuide: UILayoutGuide { get }
}
extension UIView {

    open func draw(_ rect: CGRect)

    open func setNeedsDisplay()

    open func setNeedsDisplay(_ rect: CGRect)

    open var clipsToBounds: Bool

    @NSCopying open var backgroundColor: UIColor?

    open var alpha: CGFloat

    open var isOpaque: Bool

    open var clearsContextBeforeDrawing: Bool

    open var isHidden: Bool

    open var contentMode: UIView.ContentMode

    @available(iOS 8.0, *)
    open var mask: UIView?

    @available(iOS 7.0, *)
    open var tintColor: UIColor!

    @available(iOS 7.0, *)
    open var tintAdjustmentMode: UIView.TintAdjustmentMode

    @available(iOS 7.0, *)
    open func tintColorDidChange()
}
extension UIView {

    open class func setAnimationsEnabled(_ enabled: Bool)

    open class var areAnimationsEnabled: Bool { get }

    @available(iOS 7.0, *)
    open class func performWithoutAnimation(_ actionsWithoutAnimation: () -> Void)

    @available(iOS 9.0, *)
    open class var inheritedAnimationDuration: TimeInterval { get }
}
extension UIView {

    @available(iOS 4.0, *)
    open class func animate(withDuration duration: TimeInterval, delay: TimeInterval, options: UIView.AnimationOptions = [], animations: @escaping () -> Void, completion: ((Bool) -> Void)? = nil)

    @available(iOS 4.0, *)
    open class func animate(withDuration duration: TimeInterval, animations: @escaping () -> Void, completion: ((Bool) -> Void)? = nil)

    @available(iOS 4.0, *)
    open class func animate(withDuration duration: TimeInterval, animations: @escaping () -> Void)

    @available(iOS 7.0, *)
    open class func animate(withDuration duration: TimeInterval, delay: TimeInterval, usingSpringWithDamping dampingRatio: CGFloat, initialSpringVelocity velocity: CGFloat, options: UIView.AnimationOptions = [], animations: @escaping () -> Void, completion: ((Bool) -> Void)? = nil)

    @available(iOS 4.0, *)
    open class func transition(with view: UIView, duration: TimeInterval, options: UIView.AnimationOptions = [], animations: (() -> Void)?, completion: ((Bool) -> Void)? = nil)

    @available(iOS 4.0, *)
    open class func transition(from fromView: UIView, to toView: UIView, duration: TimeInterval, options: UIView.AnimationOptions = [], completion: ((Bool) -> Void)? = nil)

    @available(iOS 7.0, *)
    open class func perform(_ animation: UIView.SystemAnimation, on views: [UIView], options: UIView.AnimationOptions = [], animations parallelAnimations: (() -> Void)?, completion: ((Bool) -> Void)? = nil)

    @available(iOS 12.0, *)
    open class func modifyAnimations(withRepeatCount count: CGFloat, autoreverses: Bool, animations: () -> Void)
}
extension UIView {

    @available(iOS 7.0, *)
    open class func animateKeyframes(withDuration duration: TimeInterval, delay: TimeInterval, options: UIView.KeyframeAnimationOptions = [], animations: @escaping () -> Void, completion: ((Bool) -> Void)? = nil)

    @available(iOS 7.0, *)
    open class func addKeyframe(withRelativeStartTime frameStartTime: Double, relativeDuration frameDuration: Double, animations: @escaping () -> Void)
}
extension UIView {

    @available(iOS 3.2, *)
    open var gestureRecognizers: [UIGestureRecognizer]?

    @available(iOS 3.2, *)
    open func addGestureRecognizer(_ gestureRecognizer: UIGestureRecognizer)

    @available(iOS 3.2, *)
    open func removeGestureRecognizer(_ gestureRecognizer: UIGestureRecognizer)

    @available(iOS 6.0, *)
    open func gestureRecognizerShouldBegin(_ gestureRecognizer: UIGestureRecognizer) -> Bool
}
```





