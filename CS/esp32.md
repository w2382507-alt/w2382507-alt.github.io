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
