###Views/ImageView###

	* 图片按原始尺寸显示
	  android:adjustViewBounds="true"
      android:layout_width="wrap_content"
      android:layout_height="wrap_content"
	* 设置最大宽度高度
	  设置View的最大高度，单独使用无效，需要与setAdjustViewBounds一起使用。如果想设置图片固定大小，又想保持图片宽高比，需要如下设置：
	1） 设置setAdjustViewBounds为true；
	2） 设置maxWidth、MaxHeight；
	3） 设置设置layout_width和layout_height为wrap_content。
	* 设置padding  android:padding
	  前景： android:src 背景: android:background
[android:scaleType属性](https://www.evernote.com/shard/s118/nl/12819723/9c5fa178-9f69-414f-9a00-9bf5e195ca66)
      
	  