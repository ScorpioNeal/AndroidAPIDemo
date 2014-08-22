###Views/Animation###

	* editview振动动画
		* 加载动画
		  Animation shake = AnimationUtils.loadAnimation(this, R.anim.shake);
		* 显示
		  view.startAnimation(shake);
	* flipper设置切换动画
		设置一个进入动画， 设置一个退出动画
		mFlipper.setInAnimation(AnimationUtils.loadAnimation(this,
                    R.anim.push_up_in));
        mFlipper.setOutAnimation(AnimationUtils.loadAnimation(this,
                    R.anim.push_up_out));
	* 设置Animation的加速器
	  Animation.setInterpolator(AnimationUtils.loadInterpolator(context, R.anim.interpolator));

	android.R.anim.accelerate_interpolator //加速
	android.R.anim.decelerate_interpolator //减速
	android.R.anim.accelerate_decelerate_interpolator//加速进入.与第一个的区别为当repeatMode为reverse时,仍为加速返回原点  
	android.R.anim.anticipate_interpolator//先往后退一点再加速前进  
	android.R.anim.overshoot_interpolator//减速前进,冲过终点前再后退  
	android.R.anim.anticipate_overshoot_interpolator
	android.R.anim.bounce_interpolator //停止前来回振几下  