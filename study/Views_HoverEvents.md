###Views/HoverEvents###
####监听悬停状态####

	* view.setOnHoverListener(View.OnHoverListener);
		* 重写public boolean onHover(View v, MotionEvent event)方法
		* MotionEvent.ACTION_HOVER_ENTER 进入时触发
		* MotionEvent.ACTION_HOVER_MOVE 在里面移动时触发
		* MotionEvent.ACTION_HOVER_EXIT 退出时触发
	* 拦截子view的悬浮监听事件
		* 重写public boolean onInterceptHoverEvent(MotionEvent event);
		  return true;那么子view就不会接受到了
		* 自己处理悬浮事件, 重写public boolean onHoverEvent(MotionEvent event);