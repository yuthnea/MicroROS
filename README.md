
# MicroROS

Setting up and Examples micro-ROS on any STM32 microcontroller



# Goal
If you follow all steps in the tutorial you should have an STM32 microcontroller with a micro-ROS publisher, subcribe,publisher_subscriber, multipl node that transmits messages via UART to your PC running ROS 2. Here you can receive the messages via ros2 topic echo



## micro-ROS

```bash
1.) Create a new CubeMx project for your micro controller
2.) In System Core -> RCC -> High Speed Clock (HSE) select Crystal/Ceramic Resonator
3.) In System Core -> SYS -> Timebase Source select TIM1
4.) In Middleware -> FREERTOS -> Interface select CMSIS_V2
4.1.) In Middleware -> FREERTOS -> Configuration -> Task and Queues double click the defaultTask and set a stack size of 3000. It has to be greater than 10.000 byte (3000 words * 4 byte = 12.000 byte).
5.) In Connectivity choose the UART / USART that you want to use.
5.1.) In the Uart configuration, go to DMA Settings. Click on the Add button. Click on the Select dropdown and choose both Rx and Tx.
5.2.) Click on the Rx DMA you've just created and for Mode choose Circular.
5.3.) For the priority of the DMA choose Very high for both Rx and Tx.
5.4.) Go to NVIC Settings of the UART and activate the UARTx global interrupt.
6.) Set up the Clock Configuration for your micro controller
7.) In Project Manager select a folder where to generate your code
7.1.) In Toolchain / IDE select Makefile
7.2.) Optional: In Project Manager -> Code Generator select Generate peripheral intitialization as a pair of '.c/.h' files per peripheral
8.) Click on Generate Code
9.) In the root folder of the code you've just generated, clone the following repository (into a subfolder, don't change its name).:

https://github.com/micro-ROS/micro_ros_stm32cubemx_utils.git
```



## Start the micro-ros-agent.
ros2 run micro_ros_agent micro_ros_agent serial -b 115200 --dev /dev/ttyACM0

## Authors

- [@(yuthnea)Rith-Josef](https://github.com/yuthnea/MicroROS)

