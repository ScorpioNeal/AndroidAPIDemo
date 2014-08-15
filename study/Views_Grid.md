###Views/Grid###

	* 获取所有launch app
	 private void loadApps() {
        Intent mainIntent = new Intent(Intent.ACTION_MAIN, null);
        mainIntent.addCategory(Intent.CATEGORY_LAUNCHER);

        List<ResolveInfo> mApps = getPackageManager().queryIntentActivities(mainIntent, 0);//获取所有满足given intent的app
    }
    
    * Grid的多选模式,长按可以选择多个
    gridview.setChoiceMode(GridView.CHOICE_MODE_MULTIPLE_MODAL);
    
    * 设置多选监听器
    gridview.setMultiChoiceModeListener(new MultiChoiceModeListener());
    
    
    //TODO有待学习  action mode  一种类似context menu功能的东西 位于action bar的位置
    
    public class MultiChoiceModeListener implements GridView.MultiChoiceModeListener {
        public boolean onCreateActionMode(ActionMode mode, Menu menu) {
       		//Called when action mode is first created. The menu supplied will be used to generate action buttons for the action mode.
        }

        public boolean onPrepareActionMode(ActionMode mode, Menu menu) {
			//Called to refresh an action mode's action menu whenever it is invalidated
        }

        public boolean onActionItemClicked(ActionMode mode, MenuItem item) {
			//Called to report a user click on an action button.
        }

        public void onDestroyActionMode(ActionMode mode) {
        	//Called when an action mode is about to be exited and destroyed.
        }

        public void onItemCheckedStateChanged(ActionMode mode, int position, long id,boolean checked) {
            //Called when an item is checked or unchecked during selection mode.
            多选模式下选择一个或者取消一个回调方法
        }

    }
   
        
    
