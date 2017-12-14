
[Android开发-贝塞尔曲线初体验]

[Android开发之贝塞尔曲线进阶篇（仿直播送礼物，饿了么购物车动画）]
```
	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}

	dependencies {
	        compile 'com.github.guochenhome:BezierView-master:1.4.5'
	}
	
	
	
	/**
         * 设置 红点的半径
         *
         * 不考虑机型适配问题，本方法自动根据屏幕分辨率 由px转dp
         * @param mRadius
         */
        public void setmRadius(int mRadius) {
            this.mRadius = mRadius;
        }

```
