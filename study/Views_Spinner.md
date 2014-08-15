###Views/Spinner###

    * 构建adapter
    ArrayAdapter<CharSequence> adapter = ArrayAdapter.createFromResource(this, R.array.*. android.R.layout.simple_spinner_item);//使用系统adapter
    //Context context, int textArrayResId, int textViewResId)
    * 设置下拉条显示样式
    adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item);
    //使用系统样式 
    *添加监听器
    setOnItemSelectedListener();
