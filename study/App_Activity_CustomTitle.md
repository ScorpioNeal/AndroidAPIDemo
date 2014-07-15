###App/Activity/Custom Title###
####自定义标题栏文本####
`如何自定义标题栏文本`

```java
	    requestWindowFeature(Window.FEATURE_CUSTOM_TITLE);
        setContentView(R.layout.custom_title);
        getWindow().setFeatureInt(Window.FEATURE_CUSTOM_TITLE, R.layout.custom_title_1);
``` 

其中R.layout.custom_title_1是自定义的标题栏布局

AndroidManifest文件中指出`This sample doesn't work with the new action bar, so use the old style theme.` 
所以在新的，带有actionbar的主题这个自定义标题栏不再适用