stm32

IDE浮点数设置：右键项目，点击Properties,C/C++build,Setting,MCU/MPU Setting,勾选右下角

GPIO:
HAL_GPIO_WritePin()     设置引脚输出电平 
HAL_GPIO_ReadPin()      读取引脚输入电平 
HAL_GPIO_TogglePin()    翻转引脚电平 

中断：
1.轮询模式      普通GPIO，不需要启用中断

2.外部中断模式  GPIO设置EXTI，并且在NVIC里面开启中断，配置优先级
                void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin)//回调函数
                HAL_Delay();//这个延时也是中断延时，所以也有优先级，用的时候要考虑优先级

3.定时器中断    定时器配置只用配置时钟，然后设置PSC，ARR，NVIC里面设置优先级
                HAL_TIM_Base_Start_IT(&htim6);//要在main里面开启对应的中断句柄
                void HAL_TIM_PeriodElapsedCallback(TIM_HandleTypeDef *htim)//并且启动回调函数

4.串口中断      选择串口模式，配置参数，配置NVIC
                HAL_UART_Receive_IT HAL_UART_Transmit_IT
                

5.DMA模式       选择串口模式，并且配置DMA和NVIC
                HAL_UART_Receive_DMA HAL_UART_Transmit_DMA

6.事件模式