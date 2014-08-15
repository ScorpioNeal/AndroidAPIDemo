###App/AlertDialog###
####各种AlertDialog####


	```java
		AlertDialog.Builder(AlertDialogSamples.this,AlertDialog.THEME_TRADITIONAL)可以设置	AlertDialog的主题
	```
	
	.setItems(R.array.items, OnclickListener);
	//第一个参数为字符串数组
	
	ProgressDialog带有进度条的Dialog
	mProgressDialog.setButton(int whichButton, CharSequence text, OnClickListener listener);
	//第一个参数: 
	 DialogInterface.BUTTON_POSITIVE
	 DialogInterface.BUTTON_NEGATIVE
	 DialogInterface.BUTTON_NEUTRAL
	 
	 
	 AlertDialog里面带Radio可选框
	 setSingleChoiceItems（数组， 默认选择， OnClickListener listener）
	 
	 AlertDialog里面带复选框
	 setMultiChoiceItems(数组， 数组形式的默认选中， OnMultiChoiceClickListener listener)
	 
	 AlertDialog自定义展示的View
	 setView(View)
	 
	 
	 //TODO
	 setMultiChoiceItems(Cursor cursor, String isCheckedColumn, String labelColumn, OnMultiChoiceClickListener listener)
	 
	 Set a list of items to be displayed in the dialog as the content, you will be notified of the selected item via the supplied listener. The list will have a check mark displayed to the right of the text for each checked item. Clicking on an item in the list will not dismiss the dialog. Clicking on a button will dismiss the dialog.

	Parameters:
		cursor the cursor used to provide the items.
		isCheckedColumn specifies the column name on the cursor to use to determine whether a checkbox is checked or not. It must return an integer value where 1 means checked and 0 means unchecked. //是否应该显示选中
		labelColumn The column name on the cursor containing the string to display in the label.listener notified when an item on the list is clicked. The dialog will not be dismissed when an item is clicked. It will only be dismissed if clicked on a button, if no buttons are supplied it's up to the user to dismiss the dialog.//显示选项
	Returns:
		This Builder object to allow for chaining of calls to set methods
		
		
	```java
			String[] projection = new String[] { ContactsContract.Contacts._ID,
					ContactsContract.Contacts.DISPLAY_NAME,
					ContactsContract.Contacts.SEND_TO_VOICEMAIL };
			Cursor cursor = managedQuery(ContactsContract.Contacts.CONTENT_URI,
					projection, null, null, null);
			return new AlertDialog.Builder(AlertDialogSamples.this)
					.setIcon(R.drawable.ic_popup_reminder)
					.setTitle(R.string.alert_dialog_multi_choice_cursor)
					.setMultiChoiceItems(cursor,
							ContactsContract.Contacts.SEND_TO_VOICEMAIL,
							ContactsContract.Contacts.DISPLAY_NAME,
							new DialogInterface.OnMultiChoiceClickListener() {
								public void onClick(DialogInterface dialog,
										int whichButton, boolean isChecked) {
									Toast.makeText(
											AlertDialogSamples.this,
											"Readonly Demo Only - Data will not be updated",
											Toast.LENGTH_SHORT).show();
								}
							}).create();
	```
	
	----
	
	String android.provider.ContactsContract.ContactOptionsColumns.SEND_TO_VOICEMAIL = "send_to_voicemail"

	Whether the contact should always be sent to voicemail. If missing, defaults to false.

	Type: INTEGER (0 for false, 1 for true)
	
	-----
	
	String android.provider.ContactsContract.ContactsColumns.DISPLAY_NAME = "display_name"

	The display name for the contact.

	Type: TEXT