---
categories: iOS
---
<link rel="stylesheet" href="http://yastatic.net/highlightjs/8.2/styles/xcode.min.css">
<script src="http://yastatic.net/highlightjs/8.2/highlight.min.js"></script>
<script>hljs.initHighlightingOnLoad();</script>

##如何在Mou中让代码高亮
![image](http://ww4.sinaimg.cn/large/74311666jw1ewtmyxc4i0j20nu0dg75h.jpg)

#### 说明
In the custom subclass from the last exercise, you added the UILabel subview to self.contentView and not self. In general, you should not add subviews directly to a collection view cell; always add them to its contentView. Here's why.
UICollectionViewCell has three subviews, denoted in Figure 2.10. The black rectangle, at the back, is the collection view cell itself. The green view at the front is the contentView, and it’s there that you add your subviews. The two intervening views are the selectedBackgroundView and the backgroundView. These are both optional and can be set at any time. The backgroundView, if set, is permanently present.
When the cell becomes selected, the selectedBackgroundView is added to the view hierarchy; when the cell becomes unselected, it is removed. Note that these two events can be called from within animation blocks and the selectedBackgroundView is animated in (with a crossfade by default).


代码如何加亮？？

	- (id)initWithFrame:(CGRect)frame{
    	if (!(self = [super initWithFrame:frame])) return nil;
    
    	self.backgroundColor = [UIColor whiteColor];
    
    	imageView = [[UIImageView alloc] initWithFrame:CGRectInset(self.bounds, 10, 10)];
    	[self.contentView addSubview:imageView];
    
    	UIView *selectedBackgroundView = [[UIView alloc] initWithFrame:CGRectZero];
    	selectedBackgroundView.backgroundColor = [UIColor colorWithWhite:1.0f alpha:0.8f];
    	self.selectedBackgroundView = selectedBackgroundView;
    
    	return self;
	}

