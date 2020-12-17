# Review

## Info

Reviewer Name: Tiancheng Xu  
Paper Title: Nested Kernel: An Operating System Architecture for Intra-Kernel Privilege Separation

## Summary
The paper proposes and implements Nested Kernel operating system, which provides privilege separation and isolation within a monolithic by virtualizing the MMU. 

### Problem and why we care
Isolation and protection are of great significance. Least privilege is an important design principle to achieve the goal. However, existing designs fail to provide a satisfying solution: monolithic kernels form a single TCB, which fails to enforce least privilege; other existing OSes, such as microkernels, completely give up the monolithic design, which requires significant amount of OS re-design and implementation. The research problem of how to enforce least privilege within existing monolithic kernel designs is thus very important. 

### Gap in current approaches
Existing OSes either fail to enforce least privilege, or completely abandons the monolithic designs. This is the first work to approach the problem of enforcing least privilege within a monolithic kernel. 

### Hypothesis, Key Idea, or Main Claim
Key idea: the key to enforcing least privilege (and thus enforce isolation and protection) is to ensure safe memory accesses. The key approach towards this goal is to virtualize the MMU. By doing so, the proposed design is able to enforce a set of novel policies to protect resources (pages) and address translation mappings, thus ensure the safety of memory accesses. 

### Method for Proving the Claim
The work presents a protetype implementing the nested kernel architecture, i.e., the PerspicuOS. It is demonstrated that, by designing and implementing the OS in the proposed way, all the security invariants can be guaranteed. 

### Method for evaluating
The effort of porting FreeBSD to a nested kernel design is evaluated in terms of lines of code needed. 
The protection for privilege isolation (defense against privilege boundary crossings) is evalulated using micro-benchmarks. 
Performance overheads are evaluated on both micro-benchmarks and application benchmarks. 

### Contributions: what we take away
The design and implementation to enforce intra-kernel isolation and protection within a monolithic kernel design. It is shown in the work that this goal can be achieved with a small set of hardware functionality changes. 

## Pros (3-6 bullets)
- Novelty. The work is the first of its kind to provide intra-kernel isolation and protection within existing monolithic kernel designs.
- Solid implementation: a prototype OS is implemented and open-sourced. 
- The introduction and background sections are well-written, the problems are clearly stated. 

## Cons (3-6 bullets)
- Evaluation could be more comprehensive, e.g., it could be evaluated on more benchmarks, more factors (e.g., execution latency) could be evaluated. 
- The third section (PerspicuOS: A Nested Kernel Prototype) and fourth section (Enforcing Intra-Kernel Security Policies) could use more context and examples for illustration purposes. 

### What is your analysis of the proposed?
Novel, interesting and practical solution to an important problem. 

## Details Comments, Observations, Questions
Discussion questions used in the class:  
- What is unique about Nested Kernel? 
- Minimal set of hardware functionalities: why MMU? 
- What assumptions are made? Are they reasonable? For example, anything about threat model? Is the hardware reliable? Hardware specification: x86 architecture? 
- “Single address space between trusted and untrusted components”. Is it good? Why? 
- Are the write-protection policies enough? 
- Is there any trade-off in the design? Literally any. 
- Are evaluation methodologies sound enough? 
- Any implementation choice you think you wouldn’t do or would do differently? 
- (*) Could you come up with an attack that invalidates the protection? 

