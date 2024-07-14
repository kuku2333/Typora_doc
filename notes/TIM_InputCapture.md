# 定时器输入捕获

在使用输入捕获模式下的定时器时，以下是必做的步骤：

(#) 使用 RCC_APBxPeriphClockCmd(RCC_APBxPeriph_TIMx, ENABLE) 函数启用 TIM 时钟

(#) 通过配置相应的 GPIO 引脚来配置 TIM 引脚

(#) 如有需要，按照本驱动程序第一部分所述配置时间基准单元，否则定时器将使用默认配置运行： (++) 自动重载值 = 0xFFFF (++) 预分频器值 = 0x0000 (++) 计数器模式 = 上计数 (++) 时钟分频 = TIM_CKD_DIV1

(#) 使用所需的参数填充 TIM_ICInitStruct，包括： (++) TIM 通道：TIM_Channel (++) TIM 输入捕获极性：TIM_ICPolarity (++) TIM 输入捕获选择：TIM_ICSelection (++) TIM 输入捕获预分频器：TIM_ICPrescaler (++) TIM 输入捕获滤波器值：TIM_ICFilter

(#) 调用 TIM_ICInit(TIMx, &TIM_ICInitStruct) 以使用相应的配置配置所需的通道，以仅测量输入信号的频率或占空比，或者调用 TIM_PWMIConfig(TIMx, &TIM_ICInitStruct) 以使用相应的配置配置所需的通道，以测量输入信号的频率和占空比

(#) 启用 NVIC 或 DMA 以读取测量的频率。

(#) 使用函数 TIM_ITConfig(TIMx, TIM_IT_CCx)（或 TIM_DMA_Cmd(TIMx, TIM_DMA_CCx)）启用相应的中断（或 DMA 请求）以读取捕获的值。

(#) 调用 TIM_Cmd(ENABLE) 函数以启用 TIM 计数器。

(#) 使用 TIM_GetCapturex(TIMx); 读取捕获的值。