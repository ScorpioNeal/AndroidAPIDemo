###Views/Popup Menu###

	* popup menu创建需要有个锚点来定位
	  PopupMenu popup  = new PopupMenu(context, anchor view);
	* 绑定菜单项
	  popup.getMenuInflater().inflat(R.menu.popup, popup.getMenu());
	  其中R.menu.popup是菜单项， 其余与menu用法一样
