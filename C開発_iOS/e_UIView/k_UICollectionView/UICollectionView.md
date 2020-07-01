# UICollectionView





## UICollectionView

https://developer.apple.com/documentation/uikit/UICollectionView



### 継承関係

```swift
class UICollectionView : UIScrollView		// : UIView : UIResponder : NSObject
```



### コンストラクタ

```swift
init()
init(frame: CGRect, collectionViewLayout: UICollectionViewLayout)
init?(coder: NSCoder)
```



### クラス定義

```swift
open class UICollectionView : UIScrollView, UIDataSourceTranslating {

    
    public init(frame: CGRect, collectionViewLayout layout: UICollectionViewLayout)

    public init?(coder: NSCoder)

    
    open var collectionViewLayout: UICollectionViewLayout

    weak open var delegate: UICollectionViewDelegate?

    weak open var dataSource: UICollectionViewDataSource?

    
    @available(iOS 10.0, *)
    weak open var prefetchDataSource: UICollectionViewDataSourcePrefetching?

    @available(iOS 10.0, *)
    open var isPrefetchingEnabled: Bool

    
    @available(iOS 11.0, *)
    weak open var dragDelegate: UICollectionViewDragDelegate?

    @available(iOS 11.0, *)
    weak open var dropDelegate: UICollectionViewDropDelegate?

    
    /* To enable intra-app drags on iPhone, set this to YES.
     * You can also force drags to be disabled for this collection view by setting this to NO.
     * By default, For iPad this will return YES and iPhone will return NO.
     */
    @available(iOS 11.0, *)
    open var dragInteractionEnabled: Bool

    
    /* Reordering cadence affects how easily reordering occurs while dragging around a reorder-capable drop destination.
     * Default is UICollectionViewReorderingCadenceImmediate.
     */
    @available(iOS 11.0, *)
    open var reorderingCadence: UICollectionView.ReorderingCadence

    
    open var backgroundView: UIView? // will be automatically resized to track the size of the collection view and placed behind all cells and supplementary views.

    
    // For each reuse identifier that the collection view will use, register either a class or a nib from which to instantiate a cell.
    // If a nib is registered, it must contain exactly 1 top level object which is a UICollectionViewCell.
    // If a class is registered, it will be instantiated via alloc/initWithFrame:
    open func register(_ cellClass: AnyClass?, forCellWithReuseIdentifier identifier: String)

    open func register(_ nib: UINib?, forCellWithReuseIdentifier identifier: String)

    
    open func register(_ viewClass: AnyClass?, forSupplementaryViewOfKind elementKind: String, withReuseIdentifier identifier: String)

    open func register(_ nib: UINib?, forSupplementaryViewOfKind kind: String, withReuseIdentifier identifier: String)

    
    open func dequeueReusableCell(withReuseIdentifier identifier: String, for indexPath: IndexPath) -> UICollectionViewCell

    open func dequeueReusableSupplementaryView(ofKind elementKind: String, withReuseIdentifier identifier: String, for indexPath: IndexPath) -> UICollectionReusableView

    
    // These properties control whether items can be selected, and if so, whether multiple items can be simultaneously selected.
    open var allowsSelection: Bool // default is YES

    open var allowsMultipleSelection: Bool // default is NO

    
    open var indexPathsForSelectedItems: [IndexPath]? { get } // returns nil or an array of selected index paths

    open func selectItem(at indexPath: IndexPath?, animated: Bool, scrollPosition: UICollectionView.ScrollPosition)

    open func deselectItem(at indexPath: IndexPath, animated: Bool)

    
    // Returns YES if the collection view is reordering or has drop placeholders.
    @available(iOS 11.0, *)
    open var hasUncommittedUpdates: Bool { get }

    
    // Note: -reloadData will discard any uncommitted updates (e.g. placeholders)
    open func reloadData() // discard the dataSource and delegate data and requery as necessary

    
    open func setCollectionViewLayout(_ layout: UICollectionViewLayout, animated: Bool) // transition from one layout to another

    @available(iOS 7.0, *)
    open func setCollectionViewLayout(_ layout: UICollectionViewLayout, animated: Bool, completion: ((Bool) -> Void)? = nil)

    
    @available(iOS 7.0, *)
    open func startInteractiveTransition(to layout: UICollectionViewLayout, completion: UICollectionView.LayoutInteractiveTransitionCompletion? = nil) -> UICollectionViewTransitionLayout

    @available(iOS 7.0, *)
    open func finishInteractiveTransition()

    @available(iOS 7.0, *)
    open func cancelInteractiveTransition()

    
    // Information about the current state of the collection view.
    
    open var numberOfSections: Int { get }

    open func numberOfItems(inSection section: Int) -> Int

    
    open func layoutAttributesForItem(at indexPath: IndexPath) -> UICollectionViewLayoutAttributes?

    open func layoutAttributesForSupplementaryElement(ofKind kind: String, at indexPath: IndexPath) -> UICollectionViewLayoutAttributes?

    
    open func indexPathForItem(at point: CGPoint) -> IndexPath?

    open func indexPath(for cell: UICollectionViewCell) -> IndexPath?

    
    open func cellForItem(at indexPath: IndexPath) -> UICollectionViewCell?

    open var visibleCells: [UICollectionViewCell] { get }

    open var indexPathsForVisibleItems: [IndexPath] { get }

    
    @available(iOS 9.0, *)
    open func supplementaryView(forElementKind elementKind: String, at indexPath: IndexPath) -> UICollectionReusableView?

    @available(iOS 9.0, *)
    open func visibleSupplementaryViews(ofKind elementKind: String) -> [UICollectionReusableView]

    @available(iOS 9.0, *)
    open func indexPathsForVisibleSupplementaryElements(ofKind elementKind: String) -> [IndexPath]

    
    // Interacting with the collection view.
    
    open func scrollToItem(at indexPath: IndexPath, at scrollPosition: UICollectionView.ScrollPosition, animated: Bool)

    
    // These methods allow dynamic modification of the current set of items in the collection view
    open func insertSections(_ sections: IndexSet)

    open func deleteSections(_ sections: IndexSet)

    open func reloadSections(_ sections: IndexSet)

    open func moveSection(_ section: Int, toSection newSection: Int)

    
    open func insertItems(at indexPaths: [IndexPath])

    open func deleteItems(at indexPaths: [IndexPath])

    open func reloadItems(at indexPaths: [IndexPath])

    open func moveItem(at indexPath: IndexPath, to newIndexPath: IndexPath)

    
    open func performBatchUpdates(_ updates: (() -> Void)?, completion: ((Bool) -> Void)? = nil) // allows multiple insert/delete/reload/move calls to be animated simultaneously. Nestable.

    
    // Support for reordering
    @available(iOS 9.0, *)
    open func beginInteractiveMovementForItem(at indexPath: IndexPath) -> Bool // returns NO if reordering was prevented from beginning - otherwise YES

    @available(iOS 9.0, *)
    open func updateInteractiveMovementTargetPosition(_ targetPosition: CGPoint)

    @available(iOS 9.0, *)
    open func endInteractiveMovement()

    @available(iOS 9.0, *)
    open func cancelInteractiveMovement()

    
    // Support for Focus
    @available(iOS 9.0, *)
    open var remembersLastFocusedIndexPath: Bool // defaults to NO. If YES, when focusing on a collection view the last focused index path is focused automatically. If the collection view has never been focused, then the preferred focused index path is used.

    
    // Drag & Drop
    
    /* YES if a drag session is currently active. A drag session begins after items are "lifted" from the collection view.
     */
    @available(iOS 11.0, *)
    open var hasActiveDrag: Bool { get }

    
    /* YES if collection view is currently tracking a drop session.
     */
    @available(iOS 11.0, *)
    open var hasActiveDrop: Bool { get }
}
```



