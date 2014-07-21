###Views/TextSwitcher1###
`TextSwitcher控件在设置setText时，文本的切入与切出具有动画效果`
`是包含一个textview的viewswitcher`

使用时： `implements ViewSwitcher.ViewFactory`<br>
重写方法(该方法返回用于显示的View)

```java
        public View makeView() {
        TextView t = new TextView(this);
        t.setGravity(Gravity.TOP | Gravity.CENTER_HORIZONTAL);
        t.setTextSize(36);
        return t;
    }
```

调用方法
```java
        mSwitcher.setFactory(this);
        //设置动画效果
        Animation in = AnimationUtils.loadAnimation(this,
                android.R.anim.fade_in);
        Animation out = AnimationUtils.loadAnimation(this,
                android.R.anim.fade_out);
        mSwitcher.setInAnimation(in);
        mSwitcher.setOutAnimation(out);
```        