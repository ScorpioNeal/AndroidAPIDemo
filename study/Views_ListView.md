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
	* List9 Demo-> 类似联系人滑动的时候以一个类似toast的形式显示开头字母的例子
		* 准备一个view用来显示ABC..., windowmanager把他加载进来，并设置为invisible， 同时需要他是不可以focusable, touchable的 不然显示的时候后面就点击不了了
		* listview滑动接口setOnScrollListener（OnScrollListener）
		* 在onScroll回掉方法中写如果firstLetter不等于prevLetter的时候才显示， 即当前letter不等于上一个letter
	* android:stackFromBottom="true" 设置这个应该是让数据从下往上显示
	  list(1,2,3,4,5) 正常是1->2->3->4->5..
	  这个是1<-2<-3<-4<-5...后来的加载在先来的后面 ...有点乱
      android:transcriptMode="normal" //不太清楚
	
	
	* OnScrollListener回调解析
		new OnScrollListener() {    
        boolean isLastRow = false;    
        
        @Override    
        public void onScroll(AbsListView view, int firstVisibleItem, int visibleItemCount, int totalItemCount) {    
            //滚动时一直回调，直到停止滚动时才停止回调。单击时回调一次。    
            //firstVisibleItem：当前能看见的第一个列表项ID（从0开始）    
            //visibleItemCount：当前能看见的列表项个数（小半个也算）    
            //totalItemCount：列表项共数    
        
            //判断是否滚到最后一行    
            if (firstVisibleItem + visibleItemCount == totalItemCount && totalItemCount > 0) {    
                isLastRow = true;    
            }    
        }    
        @Override    
        public void onScrollStateChanged(AbsListView view, int scrollState) {    
            //正在滚动时回调，回调2-3次，手指没抛则回调2次。scrollState = 2的这次不回调    
            //回调顺序如下    
            //第1次：scrollState = SCROLL_STATE_TOUCH_SCROLL(1) 正在滚动    
            //第2次：scrollState = SCROLL_STATE_FLING(2) 手指做了抛的动作（手指离开屏幕前，用力滑了一下）    
            //第3次：scrollState = SCROLL_STATE_IDLE(0) 停止滚动             
            //当屏幕停止滚动时为0；当屏幕滚动且用户使用的触碰或手指还在屏幕上时为1；  
            //由于用户的操作，屏幕产生惯性滑动时为2  
        
            //当滚到最后一行且停止滚动时，执行加载    
            if (isLastRow && scrollState == AbsListView.OnScrollListener.SCROLL_STATE_IDLE) {    
                //加载元素    
                ......    
        
                isLastRow = false;    
            }    
        }    
    }  

	从onScrollStateChanged中也可以获取到firstVisibleItem 和 visibleItemCount
 	int firstVisibleItem = view.getFirstVisiblePosition();
    int visibleItemCount = view.getChildCount();

	* listview高效添加item的方法-->使用ViewHolder
       public View getView(int position, View convertView, ViewGroup parent) {
            // A ViewHolder keeps references to children views to avoid
            // unneccessary calls
            // to findViewById() on each row.
            ViewHolder holder;

            if (convertView == null) {
                convertView = mInflater.inflate(R.layout.list_item_icon_text,
                        null);

                // Creates a ViewHolder and store references to the two children
                // views
                // we want to bind data to.
                holder = new ViewHolder();
                holder.text = (TextView) convertView.findViewById(R.id.text);
                holder.icon = (ImageView) convertView.findViewById(R.id.icon);

                convertView.setTag(holder);
            } else {
                // Get the ViewHolder back to get fast access to the TextView
                // and the ImageView.
                holder = (ViewHolder) convertView.getTag();
            }

            // Bind the data efficiently with the holder.
            holder.text.setText(DATA[position]);
            holder.icon.setImageBitmap((position & 1) == 1 ? mIcon1 : mIcon2);

            return convertView;
        }

        static class ViewHolder {
            TextView text;
            ImageView icon;
        }
	* 多选模式的listview
	   lv.setChoiceMode(ListView.CHOICE_MODE_MULTIPLE_MODAL);
       lv.setMultiChoiceModeListener(ListView.MultiChoiceModeListener);
	   对于选中的样式改变需要这样设置： 
	   setListAdapter(new ArrayAdapter<String>(this,
                android.R.layout.simple_list_item_1, mStrings));//多选带勾的
	   setListAdapter(new ArrayAdapter<String>(this,
                android.R.layout.simple_list_item_activated_1,
                Cheeses.sCheeseStrings));//无边框，选中绿色

	* 需要标识选中的item
	  // Use the built-in layout for showing a list item with a single
      // line of text whose background is changes when activated.
        setListAdapter(new ArrayAdapter<String>(this,
                android.R.layout.simple_list_item_activated_1, mStrings));

	  //设置选中某个
	     getListView().setItemChecked(position, true);

	* listview使用SimpleCursorAdapter
		* 构造SimpleCursorAdapter
		  ListAdapter adapter = new SimpleCursorAdapter(Context,
                android.R.layout.simple_list_item_1,
                // Give the cursor to the list adatper
                Cursor,
                // Map the NAME column in the people database to...
                new String[] { Contacts.DISPLAY_NAME },
                // The "text1" view defined in the XML template
                new int[] { android.R.id.text1 });
		* 其中Cursor为
		  Cursor c = getContentResolver().query(Contacts.CONTENT_URI,
                new String[] { Contacts._ID, Contacts.DISPLAY_NAME }, null,
                null, null);
	  
	