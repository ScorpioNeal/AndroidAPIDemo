###OS/MorseCode###
####通过震动展示莫尔斯密码####

	* 震动
		* 获取系统震动 Vibrator vibrator = (Vibrator)getSystemService(Context.VIBRATOR_SERVICE);
        * 震动 vibrator.vibrate(pattern, -1);
          //其中pattern是一个long数组， 第二个参数表示重复次数， -1表示不重复
		* 只有1个参数的时候，第一个参数用来指定振动的毫秒数。
		  要传递2个参数的时候，第1个参数用来指定振动时间的样本，第2个参数用来指定是否需要循环。 
		  振动时间的样本是指振动时间和等待时间的交互指定的数组。
		  e.g 下面的例子，在程序起动后等待3秒后，振动1秒，再等待2秒后，振动5秒，再等待3秒后，振动1秒
          long[] pattern = {3000, 1000, 2000, 5000, 3000, 1000}; // OFF/ON/OFF/ON…
	* 其中MorseCodeConverter转换类可以直接复用,即把数字，字母等转换为莫尔斯密码

