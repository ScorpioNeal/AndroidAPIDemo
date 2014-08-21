###Views/LayoutAnimation###

	* GridView在加载grid时候的动画添加
	  	* 在GridView xml中添加 android:layoutAnimation="@anim/layout_grid_fade"
	  	* 在/anim/添加layout_grid_fade.xml
	  	<gridLayoutAnimation 
		xmlns:android="http://schemas.android.com/apk/res/
        android:rowDelay="50%"
        android:directionPriority="column"
        android:animation="@anim/fade" />
		* 在/anim/中添加fade.xml
		<alpha xmlns:android="http://schemas.android.com/apk/res/android"
       	android:interpolator="@android:anim/accelerate_interpolator"
       	android:fromAlpha="0.0" 
		android:toAlpha="1.0"
       	android:duration="@android:integer/config_longAnimTime" />

		//gridLayoutAnimation 是固定的么？ 不太清楚

	* ListView在代码中添加动画 
	  listView.setLayoutAnimation(controller);
	  LayoutAnimationController controller = new LayoutAnimationController(
                set, 0.5f);
	  //第一个参数是Animation，可以是具体某个Animation， 也可以是AnimationSet, 他俩都是继承自Animation的
		* AlphaAnimation 
	  		Animation animation = new AlphaAnimation(0.0f, 1.0f);
	  		只要制定fromAlpha和toAlpha即可
		* TranslateAnimation
	 		 animation = new TranslateAnimation(Animation.RELATIVE_TO_SELF, 0.0f,
                Animation.RELATIVE_TO_SELF, 0.0f, Animation.RELATIVE_TO_SELF,
                -1.0f, Animation.RELATIVE_TO_SELF, 0.0f);

	  fromXType  
		Specifies how fromXValue should be interpreted. One of Animation.ABSOLUTE, Animation.RELATIVE_TO_SELF, or Animation.RELATIVE_TO_PARENT. 
	  fromXValue
	    Change in X coordinate to apply at the start of the animation. This value can either be an absolute number if fromXType is ABSOLUTE, or a percentage (where 1.0 is 100%) otherwise. 
	  toXType  
		Specifies how toXValue should be interpreted. One of Animation.ABSOLUTE, Animation.RELATIVE_TO_SELF, or Animation.RELATIVE_TO_PARENT. 
	  toXValue  
		Change in X coordinate to apply at the end of the animation. This value can either be an absolute number if toXType is ABSOLUTE, or a percentage (where 1.0 is 100%) otherwise. 	 
	  fromYType  
		Specifies how fromYValue should be interpreted. One of Animation.ABSOLUTE, Animation.RELATIVE_TO_SELF, or Animation.RELATIVE_TO_PARENT. 
	  fromYValue  
		Change in Y coordinate to apply at the start of the animation. This value can either be an absolute number if fromYType is ABSOLUTE, or a percentage (where 1.0 is 100%) otherwise. 
	  toYType  
		Specifies how toYValue should be interpreted. One of Animation.ABSOLUTE, Animation.RELATIVE_TO_SELF, or Animation.RELATIVE_TO_PARENT. 
	  toYValue  
		Change in Y coordinate to apply at the end of the animation. This value can either be an absolute number if toYType is ABSOLUTE, or a percentage (where 1.0 is 100%) otherwise.  

	* xml中加载animation
	  	* listview xml中android:layoutAnimation="@anim/layout_bottom_to_top_slide" 
	  	* /anim/layoutZ_bottom_to_top_slide
	  	  <layoutAnimation xmlns:android="http://schemas.android.com/apk/res/android"
        	android:delay="30%"
        	android:animationOrder="reverse"//反转
        	android:animation="@anim/slide_right" />
 	  		//TODO layoutAnimation 是固定的？
		* /anim/slide_right
		  <set xmlns:android="http://schemas.android.com/apk/res/android" 	android:interpolator="@android:anim/accelerate_interpolator">
    			<translate android:fromXDelta="-100%p" android:toXDelta="0"
            android:duration="@android:integer/config_shortAnimTime" />
		  </set>//主要指定了translate属性与代码中一样
	* 随机加载动画
	
	<layoutAnimation xmlns:android="http://schemas.android.com/apk/res/android"
        android:delay="0.5"
        android:animationOrder="random"//This attributes define the order animation
        android:animation="@anim/fade" />
	* GridLayout Animation
		<gridLayoutAnimation 
		xmlns:android="http://schemas.android.com/apk/res/android"
        android:columnDelay="0.5"
        android:directionPriority="row"//!! This attr is important 貌似指定了按行加载而不是一次加载全 不太清楚
        android:direction="right_to_left|bottom_to_top"//load direction
        android:animation="@anim/fade" />

	* android:rowDelay="75%"//TODO 把这几个属性搞懂
      android:columnDelay="0%"
      android:directionPriority="none"