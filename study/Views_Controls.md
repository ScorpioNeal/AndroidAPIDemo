###Views/Controls###
####不同主题####

    * 设置主题android:theme="@android:style/Theme.Holo.Light" 
    * android:enabled="@bool/atLeastHoneycomb" 设置主题最低使用的版本
    * 使用相应版本的theme
     <!-- This is a theme that will adjust itself depending on the API version.
         The default definition is the safe one, using a theme that has always
         been defined.  Look at values-11/styles.xml for a variation that is
         selected when the holographic theme is available. -->
    <style name="ThemeHolo" parent="android:Theme">
    </style>
	* 使用自定义的theme
	<color name="custom_theme_color">#b0b0ff</color>
    <style name="CustomTheme" parent="android:Theme.Light">
        <item name="android:windowBackground">@color/custom_theme_color</item>
        <item name="android:colorBackground">@color/custom_theme_color</item>
    </style>
	* 使用parent可以使得直接使用parent里面的一些属性， 然后只要重写或者增加一些新的即可
