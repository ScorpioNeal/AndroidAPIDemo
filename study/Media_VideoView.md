###Media/VideoView###
####视频播放控件####

	* xml中声明VideoView
	* 设置播放视频的本地路径
	  mVideoView.setVideoPath(String path);
      或者mVideoView.setVideoURI(Uri.parse(URLString));
	* 设置控制器
	  mVideoView.setMediaController(new MediaController(context));
	* 播放
	  mVideoView.requestFocus();
  	  mVideoView.start();