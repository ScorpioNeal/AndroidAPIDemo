###App/Activity/Animation###
####Activity切换动画####

	* startActivity(new Intent(Animation.this, CustomView1.class));
	  //第一个是进入动画，第二个是退出动画
      overridePendingTransition(R.anim.fade, R.anim.hold);