# FreeRTOS_Dispatcher
City dispatch simulation

Simulate a "City Dispatch" unit. 
Different Events come into the centralized city "dispatcher", the events should be sent to the required departments (Police, Fire, Ambulance, Corona).

1. We simulate (implement) the events using random messages and sends them 
through a queue from an ISR to the dispatcher thread.

2. The dispatcher thread read from the queue, check the type of the message (its code) and send the message to the relevant task.

3. Each Department thread (ambulance, police,…) will get out of blocking mode, receive the dispatcher's request and take a random number of time (ticks ) to complete, when done it'll go back to blocking mode.

4. Each Department thread (ambulance, police,…) has a limited number of resources It can use concurrently, so simulation accordingly:

       a. Ambulance – 4 (Units)

       b. Police – 3 (Units)

       c. Fire department – 2 (Units)

       d. Corona - 4 (Units)

5. In addition, each Department thread and the dispatcher write an entry in a logging area (Printf/Uart Transmit in STM32)
