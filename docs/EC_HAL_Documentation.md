---
description: EC_HAL API
---

# Embedded Controller HAL

Written by:  Eun-Taek Nam



Program: 		C/C++

IDE/Compiler: Keil uVision 5

OS: 					WIn10

MCU:  				STM32F411RE, Nucleo-64





## GPIO Digital In/Out 

### Header File

 `#include "ecGPIO.h"`



```c++
#include "stm32f411xe.h"

#ifndef __EC_GPIO_H
#define __EC_GPIO_H

#define INPUT  0x00
#define OUTPUT 0x01
#define AF     0x02
#define ANALOG 0x03

#define HIGH 1
#define LOW  0

#define LED_PIN 	5
#define BUTTON_PIN 13


void GPIO_init(GPIO_TypeDef *Port, int pin, int mode);
void GPIO_write(GPIO_TypeDef *Port, int pin, int Output);
int  GPIO_read(GPIO_TypeDef *Port, int pin);
void GPIO_mode(GPIO_TypeDef* Port, int pin, int mode);
void GPIO_ospeed(GPIO_TypeDef* Port, int pin, int speed);
void GPIO_otype(GPIO_TypeDef* Port, int pin, int type);
void GPIO_pupdr(GPIO_TypeDef* Port, int pin, int pudr);

#endif

```




### GPIO_init\(\)

Initializes GPIO pins with default setting and Enables GPIO Clock. Mode: In/Out/AF/Analog

```c++
void GPIO_init(GPIO_TypeDef *Port, int pin, int mode);
```

**Parameters**

* **Port:**  Port Number,  GPIOA~GPIOH

* **pin**:  pin number (int) 0~15

* **mode**:   INPUT (0), OUTPUT (1),  AF(02), ANALOG (03)

  

**Example code**

```c++
GPIO_init(GPIOA, 5, OUTPUT); // calls RCC_GPIOA_enable()
GPIO_init(GPIOC, 13, INPUT); //GPIO_init(GPIOC, 13, 0);
```



### GPIO_mode\(\)

Configures  GPIO pin modes: In/Out/AF/Analog

```c++
void GPIO_init(GPIO_TypeDef *Port, int pin, int mode);
```

**Parameters**

* **Port:**  Port Number,  GPIOA~GPIOH

* **pin**:  pin number (int) 0~15

* **mode**:   INPUT (0), OUTPUT (1),  AF(02), ANALOG (03)

  

**Example code**

```c++
GPIO_mode(GPIOA, 5, OUTPUT);
```



## GPIO_read()

It contains the input value of the corresponding I/O port.

```
int GPIO_ospeed(GPIO_TypeDef *Port, int pin);
```

**Parameters**

* **Port** : Port Number, GPIOA~GPIOH
* **Pin** : Pin number (int) 0~15
* **speed** : Low speed (0), Medium speed (1), Fast speed (2), High speed (3)

**Example code**

```
int state = GPIO_read(GPIOC, 13); // button pressed : 0, button released : 1
```



## GPIO_write()

It functions as Output data register. Bits can be individually set and reset by writing to the GPIOX register.

```
void GPIO_write(GPIO_TypeDef *Port, int pin, int Output);
```

**Parameters**

* **Port** : Port Number, GPIOA~GPIOH
* **Pin** : Pin number (int) 0~15
* **Output** : LOW (0), HIGH (1)

**Example code**

```
GPIO_write(GPIOC, 13, 1); // 1: HIGH
```



## GPIO_pupdr()

Configures GPIO pin modes : In/Out/AF/Analog

```
void GPIO_pupdr(GPIO_TypeDef *Port, int pin, int pupd);
```

**Parameters**

* **Port** : Port Number, GPIOA~GPIOH
* **Pin** : Pin number (int) 0~15
* **pupd** : No PullupPulldown (0), Pull-Up(1), Pull-Down(2), ...



**Example code**

```
GPIO_pupdr(GPIOA, 5, 0); // 0: NO PUPD
```



## GPIO_otype()

Configures GPIO pin modes : In/Out/AF/Analog

```
void GPIO_otype(GPIO_TypeDef *Port, int pin, int type);
```

**Parameters**

* **Port** : Port Number, GPIOA~GPIOH
* **Pin** : Pin number (int) 0~15
* **type** : Output push-pull (0), Output open-drain (1)



**Example code**

```
GPIO_type(GPIOA, 5, 0); // 0: Output push-pull (RESET)
```



## GPIO_ospeed()

Configures GPIO pin modes : In/Out/AF/Analog

```
void GPIO_ospeed(GPIO_TypeDef *Port, int pin, int speed);
```

**Parameters**

* **Port** : Port Number, GPIOA~GPIOH
* **Pin** : Pin number (int) 0~15
* **speed** : Low speed (0), Medium speed (1), Fast speed (2), High speed (3)

**Example code**

```
GPIO_ospeed(GPIOA, 5, 1); // 1: Medium speed
```



`header.h`



The header file is `ecGPIO.h`
