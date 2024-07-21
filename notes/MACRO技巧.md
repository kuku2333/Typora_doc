在IIC.h中这样定义宏：

```
#define TOUCH_IIC_SCK_PIN		TOUCH_GPIO_Port,TOUCH_GPIO_Pin

#define IIC_Digital_Write(_pin, _value) GPIO_WriteBit(_pin, _value == 0 ? Bit_RESET : Bit_SET)
#define IIC_Digital_Read(_pin) GPIO_ReadInputDataBit(_pin)
```

这样，在使用IIC_Digital_Write这个宏时，可以这样用：

```
IIC_Digital_Write(TOUCH_IIC_SCK_PIN, 0)
```

而TOUCH_GPIO_Port和TOUCH_GPIO_Pin定义在pin.h中：

```
#define TOUCH_GPIO_Port			GPIOB
#define TOUCH_GPIO_Pin			GPIO_Pin_8
```

这样就有了统一的接口。

在使用时，需要分别为不同的外设定义TOUCH_IIC_SCK_PIN，TOUCH_GPIO_Port，TOUCH_GPIO_Pin。





```
#define TOUCH_WRITE_PORT			GPIOB
#define TOUCH_WRITE_PIN				GPIO_Pin_8
#define TOUCH_READ_PORT				GPIOB
#define TOUCH_READ_PIN				GPIO_Pin_9

#define TOUCH_IIC_SCK_PIN		TOUCH_GPIO_Port,TOUCH_GPIO_Pin
#define TOUCH_IIC_SDA_PIN		TOUCH_GPIO_Port,TOUCH_GPIO_Pin

#define IIC_Digital_Write(_pin, _value) 	GPIO_WriteBit(_pin, _value == 0 ? Bit_RESET : Bit_SET)
#define IIC_Digital_Read(_pin) 				GPIO_ReadInputDataBit(_pin)
```

