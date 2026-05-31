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

定时器（未实验）
1.定时器定时
            HAL_TIM_Base_Start_IT(&htim);   // 功能：定时器开始计数，每到周期触发一次中断   需要开启NVIC   
            void HAL_TIM_PeriodElapsedCallback(TIM_HandleTypeDef *htim) // 触发：使用 HAL_TIM_Base_Start_IT() 时
            {
                if (htim->Instance == TIMx) 
                {
                    // 定时周期到，执行代码
                }
            }

2.PWM 输出  在定时器里面选择内部时钟，设置psc和arr，然后设置引脚模式
            不需要设置NVIC，因为这个不需要CPU参与
            __HAL_TIM_SET_COMPARE(&htim2, TIM_CHANNEL_1, n);  配置占空比=n/arr+1
            HAL_TIM_PWM_Start(&htim, TIM_CHANNEL_x);    开启pwm
            HAL_TIM_PWM_Stop(&htim, TIM_CHANNEL_x);  关闭pwm



3.输入捕获  在定时器里面选择内部时钟，设置psc和arr，然后设置引脚模式，可以选择通道2或者4为输入捕获间接模式，代表同样捕获1或者3的值（注意设置上升沿和下降沿）
            使能NVIC
            HAL_TIM_IC_Start_IT(&htim, TIM_CHANNEL_x);  // 功能：启动输入捕获，开启捕获中断
            uint32_t value = HAL_TIM_ReadCapturedValue(&htim, TIM_CHANNEL_x);   // 返回：捕获到的计数值
            void HAL_TIM_IC_CaptureCallback(TIM_HandleTypeDef *htim)    // 触发：使用 HAL_TIM_IC_Start_IT() 时
            {
                if (htim->Channel == HAL_TIM_ACTIVE_CHANNEL_x) 
                {
                    // 捕获完成，读取值
                    uint32_t value = HAL_TIM_ReadCapturedValue(htim, TIM_CHANNEL_x);
                }
            }



4.编码器模式
            HAL_TIM_Encoder_Start(&htim, TIM_CHANNEL_ALL);  // 功能：启动编码器接口，开始计数
            int32_t count = __HAL_TIM_GET_COUNTER(&htim);   // 返回：当前编码器计数值
            __HAL_TIM_SET_COUNTER(&htim, value);            // 参数：value 为要设置的初始值
            HAL_TIM_Encoder_Stop(&htim, TIM_CHANNEL_ALL);   //停止编码器


5.高级定时器