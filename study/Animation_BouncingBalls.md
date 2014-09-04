###Animatino/BouncingBalls###

	* 背景的渐变	  使用ValueAnimator
	        ValueAnimator colorAnim = ObjectAnimator.ofInt(this,"backgroundColor", RED, BLUE);//（哪个目标进行动画， 进行动画的属性，Values...）其中values: A set of values that the animation will animate between over time.
            colorAnim.setDuration(3000);
            colorAnim.setEvaluator(new ArgbEvaluator());
            colorAnim.setRepeatCount(ValueAnimator.INFINITE);
            colorAnim.setRepeatMode(ValueAnimator.REVERSE);
            colorAnim.start();
	* //TODO