**Flip-flops** store one bit and are *synchronous digital circuits* (the changes of state are synchronized by a clock signal). 

A Reset-Set flip-flop (RS) is used to store a singular bit. When not setting or resetting, the state of Q remains the same. The state changes on the clock rising or falling *edge* in an RS.
![[Pasted image 20241219105106.png]]

A **D-Type flip-flop** only takes in a data input and the state changes on the clock edge. 
![[Pasted image 20241219105621.png]]

**Registers** are made up of flip-flops. They store the data being manipulated within CPUs and are the fastest type of storage (secondary memory). 

A **shift register** *shifts* its output once every clock cycle. An **SI** is an input that supplies a new bit to shift "into" the register. For example, four flip-flops ABCD with values 0110 having an input of 1 would transform into 1011 and the previous value of D is lost.

One application of these is the conversion between **serial and parallel** data. Serial ports such as USBs transfer data in series. 
![[Pasted image 20241219110440.png]]

 Registers are expensive and occupy space on the core. L1 and L2 cache are very fast RAM which act as a buffer to the main DRAM. 

General purpose registers store all kinds of information (ie. data and address). Typically 16 registers is an optimal amount. 

A 32-bit register could address 4GB of RAM and more is needed for larger RAM. However, OS schemes can be used to split RAM into sections.

Address registers never store data and only an address that *points* somewhere in RAM. Stack pointers are used to point to a block of RAM for storing intermediate values.

**Status/flags** registers are sets of individual bits that have distinct meanings relevant to the processor such as the sign of the last result, whether or not the last result was negative, overflow errors, condition codes etc.

**Control registers** are "hidden" in the CPU. This includes the Instruction Decoding Register, the Memory Address Register and the Memory Buffer Register. The Program Counter is the only one visible in assembly code.

Week 2 Thursday, as part of [[Computer Architecture]]