### UICollectionViewDataSource

```swift
public protocol UICollectionViewDataSource : NSObjectProtocol {

    
    @available(iOS 6.0, *)
    func collectionView(_ collectionView: UICollectionView, numberOfItemsInSection section: Int) -> Int

    
    // The cell that is returned must be retrieved from a call to -dequeueReusableCellWithReuseIdentifier:forIndexPath:
    @available(iOS 6.0, *)
    func collectionView(_ collectionView: UICollectionView, cellForItemAt indexPath: IndexPath) -> UICollectionViewCell

    
    @available(iOS 6.0, *)
    optional func numberOfSections(in collectionView: UICollectionView) -> Int

    
    // The view that is returned must be retrieved from a call to -dequeueReusableSupplementaryViewOfKind:withReuseIdentifier:forIndexPath:
    @available(iOS 6.0, *)
    optional func collectionView(_ collectionView: UICollectionView, viewForSupplementaryElementOfKind kind: String, at indexPath: IndexPath) -> UICollectionReusableView

    
    @available(iOS 9.0, *)
    optional func collectionView(_ collectionView: UICollectionView, canMoveItemAt indexPath: IndexPath) -> Bool

    @available(iOS 9.0, *)
    optional func collectionView(_ collectionView: UICollectionView, moveItemAt sourceIndexPath: IndexPath, to destinationIndexPath: IndexPath)

    
    /// Returns a list of index titles to display in the index view (e.g. ["A", "B", "C" ... "Z", "#"])
    @available(iOS 6.0, *)
    optional func indexTitles(for collectionView: UICollectionView) -> [String]?

    
    /// Returns the index path that corresponds to the given title / index. (e.g. "B",1)
    /// Return an index path with a single index to indicate an entire section, instead of a specific item.
    @available(iOS 6.0, *)
    optional func collectionView(_ collectionView: UICollectionView, indexPathForIndexTitle title: String, at index: Int) -> IndexPath
}
```





