# STM32 Timer Interrupt Example using HAL

## Overview

This project demonstrates the use of **hardware timer interrupts** on the STM32 Blue Pill (STM32F103C8T6) using STM32 HAL drivers.

A timer interrupt is used to monitor the duration of a button press without blocking the main program execution. The project also demonstrates concurrent UART transmission while the timer runs in the background.

---

## Features

* Hardware Timer Interrupt (TIM3)
* Non-blocking timing operation
* GPIO input monitoring
* GPIO output control
* UART debugging messages
* STM32 HAL driver usage
* Background task execution using interrupts

---

## Hardware Used

* STM32F103C8T6 (Blue Pill)
* STM32CubeIDE
* STM32 HAL Drivers
* Push Button
* LED
* UART Serial Monitor

---

## Working Principle

### Button Detection

* The system continuously monitors a push button connected to `PA0`.
* When the button is pressed:

  * Timer3 interrupt starts.
  * A flag variable (`present_flag`) becomes active.

---

### Timer Operation

TIM3 is configured to generate interrupts periodically.

```text id="vtxk9f"
Prescaler = 7999
Period = 999
```

Using the default STM32 clock configuration, this creates approximately a 1-second timer interrupt.

---

### Interrupt Callback

The following callback executes whenever the timer period completes:

```c id="8s2t2x"
HAL_TIM_PeriodElapsedCallback()
```

Inside the callback:

* Button state is checked
* Timer is stopped if button is released
* LED status is updated
* Timing counters are reset

---

### Non-Blocking Execution

While the timer runs in the background:

* UART continuously prints:

```text id="jlwm2v"
Ongoing Task
```

This demonstrates:

* interrupt-based execution
* background processing
* non-blocking embedded programming

---

## GPIO Connections

| Pin | Function          |
| --- | ----------------- |
| PA0 | Push Button Input |
| PA1 | LED Output        |

---

## UART Output

Example serial monitor output:

```text id="jlwm6t"
Ongoing Task
Done
```

---

## Concepts Demonstrated

* Timer Interrupts
* Interrupt Service Routine (ISR)
* Non-blocking delays
* GPIO handling
* UART communication
* STM32 HAL programming
* Event-driven embedded systems

---

## Files and Modules

* `main.c`
* Timer configuration (`TIM3`)
* UART configuration (`USART1`)
* GPIO configuration

---

## Future Improvements

* Add external interrupt (EXTI) for button
* Use FreeRTOS tasks
* Add debounce handling
* Add multiple timer channels
* Use PWM output with timers

---

## Author

Sanchit Bhojwani
B.Tech Electronics and Communication Engineering (ECE)
Embedded Systems and Robotics Enthusiast

