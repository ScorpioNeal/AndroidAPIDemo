###Views/AutoComplete###

	* AutoCompleteTextView通过设置setAdapter()来设置备选项
	  ArrayAdapter<String> adapter = new ArrayAdapter<String>(this, android.R.layout.simple_dropdown_item_1line, COUNTRIES);
	  其中第一个参数是context, 第二个是显示的layout xml，第三个是包含所有备选项的数组文件
	* MultiAutoCompleteTextView 可以输入多个的自动填充textview,
	  设置逗号分隔符
	  MultiAutoCompleteTextView.setTokenizer(new MultiAutoCompleteTextView.CommaTokenizer());
	* //TODO cursor