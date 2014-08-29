###Views/CustomView###
####自定义控件####

	* 构造自定义的View(com.example.android.apis.view.LabelView)继承自View
	* 构造函数中获取xml资源文件中的属性(即可以使用xml中的自定义属性来设置view的属性)
		* TypedArray a = context.obtainStyledAttributes(attrs,
                R.styleable.LabelView);
		* 其中LabelView是在attrs.xml中写的
	    	<declare-styleable name="LabelView">
        		<attr name="text" format="string" />
        		<attr name="textColor" format="color" />
        		<attr name="textSize" format="dimension" />
    		</declare-styleable>
		* 获取text, textColor, textSize属性值
			* CharSequence s = a.getString(R.styleable.LabelView_text);
			* a.getColor(R.styleable.LabelView_textColor, 0xFF000000)
			* a.getDimensionPixelOffset(R.styleable.LabelView_textSize, 0);
			* 注意: R.styleable.LabelView_text通过后面加一个_和属性名来获取
		* 设置text, textColor, textSize的值 然后
		  requestLayout(); 通知布局更改
          invalidate(); 重绘
		* 使用完之后回收 a.recycle();
	* 构造控件宽高 重写onMeasure();//TODO 不太熟悉
	    @Override
    	protected void onMeasure(int widthMeasureSpec, int heightMeasureSpec) {
        	setMeasuredDimension(measureWidth(widthMeasureSpec),
            measureHeight(heightMeasureSpec));
    	}


		private int measureWidth(int measureSpec) {
        	int result = 0;
        	int specMode = MeasureSpec.getMode(measureSpec);
        	int specSize = MeasureSpec.getSize(measureSpec);

        	if (specMode == MeasureSpec.EXACTLY) {
            	// We were told how big to be
            	result = specSize;
        	} else {
            	// Measure the text
            	result = (int) mTextPaint.measureText(mText) + getPaddingLeft() + getPaddingRight();
            	if (specMode == MeasureSpec.AT_MOST) {
                	result = Math.min(result, specSize);
        		}
			}
        	return result;
    	}


    	private int measureHeight(int measureSpec) {
        	int result = 0;
        	int specMode = MeasureSpec.getMode(measureSpec);
        	int specSize = MeasureSpec.getSize(measureSpec);

        	mAscent = (int) mTextPaint.ascent();
        	if (specMode == MeasureSpec.EXACTLY) {
            	// We were told how big to be
           		result = specSize;
        	} else {
            	// Measure the text (beware: ascent is a negative number)
            	result = (int) (-mAscent + mTextPaint.descent()) + getPaddingTop() + getPaddingBottom();
            	if (specMode == MeasureSpec.AT_MOST) {
                	// Respect AT_MOST value if that was what is called for by
                	// measureSpec
                	result = Math.min(result, specSize);
            	}
        	}
        return result;
    	}
	* 重写onDraw()绘制
	   canvas.drawText(mText, getPaddingLeft(), getPaddingTop() - mAscent, mTextPaint);
	* 使用方法
	  布局 xml中添加view	
	  <com.example.android.apis.view.LabelView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@drawable/blue"
        app:text="Blue"
        app:textSize="20dp" />
	  跟布局添加
	  xmlns:app="http://schemas.android.com/apk/res/com.example.android.apis"


关于view的绘制部分见[view绘制](https://www.evernote.com/shard/s118/nl/12819723/f2e31c74-ea92-4a50-a2f2-31f725cc309b)