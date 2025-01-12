A **scalar operation** is a single operation on scalar values such as A=B+C or D=ExF.

We can do these two operations simultaneously. 
Most operations are on scalar quantities.

A **superscalar** system has multiple pipelined arithmetic units to perform operations simultaneously (see [[Pipelines and Branch Prediction]]).

Unlike regular pipelines, superscalar pipelines can execute more than one instruction in the same clock cycle.
![[Pasted image 20241219135749.png]]

### Limitations
Superscalar implementation is compiler based optimisation.
They are limited by many things:
- true data dependency: 2 instructions, same variable
- procedural dependency: in-branch, out-of-branch, same variable
- resource conflict: 2 instructions, same resource
- output dependency


![[Pasted image 20241223152239.png]]
#### True Data Dependency
1 `ADD r1, r2
2 `MOVE r3, r1`
Executing instructions using the same variable.
#### Procedural Dependency
1 `if (x+2) > y`
	`y = y + 1`
2 `z = x + y`
Executing instructions after a branch in parallel with instructions in a branch.
#### Resource Conflict
Instructions requiring access to the same resource at the same time, such as two arithmetic instructions accessing the ALU. You can have duplicate resources to alleviate the issue.

---
### Design Issues
- **Instruction level parallelism (program property)**: instructions in a sequence are independent, execution can be overlapped

- **Machine parallelism (hardware property)**: ability to take advantage of instruction level parallelism
	- duplication of resources
	- out-of-order issuing of instructions
	- register renaming

---
### Instruction Issue Order
- Order in which instructions:
	- are fetched
	- are executed
	- change registers and memory=
##### In-Order Issue, In-Order Completion
- Issue instructions in the order they occur
- Not efficient ie. spare ALU may not be used
- May fetch multiple instructions that stall if necessary
##### In-Order Issue, Out-of-Order Completion
1. `r3 = r3 + r5`
2. `r4 = r3 + 1` 
3. `r3 = r5 + 1`
If they complete not in order, the result will be wrong.
##### Out-of-Order Issue, Out-of-Order Completion
Instructions that have no dependencies can be completed with no care for the order in which the rest of the instructions are completed. 

---
### Anti-dependencies
Write-write dependency
1. `r3 = r3 + r5`
2. `r4 = r3 + 1`
3. `r3 = r5 + 1`
4. `r7 = r3 + r4`
i3 cannot complete before i2 starts as i2 needs the value of r3 but i3 changes r3. 
### Register renaming
- Output and anti-dependencies occur because register contents may not reflect the correct ordering from the program. 
- Dynamically allocating registers helps:
`R3b = R3a + R5a`
`R4b = R3b + 1`
`R3c = R5a + 1`
`R7b = R3c + R4b`
- The **completion unit** works out the dependencies and executes instructions in the correct order. Register renaming could make execution 50-100% faster.

### Speculative Execution
If there is a unit free then instructions that *may* be needed - out-of-order execution provides this. 
Speculatively executing code that is not meant to be ran is known as a *meltdown*.

---
![[Pasted image 20241223155848.png]]

**Superscalar Implementation:**
- Simultaneously fetch multiple scalar operations
- Logic to determine true dependencies involving register values
- Mechanisms to initiate multiple instructions in parallel
- Resources for parallel executions
- Mechanisms for executing processes in correct order

Week 3 Friday, as part of [[Computer Architecture]]