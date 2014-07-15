###App/Menu/InflateFromXML###
####各种菜单####

1. 普通菜单

```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android" >

    <item
        android:id="@+id/jump"
        android:title="@string/jump"/>
    <item
        android:id="@+id/dive"
        android:title="@string/dive"/>

</menu>
```

2. 带有图片的菜单
在1的基础上 item中加`android:icon="@drawable/stat_happy"`<br>
*但是貌似没有起作用？？*

3. 子菜单

```xml
<menu xmlns:android="http://schemas.android.com/apk/res/android" >

    <item android:title="Normal 1"/>
    <item
        android:id="@+id/submenu"
        android:title="Emotions">
        <menu>
            <item
                android:id="@+id/happy"
                android:icon="@drawable/stat_happy"
                android:title="Happy"/>
            <item
                android:id="@+id/neutral"
                android:icon="@drawable/stat_neutral"
                android:title="Neutral"/>
            <item
                android:id="@+id/sad"
                android:icon="@drawable/stat_sad"
                android:title="Sad"/>
        </menu>
    </item>
    <item android:title="Normal 2"/>

</menu>
```
在item里嵌套一个<menu> 奇怪的是子菜单里面的android:icon可以生效！！

4. 分组菜单

```xml
    <menu xmlns:android="http://schemas.android.com/apk/res/android" >

    <item
        android:id="@+id/browser_visibility"
        android:title="@string/browser_visibility"/>

    <group android:id="@+id/browser" >
        <item
            android:id="@+id/refresh"
            android:title="@string/browser_refresh"/>
        <item
            android:id="@+id/bookmark"
            android:title="@string/browser_bookmark"/>
    </group>

    <item
        android:id="@+id/email_visibility"
        android:title="@string/email_visibility"/>

    <group android:id="@+id/email" >
        <item
            android:id="@+id/reply"
            android:title="@string/email_reply"/>
        <item
            android:id="@+id/forward"
            android:title="@string/email_forward"/>
    </group>

</menu>
```
`通过mMenu.setGroupVisible(R.id.browser, shouldShowBrowser);`设置分组的隐藏或显示
    * <br>第一个参数是group id
    * <br>第二个参数是显示或者隐藏
    
5. 可选择的菜单， check or radio风格

`通过在<group>中设置android:checkableBehavior=""参数设置`
<br> 默认是android:checkableBehavior="none"
<br> android:checkableBehavior="single" 表示风格是radio 可以在单个item中设置android:checked="true"
<br> android:checkableBehavior="all" 表示风格是checkbox 可以在每个item中设置android:checked="true"
<br> 
<br> 不在<group>中设置checkableBehavior属性也可以在每个item中设置

```xml
     <item
                android:id="@+id/nongroup_checkable_item_2"
                android:checkable="true"
                android:checked="true"
                android:title="@string/item_2"/>
```

6. 菜单项快捷键

```xml
    <item android:id="@+id/b_item"
        android:alphabeticShortcut="b"
        android:title="Bart" />
```
设置快捷键， 为测试， 暂不知道怎么使用

7. 菜单项排序

```xml
    <item android:id="@+id/first_item"
        android:orderInCategory="0"
        android:title="First" />
```

`通过android:orderInCategory排序， 与xml中的顺序无关了`

8. 菜单group 排序

```xml
   <group android:id="@+id/least_used_items"
        android:menuCategory="secondary">
```
带有android:menuCategory="secondary"表示这个菜单组使用在其他菜单组的后面， 这时候该组内的orderInCategory不在于其他组内进行比较， 只会在本组内排序

9. 菜单还支持android:visible="false" 参数 和enable参数