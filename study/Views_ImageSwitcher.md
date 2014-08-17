###Views/ImageSwitcher###
####用于切换图片的控件配合gallery使用####

	* mSwitcher.setFactory(View.Switcher.ViewFactory);
	  回调方法public View makeView();返回用于显示图片的控件
	* 切换效果: mSwitcher.setInAnimation();
	          mSwitcher.setOutAnimation();