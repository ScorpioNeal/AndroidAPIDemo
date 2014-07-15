###App/Activity/Dialog###
####Dialog####
`如何显示一个形如Dialog的Activity`

AndroidManifest中 添加android:theme="@android:style/Theme.Holo.Dialog"

设置dialog的标题栏和左边icon
```java
	 	requestWindowFeature(Window.FEATURE_LEFT_ICON);
		//这个要放在setContentView前面

        setContentView(R.layout.dialog_activity);
        getWindow().setTitle("This is just a test");

        getWindow().setFeatureDrawableResource(Window.FEATURE_LEFT_ICON,
                android.R.drawable.ic_dialog_alert);
```
	
