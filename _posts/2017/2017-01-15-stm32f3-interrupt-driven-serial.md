---
layout: default
title: Interrupt driven USART for stm32f3
excerpt: A quick and easy implementation of interrupt driven USART for your project
---

# {{page.title}}

{{excerpt}}

## [FULL PROJECT WITH CODE](https://github.com/MauroMombelli/stm32f3-serial)

## WHY

This implementation is completly non-blocking, for read and write; data is placed on circular buffer where the interrupt will take care of. 
This limit every message to be at max big as the buffer (256 byte in this case, to take advantage of natural byte overflow). 
At the moment if the read has some bad quirkness if the index of readed data overflow over the current index of message to read, causing the loss of 256 char; i may fix this in the future.

## HOW

When i develop code for my project i like to create little modular and clean libraies that try to keep everything encapsulated, with minimal setup from the user and no dynamic memori allocation.
The idea is that i can create a git submodule in my main project that will care of all the subproject.
This help to move bugfix to all project that need it, but at the same time prevent a pull from the main project to mess with the versioning of the submodules (but this is material for an articel by itself).

## IMPLEMENTATION

In this specific case, only the baudrate is configurable, and the rest of the parameter are fixed at 8n1 with no flow control, as this is most of the serial configuration you will find out there; the pin are hardcoded for stm32f303. 

For sure the configuration could be made more generic, something that i plan to do when and if i will have to use this code on other version of the chip, like the stm32f301. 

Lets take a look at its interface! 

{% highlight c %}
void USART1_Init(const uint32_t speed);
uint8_t USART1_Read(uint8_t * const ris, const uint8_t len);
void USART1_Write(const void * const mess, const uint8_t len);
{% endhighlight %}

easy as it come; 
first the library need to be initialized, then byte array can be read or write to the serial. 

USART1_Read return the number of byte read, that can be 0; to prevent any allocation library-side, you have to pass to the funcion an initialized array and its len. 
if the returned number of byte read is the same size of your buffer, chances are there is still data to read, so take care! 

So we have two special case for USART1_Read: 

- no data available: return 0
- more data available: no specific return value, if the buffer is filled, you need to call the function again

USART1_Write write the current message in the buffer. As it is a circular buffer, if you write too fast you will override the older messages. 
There is currently no way to know how much space is left on the buffer; it is easy to implement so its left as exercise to the readed (unless I will need it later) 

So we have two special case for USART1_Write: 

- no way to check buffer state
- new data override oldest data if you fill the buffer faster than the serial comminication can manage
