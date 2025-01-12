#comparch_other 

Many inputs are analogue and must be converted to digital signals through **analogue to digital converters** (ADCs). 

A transducer senses an analogue input and converts it into a voltage.

**Temperature Example**: -20c to 35c in the UK. Can be converted to digital bits where -20c is 0 and 35c is 4095 (as temperature is continuous data).

---
#### **Quantisation**
is the process of assigning ranges of continuous analogue values to digital values. 
This introduces "steps"; in the below example, the step is 0.005. The smaller the steps, the more accurately the values are represented.

| Temperature, analogue | Assigned value, digital |
| --------------------- | ----------------------- |
| 3.005 < x < 3.01      | 010                     |
| 3.01   < x < 3.015    | 011                     |
| 3.015 < x < 3.02      | 100                     |
This may also occur in images, where similar colours will be assigned the same bit.
![[Pasted image 20250102162254.png]]

 - **Amplification** is required when the input to the ADC might be too much for the analogue input, such as 1.8V. The signal might be small, such as from 0V to 1V. This would be read as 0 to 4096/1.8=2275; each step would be 1/2275 volts. This loses some precision and an amplifier of gain 1.8 could be used. 
 
 - **Offset** refers to the practice of shifting the input. For example, the signal may be -1V to 1V so shifting the signal up to 1V would be needed. You could set 0=-1V and 4096=1V.
---
#### **Analogue to Digital Converters (ADCs)**
- can sense anything with appropriate transducer
- design decisions are important: number of bits? speed of conversion? cost?

**Range and quantisation**: If Full Scale Range is 3.3V, each ADC step is 3.3/4096=0.0008V or 0.8mV

ADCs use multiple **comparators** which compare two analogue inputs anfld produce a digital output depending on which input is higher. They output 0 or 1. 

- a **Flash ADC** is:
	- very fast, expensive
	- one comparator for every quantised voltage level (ie. 8-bit flash ADC contains 256 comparators)

- **MCP3008 ADC**: *successive approximation ADC*:
	- 10-bit resolution
	- 200 kHz max sample rate
	- Digital value = 1024 * Vin / 3.3 (when using 3.3V power supply)

--- 
**Digital to Analogue Converter (DACs)**
- takes a digital input and converts to an analogue voltage. Same issues as ADC but **always** faster than ADC.
---
#### **Sampling**
Sampling is how fast the analogue signal is read. Sampling too slowly is known as **aliasing**. 
![[Pasted image 20250102170200.png]]
The **Nyquist Rate**: sampling should take place at least as fast as **2x the highest frequency**.
For sounds up to 20kHz, we should sample min 40kHz. Otherwise, aliasing will take place. 
If unable to sample that fast, then filter out all frequencies above sampling rate.

**Moiré** is is aliasing that has taken place in imaging. Shrinking an image badly of high resolution or taking a low resolution image of a high resolution backdrop may cause this.
![[Pasted image 20250102170553.png]]

When converting DAC it is also important to smooth out the reconstructed signal.
![[Pasted image 20250102170651.png]]

---
#### **Pulse Width Modulation** 
is an on/off signal used for motors or LEDs.
i.e. the more ON the faster the motor spins or the brighter the LED shines.
Microcontrollers usually have PWM hardware to make these signals.
![[Pasted image 20250102170908.png]]
i.e. if an LED is on a 25% duty cycle it will be turned on for 1/4th of the time which to our eyes will be dimly lit.

Week 4 Thursday, as part of [[Computer Systems (1313)]]