### UICollectionViewDelegate

```swift
public protocol UICollectionViewDelegate : UIScrollViewDelegate {

    
    // Methods for notification of selection/deselection and highlight/unhighlight events.
    // The sequence of calls leading to selection from a user touch is:
    //
    // (when the touch begins)
    // 1. -collectionView:shouldHighlightItemAtIndexPath:
    // 2. -collectionView:didHighlightItemAtIndexPath:
    //
    // (when the touch lifts)
    // 3. -collectionView:shouldSelectItemAtIndexPath: or -collectionView:shouldDeselectItemAtIndexPath:
    // 4. -collectionView:didSelectItemAtIndexPath: or -collectionView:didDeselectItemAtIndexPath:
    // 5. -collectionView:didUnhighlightItemAtIndexPath:
    @available(iOS 6.0, *)
    optional func collectionView(_ collectionView: UICollectionView, shouldHighlightItemAt indexPath: IndexPath) -> Bool

    @available(iOS 6.0, *)
    optional func collectionView(_ collectionView: UICollectionView, didHighlightItemAt indexPath: IndexPath)

    @available(iOS 6.0, *)
    optional func collectionView(_ collectionView: UICollectionView, didUnhighlightItemAt indexPath: IndexPath)

    @available(iOS 6.0, *)
    optional func collectionView(_ collectionView: UICollectionView, shouldSelectItemAt indexPath: IndexPath) -> Bool

    @available(iOS 6.0, *)
    optional func collectionView(_ collectionView: UICollectionView, shouldDeselectItemAt indexPath: IndexPath) -> Bool // called when the user taps on an already-selected item in multi-select mode

    @available(iOS 6.0, *)
    optional func collectionView(_ collectionView: UICollectionView, didSelectItemAt indexPath: IndexPath)

    @available(iOS 6.0, *)
    optional func collectionView(_ collectionView: UICollectionView, didDeselectItemAt indexPath: IndexPath)

    
    @available(iOS 8.0, *)
    optional func collectionView(_ collectionView: UICollectionView, willDisplay cell: UICollectionViewCell, forItemAt indexPath: IndexPath)

    @available(iOS 8.0, *)
    optional func collectionView(_ collectionView: UICollectionView, willDisplaySupplementaryView view: UICollectionReusableView, forElementKind elementKind: String, at indexPath: IndexPath)

    @available(iOS 6.0, *)
    optional func collectionView(_ collectionView: UICollectionView, didEndDisplaying cell: UICollectionViewCell, forItemAt indexPath: IndexPath)

    @available(iOS 6.0, *)
    optional func collectionView(_ collectionView: UICollectionView, didEndDisplayingSupplementaryView view: UICollectionReusableView, forElementOfKind elementKind: String, at indexPath: IndexPath)

    
    // These methods provide support for copy/paste actions on cells.
    // All three should be implemented if any are.
    @available(iOS, introduced: 6.0, deprecated: 13.0)
    optional func collectionView(_ collectionView: UICollectionView, shouldShowMenuForItemAt indexPath: IndexPath) -> Bool

    @available(iOS, introduced: 6.0, deprecated: 13.0)
    optional func collectionView(_ collectionView: UICollectionView, canPerformAction action: Selector, forItemAt indexPath: IndexPath, withSender sender: Any?) -> Bool

    @available(iOS, introduced: 6.0, deprecated: 13.0)
    optional func collectionView(_ collectionView: UICollectionView, performAction action: Selector, forItemAt indexPath: IndexPath, withSender sender: Any?)

    
    // support for custom transition layout
    @available(iOS 7.0, *)
    optional func collectionView(_ collectionView: UICollectionView, transitionLayoutForOldLayout fromLayout: UICollectionViewLayout, newLayout toLayout: UICollectionViewLayout) -> UICollectionViewTransitionLayout

    
    // Focus
    @available(iOS 9.0, *)
    optional func collectionView(_ collectionView: UICollectionView, canFocusItemAt indexPath: IndexPath) -> Bool

    @available(iOS 9.0, *)
    optional func collectionView(_ collectionView: UICollectionView, shouldUpdateFocusIn context: UICollectionViewFocusUpdateContext) -> Bool

    @available(iOS 9.0, *)
    optional func collectionView(_ collectionView: UICollectionView, didUpdateFocusIn context: UICollectionViewFocusUpdateContext, with coordinator: UIFocusAnimationCoordinator)

    @available(iOS 9.0, *)
    optional func indexPathForPreferredFocusedView(in collectionView: UICollectionView) -> IndexPath?

    
    @available(iOS 9.0, *)
    optional func collectionView(_ collectionView: UICollectionView, targetIndexPathForMoveFromItemAt originalIndexPath: IndexPath, toProposedIndexPath proposedIndexPath: IndexPath) -> IndexPath

    
    @available(iOS 9.0, *)
    optional func collectionView(_ collectionView: UICollectionView, targetContentOffsetForProposedContentOffset proposedContentOffset: CGPoint) -> CGPoint // customize the content offset to be applied during transition or update animations

    
    // Spring Loading
    
    /* Allows opting-out of spring loading for an particular item.
     *
     * If you want the interaction effect on a different subview of the spring loaded cell, modify the context.targetView property.
     * The default is the cell.
     *
     * If this method is not implemented, the default is YES.
     */
    @available(iOS 11.0, *)
    optional func collectionView(_ collectionView: UICollectionView, shouldSpringLoadItemAt indexPath: IndexPath, with context: UISpringLoadedInteractionContext) -> Bool

    
    // Multiple Selection
    
    /* Allows a two-finger pan gesture to automatically enable allowsMultipleSelection and start selecting multiple cells.
     *
     * After a multi-select gesture is recognized, this method will be called before allowsMultipleSelection is automatically
     * set to YES to allow the user to select multiple contiguous items using a two-finger pan gesture across the constrained
     * scroll direction.
     *
     * If the collection view has no constrained scroll direction (i.e., the collection view scrolls both horizontally and vertically),
     * then this method will not be called and the multi-select gesture will be disabled.
     *
     * If this method is not implemented, the default is NO.
     */
    @available(iOS 13.0, *)
    optional func collectionView(_ collectionView: UICollectionView, shouldBeginMultipleSelectionInteractionAt indexPath: IndexPath) -> Bool

    
    /* Called right after allowsMultipleSelection is set to YES if -collectionView:shouldBeginMultipleSelectionInteractionAtIndexPath:
     * returned YES.
     *
     * In your app, this would be a good opportunity to update the state of your UI to reflect the fact that the user is now selecting
     * multiple items at once; such as updating buttons to say "Done" instead of "Select"/"Edit", for instance.
     */
    @available(iOS 13.0, *)
    optional func collectionView(_ collectionView: UICollectionView, didBeginMultipleSelectionInteractionAt indexPath: IndexPath)

    
    /* Called when the multi-select interaction ends.
     *
     * At this point, the collection view will remain in multi-select mode, but this delegate method is called to indicate that the
     * multiple selection gesture or hardware keyboard interaction has ended.
     */
    @available(iOS 13.0, *)
    optional func collectionViewDidEndMultipleSelectionInteraction(_ collectionView: UICollectionView)

    
    /**
     * @abstract Called when the interaction begins.
     *
     * @param collectionView  This UICollectionView.
     * @param indexPath       IndexPath of the item for which a configuration is being requested.
     * @param point           Location in the collection view's coordinate space
     *
     * @return A UIContextMenuConfiguration describing the menu to be presented. Return nil to prevent the interaction from beginning.
     *         Returning an empty configuration causes the interaction to begin then fail with a cancellation effect. You might use this
     *         to indicate to users that it's possible for a menu to be presented from this element, but that there are no actions to
     *         present at this particular time.
     */
    @available(iOS 13.0, *)
    optional func collectionView(_ collectionView: UICollectionView, contextMenuConfigurationForItemAt indexPath: IndexPath, point: CGPoint) -> UIContextMenuConfiguration?

    
    /**
     * @abstract Called when the interaction begins. Return a UITargetedPreview describing the desired highlight preview.
     *
     * @param collectionView  This UICollectionView.
     * @param configuration   The configuration of the menu about to be displayed by this interaction.
     */
    @available(iOS 13.0, *)
    optional func collectionView(_ collectionView: UICollectionView, previewForHighlightingContextMenuWithConfiguration configuration: UIContextMenuConfiguration) -> UITargetedPreview?

    
    /**
     * @abstract Called when the interaction is about to dismiss. Return a UITargetedPreview describing the desired dismissal target.
     * The interaction will animate the presented menu to the target. Use this to customize the dismissal animation.
     *
     * @param collectionView  This UICollectionView.
     * @param configuration   The configuration of the menu displayed by this interaction.
     */
    @available(iOS 13.0, *)
    optional func collectionView(_ collectionView: UICollectionView, previewForDismissingContextMenuWithConfiguration configuration: UIContextMenuConfiguration) -> UITargetedPreview?

    
    /**
     * @abstract Called when the interaction is about to "commit" in response to the user tapping the preview.
     *
     * @param collectionView  This UICollectionView.
     * @param configuration   Configuration of the currently displayed menu.
     * @param animator        Commit animator. Add animations to this object to run them alongside the commit transition.
     */
    @available(iOS 13.0, *)
    optional func collectionView(_ collectionView: UICollectionView, willPerformPreviewActionForMenuWith configuration: UIContextMenuConfiguration, animator: UIContextMenuInteractionCommitAnimating)
}
```













