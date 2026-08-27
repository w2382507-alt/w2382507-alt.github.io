- 程序运行例：
  ```python
  import sys
  from PySide6.QtWidgets import QApplication, QLabel

  app = QApplication(sys.argv)
  label = QLabel("Hello World!")
  label.show()
  app.exec()
  ```
	1. 从PySide6.QtWidgets模块导入适当的类
		- QtCore：纯底层逻辑，无任何窗口、按钮、图像界面控件
		- QtGui：图形绘制基础
		- QtWidgets：窗口、按钮、输入框等桌面控件
	2. 实例化QApplication
	3. 实例化小部件
	4. 调用app.exec()进入Qt主循环
- 信号和槽(slot)
	- 连接：
	  ```python
	  @Slot()
	  def target_func():
		  pass
	  
	  部件.信号.connect(target_func)
	  ```
	  
	- 当信号触发时执行函数：信号会将自己的状态传入槽函数
	- 要向函数传入信号的状态值，需要在Slot中写明变量类型，target_func()内写参数名称

- 视频播放
	- QtMultimedia.QMediaPlayer（引擎）──> setVideoOutput ──> QtMeltimediaWidgets.QVideoWidget（屏幕）
	- 
	  ```python
	  player = QMediaPlayer()              # ① 创建引擎
	  player.setVideoOutput(video_widget)  # ② 把画面输出到屏幕控件
	  player.setAudioOutput(audio_output)  # 设置音频输出对象，QtMultimedias.QAudioOutput
	  player.setSource(QUrl.fromLocalFile("视频文件路径"))  # ③ 告诉它播哪个文件
	  player.play()                        # 开始播放
	  ```
	  - `setSource` 需要的是"统一资源定位符"（URL），不是普通路径。本地文件要用 `QUrl.fromLocalFile()` 包装
	  - QUrl位于QtCore
	  - QMediaPlayer.mediaStatusChanged信号状态：
		  - 
		    | 状态常量 | 含义 |
			|---|---|
			|`QMediaPlayer.MediaStatus.EndOfMedia`|视频播放完了|
			|`QMediaPlayer.MediaStatus.LoadedMedia`|文件加载好了|
			|`QMediaPlayer.MediaStatus.PlayingMedia`|正在播放|
- QStackedWidget
	- .addWidget(界面)：会按创建的顺序赋予 index 值
	- .setCurrentIndex(int)：切换到对应界面
- 鼠标消息
	- 当鼠标被点击时，被事件循环捕获，打包成QMouseEvent实例，自动找到所在部件，并且调用控件的鼠标消息
	- def 控件.mousePressEvent(event: QMouseEvent):
		- super().mousePressEvent(event)#当被控件是继承过来的时候写一下比较好
		- 当鼠标被按下时做的事情
- QThead
	- 创建自定义类继承自QThead
	- 重写run函数
	- 开始线程时调用.start()
	