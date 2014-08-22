###Views/Listview###

	* 使用系统的Adapter
	  setListAdapter(new ArrayAdapter<String>(this,
                android.R.layout.simple_list_item_1, mStrings));
	* 使用自定义的Adapter
	  class MyAdapter extends BaseAdapter
	* 继承自BaseAdapter 重写
	  public boolean isEnabled(int position)
	  Returns true if the item at the specified position is not a separator. (A separator is a non-selectable, non-clickable item). The result is unspecified if position is invalid.
      //就是说如果return true表示这个item是可选择的可点击的
	* 更新listview
	  notifyDataSetChanged(); 
	  Notifies the attached observers that the underlying data has been changed and any View reflecting the data set should refresh itself. 
  	  在Adapter数据改变的时候调用这个可以刷新listview
	* item是RadioButton的listview
	  	* 使用android.R.layout.simple_list_item_single_choice
	  	  setListAdapter(new ArrayAdapter<String>(this,
                android.R.layout.simple_list_item_single_choice, GENRES));//只是指定样式-〉即右边带个圈，但是点击没有效果，圈圈不会变
		* listView.setChoiceMode(ListView.CHOICE_MODE_SINGLE); 设置选择模式，即点击圈圈会被选中
	* item是Checkbox的listview
	  	* 使用simple_list_item_multiple_choice
	  	          setListAdapter(new ArrayAdapter<String>(this,
                android.R.layout.simple_list_item_multiple_choice, GENRES));//只是指定样式-〉即右边带个框，但是点击没有效果，框框不会变
		* listView.setChoiceMode(ListView.CHOICE_MODE_MULTIPLE); 设置选择模式，即点击框会被选中
