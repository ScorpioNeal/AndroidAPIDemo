###App/Notification###

	* 构造NotificationManager
	  NotificationManager nm = (NotificationManager) getSystemService(NOTIFICATION_SERVICE);
	* 构造PendingIntent
		*  PendingIntent contentIntent = PendingIntent.getActivities(this, 0,
                makeMessageIntentStack(this, from, message),
                PendingIntent.FLAG_CANCEL_CURRENT);
		* PendingIntent contentIntent = PendingIntent.getActivity(this, 0,
                intent, PendingIntent.FLAG_CANCEL_CURRENT);
		//其中第三个参数可以为一个intent，也可以是一个intent的数组, 数组表明点击进去后进入的是一个activity栈， 按返回键会按照栈的顺序显示

		static Intent[] makeMessageIntentStack(Context context, CharSequence from,
            CharSequence msg) {
       
        Intent[] intents = new Intent[4];

        // First: root activity of ApiDemos.
        // This is a convenient way to make the proper Intent to launch and
        // reset an application's task.
		//第一个intent, root
        intents[0] = Intent.makeRestartActivityTask(new ComponentName(context,
                com.example.android.apis.ApiDemos.class));
		//第二个
        // "App"
        intents[1] = new Intent(context,
                com.example.android.apis.ApiDemos.class);
        intents[1].putExtra("com.example.android.apis.Path", "App");
        // "App/Notification"
		//第三个
        intents[2] = new Intent(context,
                com.example.android.apis.ApiDemos.class);
        intents[2]
                .putExtra("com.example.android.apis.Path", "App/Notification");
		//第四个， 最先显示
        // Now the activity to display to the user. Also fill in the data it
        // should display.
        intents[3] = new Intent(context, IncomingMessageView.class);
        intents[3].putExtra(IncomingMessageView.KEY_FROM, from);
        intents[3].putExtra(IncomingMessageView.KEY_MESSAGE, msg);

        return intents;
    }

	* 构造Notification
	  Notification notif = new Notification(R.drawable.stat_sample,
                tickerText, System.currentTimeMillis());
	  notif.setLatestEventInfo(Context, contentTitle, contentText, pendingIntent);
	  notif.defaults = Notification.DEFAULT_ALL;
	* 展示nm.notify(ID, notif);

		//FLAG_AUTO_CANCEL   该通知能被状态栏的清除按钮给清除掉
        //FLAG_INSISTENT     是否一直进行，比如音乐一直播放，知道用户响应
        notification.flags |= Notification.FLAG_ONGOING_EVENT; // 将此通知放到通知栏的"Ongoing"即"正在运行"组中   
        notification.flags |= Notification.FLAG_NO_CLEAR; // 表明在点击了通知栏中的"清除通知"后，此通知不清除，经常与FLAG_ONGOING_EVENT一起使用   
        notification.flags |= Notification.FLAG_SHOW_LIGHTS;   
        //DEFAULT_ALL     使用所有默认值，比如声音，震动，闪屏等等
        //DEFAULT_LIGHTS  使用默认闪光提示
        //DEFAULT_SOUNDS  使用默认提示声音
        //DEFAULT_VIBRATE 使用默认手机震动，需加上<uses-permission android:name="android.permission.VIBRATE" />权限
        notification.defaults = Notification.DEFAULT_LIGHTS; 
	* 取消notification
        NotificationManager nm = (NotificationManager) getSystemService(NOTIFICATION_SERVICE);
        nm.cancel(ID);

