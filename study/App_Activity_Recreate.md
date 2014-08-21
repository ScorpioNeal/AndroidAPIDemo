###App/Activity/ActivityRecreate###
####Activity重建####

	* recreate(); 这就是让他重建的方法--
	* 在onSaveInstanceState里面保存当前theme
	  savedInstanceState.putInt("theme", mCurTheme);
	* 在onCreate里面取出来
	  if (savedInstanceState != null) {
            mCurTheme = savedInstanceState.getInt("theme");
	  }
	  然后设置theme  setTheme();