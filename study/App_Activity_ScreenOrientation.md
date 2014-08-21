###App/Activity/ScreenOrientation###
####屏幕方向####

 	   ActivityInfo.SCREEN_ORIENTATION_UNSPECIFIED,//未指定，此为默认值。由Android系统自己选择合适的方向。
       ActivityInfo.SCREEN_ORIENTATION_LANDSCAPE,//横屏
       ActivityInfo.SCREEN_ORIENTATION_PORTRAIT,//竖屏
       ActivityInfo.SCREEN_ORIENTATION_USER,//用户当前的首选方向
       ActivityInfo.SCREEN_ORIENTATION_BEHIND,//继承Activity堆栈中当前Activity下面的那个Activity的方向
       ActivityInfo.SCREEN_ORIENTATION_SENSOR,//由物理感应器决定显示方向
       ActivityInfo.SCREEN_ORIENTATION_NOSENSOR,//忽略物理感应器——即显示方向与物理感应器无关
       ActivityInfo.SCREEN_ORIENTATION_SENSOR_LANDSCAPE,
       ActivityInfo.SCREEN_ORIENTATION_SENSOR_PORTRAIT,
       ActivityInfo.SCREEN_ORIENTATION_REVERSE_LANDSCAPE,
       ActivityInfo.SCREEN_ORIENTATION_REVERSE_PORTRAIT,
       ActivityInfo.SCREEN_ORIENTATION_FULL_SENSOR,

	  设置setRequestedOrientation（int orientation）