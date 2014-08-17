###Views/ScrollBars###

    * android:scrollbarTrackVertical="@drawable/" 垂直滚动条轨迹的drawable
    * android:scrollbarThumbVertical="@drawable/" 垂直滚动条的drawable
    * android:scrollbarSize=""滚动条宽度
    * [android:scrollbarStyle=""](https://www.evernote.com/shard/s118/sh/2a769fe1-99db-4618-9638-c493dc4ed070/80a12fc065dd19e29bb6dbce622cea3b)

	* outsideInset & outsideOverlay 
	  bar显示在view的边缘，但是outsideInset计算padding时候是bar的左边到view的右边的距离算作padding的值
	  outsideOverlay计算padding的时候不算bar,相当于bar是浮在上面的，so called overlay
	* insideInset & insideOverlay
	  bar显示在view正文里， 但是insideInset在padding的时候只会右边增加padding， bar还是紧靠正文， insideOverlay则可能和正文区域重叠， so called overlay
	  
    * 默认是insideOverlay?
    * 不仅可以在xml中设置， 还可以这样设置
      setScrollBarStyle(View.SCROLLBARS_INSIDE_INSET);