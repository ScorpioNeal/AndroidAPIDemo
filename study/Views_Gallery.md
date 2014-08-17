###Views/Gallery###

	* Gallery.setAdapter()//设置显示内容，与list一样用法
	* registerForContextMenu(View);//view长按会弹出一个contextmenu
	  其中contextmenu样式在onCreateContextMenu中设置
	     contextmenu操作在onContextItemSelecte回调中设置
    *//TODO ContextMenuInfo    
    @Override
    public boolean onContextItemSelected(MenuItem item) {
        AdapterContextMenuInfo info = (AdapterContextMenuInfo) item.getMenuInfo();
        //这样可以获取adapter的信息
        Toast.makeText(this, "Longpress: " + info.position, Toast.LENGTH_SHORT).show();
        return true;
    }
    
    AdapterContextMenuInfo : 当显示 AdapterView 的上下文菜单时，为 onCreateContextMenu(ContextMenu, View, ContextMenuInfo) 回调函数提供的额外的菜单信息。
    
    public long id 用于显示上下文菜单的子视图的行 ID。
 	public int position 用于显示上下文菜单的子视图在适配器中的位置。
    public View targetView 用于显示上下文菜单的子视图。也是 AdapterView 的子视图之一。

