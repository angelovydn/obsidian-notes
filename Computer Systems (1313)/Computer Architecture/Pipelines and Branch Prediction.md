**Pipelining** is the process of performing the Fetch, Decode and Execute cycle at different stages simultaneously. For example, you can be decoding the previous instruction whilst fetching the following instruction.

Branches cause pipeline "stalls" as new instructions have to be dealt with.
- Multiple streams
- Prefetch branch target
- Loop buffer
- Branch prediction
- Delayed branching

Multiple streams:
- have two pipelines
- prefetch each branch into a separate pipeline, use the appropriate one
- leads to bus and register contention - multiple values attempt to be stored simultaneously

Prefetch branch target:
- Target of branch is prefetched in addition to instructions' following branch
- Keep target until branch is executed

Loop buffer - intel:
- Very fast memory stores last n instructions (ie. for loop)
- Maintained by fetch stage
- Very good for small loops

Branch Prediction, static:
- Prediction 1: assume jump will never happen; always fetch next instruction
- Prediction 2: assume jump will always happen; always fetch target

Branch Prediction:
- Predict by Opcode: some instructions are more likely to result in a jump
- Taken/not taken switch: based on previous history, good for loops

**I**ntel **A**rchitecture: IA-34 IA-64
- Very sophisticated branch prediction
- Speculative execution: executes instructions beyond branch in case it is used
- Retirement unit looks at what it can complete

Pipelines are designed to complete an instruction each clock.
Branches can cause wasted effort in pipelines as the wrong instruction can be worked on.
Branch prediction units can be >90% accurate in the real world.

Week 2 Friday, as part of [[Computer Architecture]]