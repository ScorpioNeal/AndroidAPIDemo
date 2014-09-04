###App/LauncherShortcuts###

	* Android除了在launcher中生成指向应用主Activity的快捷方式外，还可以在HomeScreen定义指向Application中任意Activity的快捷方式（notice launcher和home screen的不同）
	* Activity中声明<action android:name="android.intent.action.CREATE_SHORTCUT" />
	    <activity
            android:name=".app.LauncherShortcuts"
            android:label="@string/shortcuts" >
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
				<action android:name="android.intent.action.CREATE_SHORTCUT" />
                <category android:name="android.intent.category.SAMPLE_CODE" />
                
            </intent-filter>
        </activity>

	* 不过建议是在activity-alias中声明，并指向activity
	    <activity-alias
            android:name=".app.LauncherShortcuts"
            android:label="@string/sample_shortcuts"
            android:targetActivity=".app.LauncherShortcuts" >

            <!-- This intent-filter allows your shortcuts to be created in the launcher. -->
            <intent-filter>
                <action android:name="android.intent.action.CREATE_SHORTCUT" />

                <category android:name="android.intent.category.DEFAULT" />
            </intent-filter>
        </activity-alias>
 	* 真正创建一个home screen的快捷方式
 	    private void setupShortcut() {
        	// First, set up the shortcut intent.  For this example, we simply create an intent that
        	// will bring us directly back to this activity.  A more typical implementation would use a 
        	// data Uri in order to display a more specific result, or a custom action in order to 
        	// launch a specific operation.

        	Intent shortcutIntent = new Intent(Intent.ACTION_MAIN);
        	shortcutIntent.setClassName(this, this.getClass().getName());
        	shortcutIntent.putExtra(EXTRA_KEY, "ApiDemos Provided This Shortcut");

        	// Then, set up the container intent (the response to the caller)

        	Intent intent = new Intent();
        	intent.putExtra(Intent.EXTRA_SHORTCUT_INTENT, shortcutIntent);
        	intent.putExtra(Intent.EXTRA_SHORTCUT_NAME, getString(R.string.shortcut_name));
        	Parcelable iconResource = Intent.ShortcutIconResource.fromContext(
                this,  R.drawable.app_sample_code);
        	intent.putExtra(Intent.EXTRA_SHORTCUT_ICON_RESOURCE, iconResource);

        	// Now, return the result to the launcher

       		setResult(RESULT_OK, intent);
    }
	* 然后点击快捷方式进入activity可以从getIntent()中获取shortcutIntent传来的参数
	* 注意： 在homescreen创建快捷方式的时候点击会进入目标Activity， 所以第一次进入需要
	    if (Intent.ACTION_CREATE_SHORTCUT.equals(action)) {
            setupShortcut();
            finish();
            return;
        }
		即初始化homescreen快捷方式后就要退出这个activity