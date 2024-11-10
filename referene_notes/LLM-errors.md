# LLM error detection with probing
- The paper refers to all types of hallucinations as errors rather than categorizing them.
- It proposes using probing (training a classifier on the internal state of a layer-token pair) to detect these errors.
- The study finds that training a probing classifier on the "exact answer token" (the critical token for answer correctness) accurately predicts answer correctness.
- The classifier’s performance does not generalize well across different datasets, suggesting task-specific internal representations.
- Errors are categorized into types, including "refused to answer," "almost correct," "almost incorrect," "many answers," and "two competing answers," with the classifier accurately detecting these types.
- The probing classifier can improve accuracy in uncertain cases (e.g., competing answers), implying that while LLMs encode correct information, they may still generate incorrect answers, potentially addressable with improved sampling methods (this part is my thought).
# Ref
LLMS KNOW MORE THAN THEY SHOW: ON THE INTRINSIC REPRESENTATION OF LLM HALLUCINATIONS