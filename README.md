# SOC_estimation
State of Charge estimation of Li-Ion battery, based on voltage measurements and Coulomb couting. Implementation on STM32 Nucleo board
![wykres1](https://github.com/user-attachments/assets/c3bb586c-1064-4a03-ba7e-10d01aa7f85e)

These are the preliminary measurement results. The BC234 transistor cuts off the load when the cell voltage drops to 2.8 V. However, after disconnection, the measured cell voltage rises back above 2.8 V. This causes the microcontroller to switch the transistor and load back on, resulting in cyclical on/off behavior. Clearly, this issue will need to be resolved.

![jumps](https://github.com/user-attachments/assets/c2f10ba8-d883-4b77-bb93-f26e9018a2c7)

Unfortunately, I couldn’t use the INA219 sensor (maximum current of 3.2 A) because it was damaged during soldering. Instead, the current was measured using an ACS758LCB-050B (maximum current of 50 A, sensitivity 40 mV/A). The output voltage was sampled by the Nucleo’s 12‑bit ADC. As a result, the readings show significant noise, and the ADC’s limited resolution is also evident — quantization effects can clearly be seen as discrete voltage steps.
I’m certain it will be interesting to compare the INA219 to the ACS758, as the two sensors differ so much in terms of design and performance.
![obraz](https://github.com/user-attachments/assets/2fd71b96-6bbf-4f46-9d97-9fb29c284e0e)

Numerical integration performed using the rectangular method resulted in a total energy of 6.75 Wh and a total charge of 1826 mAh.
In the next measurement, I will try to compare these results with data from a more accurate INA219 sensor and also apply the trapezoidal method for numerical integration.



