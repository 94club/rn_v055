*
 要注意 ios 使用默认实现的addLoadingView的方法, 在主View之前增加一个view来实现splashscreen
  要注意 android 使用新增一个Dialog的方式来实现splashscreen

* 要注意 android 代码获取图片资源时(无文件后缀名), png与jpg都可以获取到
  但是在 ios 代码获取图片资源时(无文件后缀名), 只能获取到png

* (废弃, bitmap消耗过大)要注意 android 使用了bitmap操作图片进行了裁剪,
  为使launchScreen时设置的背景图与splashScreen的图片展现一致(android的顶部的statusBar与底部的navigationBar的高度会影响Dialog)

* 要注意 android 给windowbackground设置背景图也会加大每帧渲染的消耗, 并且会有可能导致奇怪的闪屏bug, 故也废弃
* 要注意 android 采用起始application设置window透明色的方式
* 要注意 android 从0.3x版本开始, 组件package的加载放至application中, 故将package加载和splashscreen显示二个动作分开,
  否则无法保证splashscreen显示的动作正好在onCreate操作之前

* drawable文件添加启动动画的文件资源
* style.xml添加 '<item name="android:windowIsTranslucent">true</item>' (说是优化交互体验, 没有测试过)
* MainActivity.java的onCreate的生命周期方法调用启动界面开启方法
* MainMainApplication.java引入启动界面的依赖
* app/build.gradle中dependencies添加 "compile project(':rn-splash-screen')"
* android/setting.gradle添加 "include ':rn-splash-screen'
project(':rn-splash-screen').projectDir = new File(rootProject.projectDir, '../node_modules/rn-splash-screen/android')"
* App.js中引入依赖，在合适的时候调用启动界面关闭方法
