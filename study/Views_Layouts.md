###Views/Layouts###

	* LinearLayout
    * android:layout_alignBaseLine: 表示该widget的BaseLine必须参数值标识的widget的BaseLine重合。这个主要用于Label或者其他包含文本的widgets。
    * android:baselineAlignedChildIndex="int" 指定第几个子控件作为baseline 从0开始计数
      但是貌似指定了android:layout_gravity="center_vertical"的时候貌似不起作用了！！！
	*  android:baselineAlignedChildIndex可以嵌套指定， 即最终设为baseline的是嵌套里面最后的子控件
		<view1 baseline=1
			<view2 baseline=2>>
		即最后设为baseline的是view2的第3个控件
	* android:addStatesFromChildren="true"
	 设置整个viewGroup的drawable状态是否也包含子空间的drawable状态。该属性用于当子控件editext或者button获得焦点时作为一个组出现使用(翻译的不好，水平有限，理解就好)，这样一来，将android:addStatesFromChildren设为true，当组中的EditText或是Button获取焦点时，将Layout的Background设置成相应EditText或的Button的Drawable ，这样看上去该linear中的view是一个整体。(Sample/Views/Layouts/LinearLayout/10 案例很好)
	* android:background="@android:drawable/edit_text"背景设置为editext的样子
	* LinearLayout可以动态设置setOrientation 和 gravity
	  mLinearLayout.setOrientation(LinearLayout.VERTICAL);
	  mLinearLayout.setVerticalGravity(Gravity.TOP);
	  mLinearLayout.setHorizontalGravity(Gravity.LEFT);	


    * TableLayout
      主要是使用TableRow来作为每行的分割， 其实用LinearLayout也行
	  [TableLayout属性详解](https://www.evernote.com/shard/s118/sh/8b9dc93c-7a0e-42a3-a2d6-487a51e0156c/2faf8d0681282c2bcfe6faac4195d111)

	* GridLayout
	  android:columnCount="4" 设置列数
	  android:layout_columnSpan 表示该组件在列数上占了几列
	  
	  若要指定某控件显示在固定的行或列，只需设置该子控件的android:layout_row和android:layout_column属性即可，但是需要注意：android:layout_row=”0”表示从第一行开始，android:layout_column=”0”表示从第一列开始

	  代码设置GridLayout 
	  * 构造GridLayout
	    GridLayout p = new GridLayout(context);
        p.setUseDefaultMargins(true);
        p.setAlignmentMode(ALIGN_BOUNDS);
        p.setRowOrderPreserved(false);
	  * 构造Spec Spec(start, size, align)
	  * 添加进去
	    p.addView(view, new LayoutParams(rowSpec, colSpec));