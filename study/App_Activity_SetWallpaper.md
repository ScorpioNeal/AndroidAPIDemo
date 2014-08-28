###App/Activity/SetWallpaper###
####设置壁纸获取壁纸####

	* 获取壁纸
		* WallpaperManager wallpaperManager = WallpaperManager.getInstance(this);
		* 获取Drawable
		  Drawable wallpaperDrawable = wallpaperManager.getDrawable();
	* 设置壁纸
	  wallpaperManager.setBitmap(imageView.getDrawingCache());
	  //notice! imageView.getDrawingCache()会返回Bitmap