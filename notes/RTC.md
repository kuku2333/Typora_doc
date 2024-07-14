# RTC

RTC（Real Time Clock）是一个独立的BCD定时器\计数器。

产生时钟来源时，有两个预分频器，为的是更大的分频，降低功耗。

## 程序编写步骤（如何使用RTC外设）

- 这个实时时钟（RTC）、RTC备份寄存器、备份SRAM在主VDD供电没有时，可以从VBAT（也就是batter voltage电池电平）得到电源。去保存内容到RTC备份寄存器、备份SRAM，当VDD关掉时供应RTC，VBAT引脚可以连接一个可选的备用电压，可以是电池或者其他电源。



- 在备份域复位之后，备份域（RTC寄存器、RTC备份数据寄存器、备份SRAM）是保护的，拒绝可能的不想要的写访问。要想开启进入RTC域和RTC寄存器，需要做这些步骤：
  1. 使能电源控制器（PWR）APB1接口时钟使用这RCC_APB1PeriphClockCmd()函数。
  2. 使能访问RTC域使用这个PWR_BackupAccessCmd()函数。
  3. 选择这个RTC时钟源使用这个RCC_RTCCLKConfig()函数。
  4. 使能RTC时钟使用这个RCC_RTCCLKCmd()函数。	



- 使用RTC外设：
  1. 使能这个RTC域访问。
  2. 配置RTC预分频器（同步的和异步的），还有RTC小时格式，使用RTC_Init()函数配置。

​	

- 时间和日期的配置
  1. 配置这个RTC日历（时间和日期）使用这个RTC_SetTime()和RTC_SetDate()函数。
  2. 去读这个RTC日历，使用这个RTC_GetTime()和RTC_GetDate()函数。
  3. 使用RTC_DayLightSavingConfig()函数去增加或者减少一小时到这个RTC日历。
- RTC唤醒配置
  1. 配置这个RTC唤醒时钟源使用这个RTC_WakeUpClockConfig()函数。
  2. 配置这个RTC唤醒计数器使用这个RTC_SetWakeUpCounter()函数。
  3. 使能RTC唤醒使用这个RTC_WakeUpCmd()函数。
  4. 去读这RTC唤醒计数器寄存器，使用这个RTC_GetWakeUpCounter()函数。

RTC_Weekday_Monday   
RTC_Weekday_Tuesday  
RTC_Weekday_Wednesday
RTC_Weekday_Thursday 
RTC_Weekday_Friday   
RTC_Weekday_Saturday 
RTC_Weekday_Sunday   

![](.\pictures\RTC中断.png)

- 