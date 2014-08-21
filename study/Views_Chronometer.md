###Views/Chronometer###
####计时器####
	
	*  启动 mChronometer.start();
	*  停止 mChronometer.stop();
	*  复位 mChronometer.setBase(SystemClock.elapseRealtime());
	*  设置格式: mChronometer.setFormat("Formateed time %s ");
		Sets the format string used for display. The Chronometer will display this string, with the first "%s" replaced by the current timer value in "MM:SS" or "H:MM:SS" form. If the format string is null, or if you never call setFormat(), the Chronometer will simply display the timer value in "MM:SS" or "H:MM:SS" form.
	*  清除格式: mChronometer.setFormat(null);