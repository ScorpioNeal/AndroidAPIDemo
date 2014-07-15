###Text/Linkify###
####带有链接的textview####
	* 方法1
	  直接在xml中设置为android:autoLink="all" 然后文本中的数字， 或者邮箱， 或者电话会自动进行转换
	* 方法2
	  如果不用android:autoLink="all" 那么系统只会自动转换带有tag <a>的标签
	  e.g <a href="tel:4155551212">dial a phone number</a>
	      <a href="http://www.google.com">link</a>
	* 方法3
	  通过Html构造
	  e.g t3.setText(Html.fromHtml(htmlSource);
	* 方法4
	  通过SpannableString 构造自定义的链接
	  
<b>注意</b>：<p>需要设置<p>
```
	textview.setMovementMethod(LinkMovementMethod.getInstance());
``` 
<p>这样才能使得点击链接产生效果
