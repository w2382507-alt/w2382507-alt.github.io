# arduino

- 函数
	- pinMode(pin, mode)
		- mode为设置的模式
	- digitalWrite(pin, value)
		- value为写入的值HIGH or LOW
	- digitalRead(pin)
	- delay(ms)
	- millis()
		- 返回启动以来的毫秒数
- OLED
	- SPI协议
		- 标准4线
			- MOSI：主器件数据输出，从器件数据输入
			- MISO：主器件数据输入，从器件数据输出
			- SCK：时钟信号，由主设备控制发出。
			- CS（NSS）：从机设备选择信号，由主设备控制。当 `CS` 为低电平则选中从器件。
	- C2I协议
	- U8g2库
		- 
		  ```c++
		  #include <Arduino.h>
		  #include <U8g2lib.h>
		  
		  //constructor
		  U8G2_SSD1306_128X64_NONAME_F_HW_I2C u8g2(/*rotation*/U8G2_R0， /*reset*/U8X8_PIN_NONE, clock, data);
		  //rotation旋转:R0为不旋转R1为旋转九十度，一直到R3
		  //reset复位引脚U8X8_PIN_NONE为无
		  //clock是SCL
		  //data是SDA
		  
		  void setup(void){
			  u8g2.begin();
		  }
		  
		  void loop(void){
			  u8g2.firstPage();
			  do {
			  //绘制内容
			  }while(u8g2.nextPage());
			  delay(1000);
		  }
		  ```
- 中断
	- attachInterrupt(digitalPinToInterrupt(pin), ISR, mode)
		- pin:GPIO端口号
		- ISR:中断执行的函数，没有返回值没有参数
		- mode：中断触发的方式
			- LOW：低电平
			- HIGH
			- RISING：上升沿触发
			- FALLING
			- CHANGE：电平变化触发
	- 中断处理函数内不要使用delay，使用micros()返回板子上电以来走过的微秒（µs）数
	- 中断处理函数内不要对oled发消息，只要改一个变量，让loop中改变oled状态就好，
- 定时器
	- 硬件定时器
		- 初始化
			1. hw_timer_t * timerBegin(timer_num, divider, count_up)
				- timer_num:定时器编号，0-3等
				- divider:分频系数，一般为80
				- count_up：指定定时器向上还是向下计数，true or false
			2. timerAttachInterrupt(timer, isr, *arg, intr_type)
				- timer：定时器指针
				- isr：中断处理函数
				- *arg：传给中断处理函数的参数
				- intr_type：中断类型，true为边沿触发，false为电平触发
			3. timerAlarmWrite(timer, alarm_value, autoreload)
				- timer：定时器指针
				- alarm_value：计数值，触发的值，单位us
				- autoreload：是否自动重载（持续重复，true or false）
			4. timerAlarmEnable(timer)
				- 启动计时器
		- 其他函数
			- timerStart(timer)
			- timerStop(timer)
			- timerRestart(timer)
	- 软件定时器 （Ticker类）
		- .detach()：停止
		- .active()：返回是否激活
		- once(n, callbacl, arg)：n秒后执行callback，不重复
		- once_ms(n, callback, arg)：n毫秒后执行callback，不重复
		- attach(n, callback, arg)：n秒后执行callback，重复
		- attack_ms(n, callback, arg)：n毫秒后执行callback，重复
- WIFI
	- `#include <WiFi.h>`
	- WiFi.begin(ssid, password)：连接网络。ssid和password都是const  char \*，注意begin不是一下子就完成的，在连接的时候就直接执行下面的代码了
	- WiFi.disconnect()：断开连接
	- WiFI.status()：返回状态
		- WLCONNECTED
		- WL_DISCONNECTED
		- WL_IDLE_STATUS：空闲
		- WL_NO_SSID_AVAIL：未找到指定WiFi
	- WiFi.localIP()：返回被分配的本地IP地址
	- WiFi.macAddress()：返回MAC地址
	- WiFi.scanNetworks()：扫描可用WiFi，返回扫描到的网络数
	- WiFi.SSID(networkIndex)：返回指定索引的WiFi的SSID
	- WiFi.RSSI(networkIndex)：返回指定索引的WiFi的信号强度
- HTTPClient
	- 首先创建HTTPClient类对象
	- .begin(url)：设置url
	- .addHeader(name, value)
	- .setAuthorization(username, password)
	- .setTimeout(timeout)
	- .GET()：发送GET请求，返回状态码
	- .POST(payload)
	- .responseStatusCode()
	- .responseHeaders()
	- .responseBody()
	- .getSring()
		- 使用ArduinoJson.h解析json数据
		- 创建对象`DynamicJsonDocument doc(json文档大小);`
		- deserializeJson(doc, json)  将json（字符串）解析到DynamicJsonDocument对象中
		- 使用`.doc["key"].as<type>()`获取对应值
	- .getStream()
	- .end()
- 串口监视器
	- Serial.begin(通信比特率):一般填9600
	- Serial.println()：串口打印内容