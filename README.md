Exercise 7 – Demonstrate that the sharing of resources
in a multitasking design can lead to a deterioration in
system performance.

This project demonstrates the use of FreeRTOS to manage multiple tasks attempting to access a shared resource in a multitasking system. The program's output reflects how the four LEDs behave based on access control to the shared resource using a mutual exclusion mechanism.

Diagram Task:

Required Hardware:

STM32F401CCU6
LEDs
Required Software:

STM32CubeIDE
FreeRTOS
How It Works:

Task Initialization and Scheduling:

The program begins with FreeRTOS initialization, configuring tasks to run concurrently.
There are 4 main tasks as follows:
a. GreenTask and RedTask attempt to access a shared resource called StartFlag using a mutual exclusion mechanism.
b. OrangeTask runs continuously with higher priority.
c. BlueTask monitors conflicts in accessing the shared resource and activates the red LED if a conflict occurs.
Mutual Exclusion (Conflict Avoidance):

GreenTask and RedTask alternate in accessing the shared resource (StartFlag). This access is protected using mutual exclusion to ensure only one task accesses the resource at a time.
If a task successfully accesses the shared resource, the corresponding LED lights up.
If a task fails to access the shared resource because another task is using it, BlueTask activates to indicate the failure.
Orange LED Blinking:

OrangeTask has higher priority than other tasks, so it runs continuously without interruption.
The orange LED (LED4) blinks continuously with a 50ms delay, demonstrating that OrangeTask runs independently of the shared resource.
Conflict Handling:

If the critical section is removed or not implemented correctly, GreenTask and RedTask may try to access the shared resource simultaneously, causing conflicts.
BlueTask will frequently activate to indicate conflicts when both tasks attempt to access the shared resource at the same time.
LED Operation Cycle:

Normal Case: If mutual exclusion works correctly, GreenTask and RedTask will alternate, indicating successful access to the shared resource. OrangeTask will blink continuously at high speed.
Conflict Case: If mutual exclusion is not properly implemented, GreenTask and RedTask may light up simultaneously or in an irregular pattern, and BlueTask will activate to signal conflicts.

Hardware Overview:

Demo video:
