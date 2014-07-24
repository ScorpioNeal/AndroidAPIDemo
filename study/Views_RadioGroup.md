###Views/Radio Group###
    * 在xml中设置
    	<RadioGroup>
    		<RadioButton>...这种层级关系
    *  RadioGroup中： android:checkButton=""//设置默认选择的radio
    *  动态加载Radio
    	RadioButton newRadioButton = new RadioButton(this);
        newRadioButton.setText(R.string.radio_group_snack);
        newRadioButton.setId(R.id.snack);
        //Notice 这里的R.id.snack是在values文件夹中ids文件里面写的
        //<resources>
  		//	<item type="id" name="snack" />
		//</resources>
        LinearLayout.LayoutParams layoutParams = new RadioGroup.LayoutParams(
                RadioGroup.LayoutParams.WRAP_CONTENT,
                RadioGroup.LayoutParams.WRAP_CONTENT);
        mRadioGroup.addView(newRadioButton, 1, layoutParams);
        //这里的1表示加载到RadioGroup的哪个位置 从0开始
	* setOnCheckedChangeListener// RadioGroup选择不同的radio会回掉的方法
	* RadioGroup.clearCheck(); 清楚选择的Radio