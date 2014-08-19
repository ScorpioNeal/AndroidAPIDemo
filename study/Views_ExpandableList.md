###Views/ExpandableList###

	* 与listview一样，需要一个adapter来指定显示内容
	  adapter extends BaseExpandableListAdapter
	  重载方法很容易，根据名字就看出来， 里面需要一个二维数组或者嵌套的list
	* 使用默认的样式会使得group左边带有一个箭头标识的icon
	* 构造contextmenu： registerForContextMenu（View view）
	* 如果activity继承自ExpandableListActivity 则可以通过getExpandableListView()直接获取ExpandableListView
	* 处理ExpandableListView点击
	  //获取MenuInfo
	  ExpandableListContextMenuInfo info = (ExpandableListContextMenuInfo) item.getMenuInfo();
	  //info.targetView 
	  //The view for which the context menu is being displayed. This will be one of the children Views of this ExpandableListView. 
      String title = ((TextView) info.targetView).getText().toString();
      //获取点击类型 ExpandableListView.getPackedPositionType
	  //获取点击的组的position ExpandableListView.getPackedPositionGroup
	  //获取点击的child的position ExpandableListView.getPackedPositionChild
      int type = ExpandableListView.getPackedPositionType(info.packedPosition);
      if (type == ExpandableListView.PACKED_POSITION_TYPE_CHILD) {
            int groupPos = ExpandableListView.getPackedPositionGroup(info.packedPosition); 
            int childPos = ExpandableListView.getPackedPositionChild(info.packedPosition); 
            Toast.makeText(this, title + ": Child " + childPos + " clicked in group " + groupPos,
                    Toast.LENGTH_SHORT).show();
            return true;
       } else if (type == ExpandableListView.PACKED_POSITION_TYPE_GROUP) {
            int groupPos = ExpandableListView.getPackedPositionGroup(info.packedPosition); 
            Toast.makeText(this, title + ": Group " + groupPos + " clicked", Toast.LENGTH_SHORT).show();
            return true;
        }

	* 如果不用自定义的Adapter，也可以使用系统带的SimpleExpandableListAdapter传入相应参数即可
	* //TODO 使用Cursor的Adapter
	 
        
    
