# Software PWM

Using software to produce a PWM signal with the MSP430 microcontrollers requires the use of timer with designated interrupts. Assuming upmode, the frequency of the signal can be determined using CCR0. Once the frequency of the PWM signal is set, the duty cycle can be controlled using another CCR register by triggering an interrupt between 0 and the CCR0 value. That interrupt can be used to set the signal, and then the signal can be reset to 0 using an interrupt for when the timer overflows. In the case of the lab, CCR1 lights up the LED, and CCR0 turns off the LED. To change the duty cycle of the PWM, an interrupt can take place after a button press, that changes the value of the CCR1 register. 

With the SMCLK (1 MHz), to produce a 1 kHz signal, with require 1000 counts (CCR0). Starting at a duty cycle of 50%, CCR1 is set to 500. In order to increment the duty cycle by 10%, 100 can be added to the CCR1. Once CCR1 matches CCR0, an "if" statement can be used to set it back to 0.  

Note: When coding this PWM, I had trouble getting the LED to reach 100% duty cycle. I figured out that the interrupts for the overflow CCR1 register were conflicting. In order to fix this problem, I disabled the overflow interrupt, so that the LED was constantly set. This required the use of three "if" statements instead of two.
