###App/Activity/TranslucentActivity###
####Activity背景半透明####


在AndroidManifest.xml中添加一个Theme
    <style name="Theme.Translucent" parent="android:style/Theme.Translucent">
        <item name="android:windowBackground">@drawable/translucent_background</item>
        <item name="android:windowNoTitle">true</item>
        <item name="android:colorForeground">#fff</item>
    </style>

    其中translucent_background：
    <drawable name="translucent_background">#e0000000</drawable>