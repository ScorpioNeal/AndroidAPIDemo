###Views/Layouts###

    * android:layout_alignBaseLine: 表示该widget的BaseLine必须参数值标识的widget的BaseLine重合。这个主要用于Label或者其他包含文本的widgets。
    * android:baselineAlignedChildIndex="int" 指定第几个子控件作为baseline 从0开始计数
      但是貌似指定了android:layout_gravity="center_vertical"的时候貌似不起作用了！！！
	*  android:baselineAlignedChildIndex可以嵌套指定， 即最终设为baseline的是嵌套里面最后的子控件
		<view1 baseline=1
			<view2 baseline=2>>
		即最后设为baseline的是view2的第3个控件
    * TableLayout
      主要是使用TableRow来作为每行的分割， 其实用LinearLayout也行