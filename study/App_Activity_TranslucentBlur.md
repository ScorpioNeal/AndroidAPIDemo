###App/Activity/TranslucentBlur###
####Activity背景全透明####


在AndroidManifest.xml中添加一个Theme
    <style name="Theme.Transparent">
        <item name="android:windowIsTranslucent">true</item>
        <item name="android:windowAnimationStyle">@android:style/Animation.Translucent</item>
        <item name="android:windowBackground">@drawable/transparent_background</item>
        <item name="android:windowNoTitle">true</item>
        <item name="android:colorForeground">#fff</item>
    </style>

    其中： <drawable name="transparent_background">#00000000</drawable>
    