###App/Activity/Intents###
####intent####
	*  选取音乐应用
		Intent intent = new Intent(Intent.ACTION_GET_CONTENT);
        intent.setType("audio/*");//类型
        startActivity(Intent.createChooser(intent, "Select music")); //多选

		Activity Action: Allow the user to select a particular kind of data and return it. This is different than ACTION_PICK in that here we just say what kind of data is desired, not a URI of existing data from which the user can pick. An ACTION_GET_CONTENT could allow the user to create the data as it runs (for example taking a picture or recording a sound), let them browse over the web and download the desired data, etc. 
		意思就是Intent.ACTION_GET_CONTENT是可以允许用户创造这样类型的data然后再返回的
		而ACTION_PICK则是选取已经存在了的data