# Hardware PWM

When implementing PWM using hardware, all you have to do is use set the output mode, and start a timer that produces the right frequency. No interrupts for the timer are required.  The output mode can be set using 3 bits in the TACCTL register. Using the toggle/reset output mode, the signal produced is toggled when it reaches CCR1 and reset when it reaches CCR0. Like before, a button interrupt can be used to change CCR1 which will change the duty cycle. Once the output signal is configured, it can be sent to a particular pin by setting PxSEL and PxDIR to 1 based on the port mapping of the microcontroller (PxSEL2 should be set to 0).

