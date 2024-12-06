# Exercise 7: Demonstrating Resource Sharing and System Performance Deterioration in a Multitasking Design

This project demonstrates how FreeRTOS manages multiple tasks attempting to access a shared resource in a multitasking system. The program showcases the behavior of four LEDs, highlighting the effects of proper and improper resource sharing using a mutual exclusion mechanism.

---

## **Diagram Task**
https://drive.google.com/file/d/18MD5usXj3OTBPVKLr7SZ-sG0O04YJtgU/view?usp=drive_link

---

## **Required Hardware**
- **STM32F401CCU6** Microcontroller
- LEDs (Green, Red, Blue, Orange)

---

## **Required Software**
- **STM32CubeIDE**
- **FreeRTOS**

---

## **How It Works**

### **Task Initialization and Scheduling**
- The program starts by initializing **FreeRTOS**, which configures tasks to run concurrently.
- **Four main tasks** are implemented:
  1. **GreenTask**: Attempts to access a shared resource (`StartFlag`) using mutual exclusion.
  2. **RedTask**: Similar to GreenTask, attempts to access the same shared resource.
  3. **OrangeTask**: Runs continuously with **higher priority**, independently of the shared resource.
  4. **BlueTask**: Monitors for access conflicts and activates the **blue LED** if conflicts occur.

---

### **Mutual Exclusion (Conflict Avoidance)**
- **GreenTask** and **RedTask**:
  - Alternate in accessing the shared resource (`StartFlag`).
  - Use a **mutual exclusion mechanism** (e.g., semaphores) to ensure only one task accesses the resource at a time.
  - **Green LED** or **Red LED** lights up when the task successfully accesses the resource.
- **BlueTask**:
  - Activates the **blue LED** if a conflict occurs (e.g., when two tasks try to access the shared resource simultaneously).

---

### **Orange LED Blinking**
- **OrangeTask**:
  - Has **higher priority** than all other tasks.
  - Runs continuously without interruption.
  - Controls the **orange LED**, which blinks with a **50ms delay** to demonstrate independent operation from the shared resource.

---

### **Conflict Handling**
- If the critical section is removed or not implemented correctly:
  - **GreenTask** and **RedTask** may try to access the shared resource simultaneously.
  - **BlueTask** frequently activates, and the **blue LED** lights up to signal conflicts.

---

## **LED Operation Cycle**

### **Normal Case**
- **GreenTask** and **RedTask** alternate access to the shared resource.
  - Green and red LEDs light up alternately, indicating successful resource access.
- **OrangeTask** runs independently and blinks the **orange LED** at high speed (50ms delay).
- **BlueTask** does not activate, as no conflicts occur.

### **Conflict Case**
- Without proper mutual exclusion:
  - **GreenTask** and **RedTask** may light up simultaneously or in irregular patterns.
  - **BlueTask** frequently activates, lighting the **blue LED** to indicate conflicts.

---

## **Hardware Overview**
- **Microcontroller**: STM32F401CCU6
- **LEDs**:
  - **Green LED**: Indicates access by **GreenTask**.
  - **Red LED**: Indicates access by **RedTask**.
  - **Blue LED**: Indicates conflicts in shared resource access.
  - **Orange LED**: Demonstrates high-priority task running independently.
https://drive.google.com/file/d/16Y04Cxs3r6Ddw4P349TiRfD-AzsrOiKe/view?usp=sharing
---

## **Demo Video**
https://drive.google.com/file/d/1PJ0HDzmCBbItIJYzymB1eZohwKEN7pK7/view?usp=sharing
