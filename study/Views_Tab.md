###Views/Tab###

	* 使用TabActivity
	* 获取TabHost 直接getTabHost();
	* 显示LayoutInflater.from(this).inflate(R.layout.tabs1, tabHost.getTabContentView(), true);
	* 添加子Tab
		tabHost.addTab(TabSpec);
		
		tabHost.addTab(tabHost.newTabSpec("tab1")
                .setIndicator("tab1")
                .setContent(R.id.view1));//这些view在R.layout.tabs1里面定义的
		第一个是tag,用来区分不同tab
		第二个是显示的内容
		第三个是view 显示的样式

		其中setContent()可以不直接使用View ID 而是
		setContent(TabContentFactory contentFactory)
		这里面返回一个view即可

		其中setContent()里面还可以使用intent， 来显示另一个activity的内容setContent(new Intent(this, List8.class))

		其中setIndicator()里面还可以制定图标
		setIndicator("tab1", getResources().getDrawable(R.drawable.star_big_on) 但是有的主题可能不会显示这个图标
	* 在xml中设置tab
	<TabHost xmlns:android="http://schemas.android.com/apk/res/android"
    	android:id="@android:id/tabhost"//固定的
    	android:layout_width="match_parent"
    	android:layout_height="match_parent">
    	<LinearLayout
        	android:orientation="vertical"
        	android:layout_width="match_parent"
        	android:layout_height="match_parent"
        	android:padding="5dp">
        	<HorizontalScrollView
            	android:layout_width="match_parent"
            	android:layout_height="wrap_content"
            	android:scrollbars="none">
            	<TabWidget//用来显示子tab的控件
               		android:id="@android:id/tabs"//固定的
                	android:layout_width="match_parent"
                	android:layout_height="wrap_content" />
        	</HorizontalScrollView>
        <FrameLayout//用来显示tab对应的界面的布局
            android:id="@android:id/tabcontent"//固定的
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:padding="5dp" />
    	</LinearLayout>
	</TabHost>