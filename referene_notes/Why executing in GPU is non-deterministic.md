2025-09-16T21:39
## Contents
1. Floating-point is non-associativity
	1. a + (b + c) != (a+ b) + c
	2. This happens when the range of number are different. For example, if a = 1.23 * 10^3, b= 2.34 * 10^1, and if we allow for two mantissas, then a + b = 1.24 * 10^3 . The last two digits are dropped.
2. Atomic add:  GPU executes thing concurrently, and the performs add atomically. In this way the order of add (reduction) is non-deterministic. This is a non-deterministic reduction.
3. However, modern deep learning applications usually run parallel on data-batch axis and don't run parallel on the axis that needs reduction. Also, the modern libraries usually implement their deterministic reduction.
4. The reason why current LLM inference endpoints are non-deterministic is that it is not batch-invariant, and the batch size is non-deterministic.
5. After making RMS-norm, matrix multiplication, and attention batch-invariant, the LLM inference endpoints can be deterministic.
	1. All these operations (RMS-norm, matrix multiplication, and attention) has some operations that are nondeterministic parallel reduction. This makes them nondeterministic

## Reference

https://thinkingmachines.ai/blog/defeating-nondeterminism-in-llm-inference/
