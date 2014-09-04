###App/SoftInputModes###
####软键盘弹起的不同方式####

	* 代码中配置 getWindow().setSoftInputMode(SOFT_INPUT_***)；
		  SOFT_INPUT_ADJUST_NOTHING: 不调整(输入法完全直接覆盖住,未开放此参数)
		  SOFT_INPUT_ADJUST_PAN:  把整个Layout顶上去露出获得焦点的EditText,不压缩多余空间
		  SOFT_INPUT_ADJUST_RESIZE:  整个Layout重新编排,重新分配多余空间
		  SOFT_INPUT_ADJUST_UNSPECIFIED:  系统自己根据内容自行选择上两种方式的一种执行(默认配置)
	* 或者在AndroidManifest中配置
	  android:windowSoftInputMode=""