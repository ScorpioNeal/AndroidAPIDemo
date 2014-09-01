###Views/SearchView###
####search view####

    * 在ActionBar上的SearchView
    	* 获取WindowFeature: getWindow().requestFeature(Window.FEATURE_ACTION_BAR);
    	* 创建ActionBar上的SearchView
    	  MenuInflater inflater = getMenuInflater();
          inflater.inflate(R.menu.searchview_in_menu, menu);
          MenuItem searchItem = menu.findItem(R.id.action_search);
          mSearchView = (SearchView) searchItem.getActionView();
		  //其中R.menu.searchview_in_menu如下
		  <menu xmlns:android="http://schemas.android.com/apk/res/android" >
    		<item
        		android:id="@+id/action_search"
        		android:actionViewClass="android.widget.SearchView"//Notice！
        		android:icon="@android:drawable/ic_menu_search"
        		android:showAsAction="always"
        		android:title="@string/action_bar_search"/>
		  </menu>
		* 设置ActionBar展示方式
		  searchItem.setShowAsActionFlags(MenuItem.SHOW_AS_ACTION_IF_ROOM
                | MenuItem.SHOW_AS_ACTION_COLLAPSE_ACTION_VIEW);//可以参考官方文档那几种方式
		  如果是 mSearchView.setIconifiedByDefault(false); 那么表示一直是展开的
 		  如果是 mSearchView.setIconifiedByDefault(true);   那么表示是一个图标，然后点击会展开， 然后会有个叉叉，点击会关闭
		* 获取SearchManager
		   SearchManager searchManager = (SearchManager) getSystemService(Context.SEARCH_SERVICE);
		* 进行Search本机安装的application, Notice!!!
		  if (searchManager != null) {
            List<SearchableInfo> searchables = searchManager
                    .getSearchablesInGlobalSearch();

            // Try to use the "applications" global search provider
            SearchableInfo info = searchManager
                    .getSearchableInfo(getComponentName());
            for (SearchableInfo inf : searchables) {
                if (inf.getSuggestAuthority() != null
                        && inf.getSuggestAuthority().startsWith("applications")) {
                    info = inf;
                }
            }
            mSearchView.setSearchableInfo(info);
        }
		* 监听search事件setOnQueryTextListener(new OnQueryTextListener())
		  重写
			public boolean onQueryTextSubmit(String query) 提交时触发
			public boolean onQueryTextChange(String newText) search内容改变时触发

	* SearchView当作控件搭配listview使用
		* listview开启filter功能： mListView.setTextFilterEnabled(true);
		*  mSearchView.setOnQueryTextListener(new OnQueryTextListener() {
            
            @Override
            public boolean onQueryTextSubmit(String query) {
                return false;
				//true if the query has been handled by the listener, false to let the SearchView perform the default action. 
            }
            
            @Override
            public boolean onQueryTextChange(String newText) {
                if (TextUtils.isEmpty(newText)) {
                    mListView.clearTextFilter();//默认清楚filter
                } else {
                    mListView.setFilterText(newText.toString());//listview设置filter
                }
                return true;
            }
        });