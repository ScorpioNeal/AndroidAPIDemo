###App/Activity/PersistentState###
####状态保存####
	* onPause的时候保存 onResume的时候恢复 数据保存在preference里面
	*  mSaved.getSelectionStart() textview光标开始
	   mSaved.getSelectionEnd() textview光标结束

	   mSaved.setSelection(selectionStart, selectionEnd);//设置