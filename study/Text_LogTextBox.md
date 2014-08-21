###Text/LogTextBox###
####自定义一个继承自TextView的控件 让他在超过长度时候可滑动####
	
	 *    重写
    protected MovementMethod getDefaultMovementMethod() {
        return ScrollingMovementMethod.getInstance();
    }
