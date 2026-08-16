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
		  U8G2_SSD1306_128X64_NONAME_F_HW_I2C u8g2(U8G2_R0);
		  
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
