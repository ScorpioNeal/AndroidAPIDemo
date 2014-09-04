###Preference###

	* 新建一个类继承自PreferenceActivity， 重写onCreate方法
	* 在onCreate中加载xml addPreferencesFromResource(R.xml.preference);
	* 详解/xml/preference.xml
		* 父布局PreferenceScreen
		* 每一个分类用PreferenceCategory来分割， 可以设置title android:title=""
		* CheckBoxPreference 带checkbox的preference
			* android:key="key" 存储标识key
			* android:summary="summary ,用来简介功能的"
			* android:title="title" 标题
			* android:dependency="pre_key" 设置这个表示他会根据pre_key的状态来改变本身的状态， 即假设一个checkboxpreference 的 key 是 pre_key , 如果他选中了， 那么设置android:dependency="pre_key"的preference才可以用， 否则为默认不可选状态
			* android:defaultValue="true" 设置默认为选中
			* android:summaryOff="" //check关闭时显示的文本
        	* android:summaryOn="" //check打开时显示的文本
		* EditTextPreference 点击会弹出一个EditText用来输入
			* android:key
			* android:summary
			* android:title
			* android:dialogTitle 弹出的dialog（包含edittext）的标题
			* android:defaultValue 默认显示在edittext的值
		* ListPreference 点击会弹出一个list
			* android:key
			* android:title
			* android:summary 
			* android:dialogTitle
			* android:entries="@array/***" 展示的内容
			* android:entryValues="@array/***"真正存储的值
			* android:defaultValue="entryvalues里面对应的某个值" 设置默认 
		* SwitchPreference 带switch btn的
			* android:key
			* android:title
			* android:summary
			* android:defaultValue="true"
			* android:switchTextOn = "YES"
            * android:switchTextOff = "NO"
		* Preference的嵌套， 即点击会进入另外一个preference 或者打开一个intent
   			<PreferenceCategory android:title="@string/launch_preferences" >
        		<PreferenceScreen
            		android:key="screen_preference"
            		android:summary="@string/summary_screen_preference"
            		android:title="@string/title_screen_preference" >
            			<CheckBoxPreference
                			android:key="next_screen_checkbox_preference"
                			android:summary="@string/summary_next_screen_toggle_preference"
                			android:title="@string/title_next_screen_toggle_preference" />
        		</PreferenceScreen>
        		<PreferenceScreen
            		android:summary="@string/summary_intent_preference"
            		android:title="@string/title_intent_preference" >
            			<intent
                			android:action="android.intent.action.VIEW"
                			android:data="http://www.android.com" />
        		</PreferenceScreen>
   	 	  </PreferenceCategory>
	* PreferenceManager.setDefaultValues() 把preference xml中的默认值保存到preference里面
	* 代码设置Preference
	  PreferenceScreen root = getPreferenceManager().createPreferenceScreen(context);
	  其余直接new就行了，然后按照嵌套关系add
	* preference监听
		* 注册 getPreferenceScreen().getSharedPreference().registerOnSharedPreferenceChangeListener(OnSharedPreferenceChangeListener);
		* 解除 getPreferenceScreen().getSharedPreferences().unregisterOnSharedPreferenceChangeListener(OnSharedPreferenceChangeListener);
		* 重写 public void onSharedPreferenceChanged(SharedPreferences sharedPreferences, String key) {} 然后针对不同的key执行不同的操作