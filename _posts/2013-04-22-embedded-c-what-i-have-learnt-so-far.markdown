---
layout: post
title: "Embedded C &#8211; what I have learnt so far"
date: 2013-04-22T09:43:49+00:00
---

I have recently been working with my good friend Darren Leyland to learn Embedded C on the AVR platform and I thought I would share what I think I have learnt so far.

<p>Before we begin, an 'AVR' is a type of microcontroller that can be programmed to do a myriad of tasks. Microcontroller exist inside allow of devices including your phone, they are a simple cpu of some sorts.</p>
<p>Now into the code...you what ports ont he AVR, the AVR we are using is the ATMEGA32 which has 4 ports (PORTA, PORTB, PORTC and PORTD). Each port represents 8 pins on the chip as a binary number like this:</p>
[c]PORTB = 0b0000001[/c]
<p>The code above sets pin 1 to high (+5v) which for arguments sake is linked up to a led, the led is now on. To turn it off we set the pin to low(0v) like this:</p>
[c]PORTB = 0b0000000[/c]
<p>A major learning block for me has been the bitwise operators, we are going to use one now, this flips the bits, which, when ran in a loop will flash the led on and off.</p>
[c]PORTB ^= 0b0000001[/c]
<p>I think that will do for now, I am currently trying to master the other bitwise operators. I hope this gives you a taste of embedded C, call back for more embedded C lovelyness.</p>
