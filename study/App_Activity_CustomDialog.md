###App/Activity/Custom Dialog###
####自定义Dialog主题####
`如何显示一个自定义主题的Dialog`

AndroidManifest中 添加android:theme="@style/Theme.CustomDialog"
 
 然后在styles.xml里面添加一个自定义的style

```xml
	<style name="Theme.CustomDialog" parent="android:style/Theme.Dialog">
        <item name="android:windowBackground">@drawable/filled_box</item>
   	</style>
```
