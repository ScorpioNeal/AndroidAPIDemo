###Views/DateWidget###

	* 获取当前年月日十分
	    final Calendar c = Calendar.getInstance();
		mYear = c.get(Calendar.YEAR);
		mMonth = c.get(Calendar.MONTH);
		mDay = c.get(Calendar.DAY_OF_MONTH);
		mHour = c.get(Calendar.HOUR_OF_DAY);
		mMinute = c.get(Calendar.MINUTE);
	* 创建日期选择dialog new DatePickDialog(Context, DateSetListener, Year, Month, Day);
	* 创建时间选择dialog new TimePickerDialog(Context, TimeSetListener, Hour, Minute, is24HourView(boolean))	;
	* 2个回调
		private DatePickerDialog.OnDateSetListener mDateSetListener = new DatePickerDialog.OnDateSetListener() {

		public void onDateSet(DatePicker view, int year, int monthOfYear,
				int dayOfMonth) {
			
		}
	};

	private TimePickerDialog.OnTimeSetListener mTimeSetListener = new TimePickerDialog.OnTimeSetListener() {

		public void onTimeSet(TimePicker view, int hourOfDay, int minute) {
			
		}
	};
	
	* 如果不是用弹出对话框的形式展示， 也可以选择控件形式TimePicker