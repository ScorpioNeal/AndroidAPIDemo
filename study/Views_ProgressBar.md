###Views/ProgressBar###

    * ProgressBar分为2种:
        一种是有进度的Progress
        一种是无进度的indeterminate progress
	* ProgressBar可以在title栏设置，也可以在contentview中设置
	* 标题栏中的有进度的progressbar
		requestWindowFeature(Window.FEATURE_PROGRESS); 
		进度范围是0-10000 
    * title栏中的无进度progressbar
        requestWindowFeature(Window.FEATURE_INDETERMINATE_PROGRESS);
    	可以通过方法setProgressBarIndeterminateVisibility(boolean)来设置是否显示
	* 普通的progress更改:
	    更改一级进度progress.incrementProgressBy(进度增幅，可正可负)
	    更改二级进度progress.incrementSecondaryProgressBy(进度增幅，可正可负)
	  标题栏中的progress进度更改:
	    更改一级进度setProgress(具体进度) 
	    更改二级进度setSecondaryProgress(具体进度)
	* 有进度的progress 
        在xml中设置style="?android:attr/progressBarStyleHorizontal"
	  无尽度的progress 
        在xml中设置style="?android:attr/progressBarStyleLarge" 大的圈
	  	默认不设置是中等的圈
	  	style="?android:attr/progressBarStyleSmall" 小的圈
	  	style="?android:attr/progressBarStyleSmallTitle" 也是小的圈，不知道跟上一个有什么区别
	* Dialog中的progress -> ProgressDialog
	    e.g
			ProgressDialog dialog = new ProgressDialog(this);
            dialog.setTitle("Indeterminate");
            dialog.setMessage("Please wait while loading...");
            dialog.setIndeterminate(true);
            dialog.setCancelable(true);
   