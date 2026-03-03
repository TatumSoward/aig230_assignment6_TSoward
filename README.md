# aig230_assignment6_TSoward
My submission for AIG 230 Assignment 6 <br>
assignment_part_b_starter.ipynb -> Part B <br>
Assignment6-PartD-PartA.ipynb -> Part D and Part A <br>

Language Modeling Report: Brown 'News' Corpus
## 1. Part A: Trigram Model (NLTK) - Assignment6-PartD-PartA.ipynb
Model: Trigram with Laplace (Add-1) Smoothing.<br>
Smoothing: Necessary to handle the "zero-probability" problem by reallocating probability mass to unseen word sequences, ensuring the model can evaluate new data.<br>
Perplexity: Achieved ~10,000 on the test set. <br>
Findings: Text generation was locally grammatical but "loopy" due to the short 2-word memory horizon.
## 2. Part B: Neural Language Model (RNN/LSTM) - assignment_part_b_starter.ipynb
Architecture: PyTorch LSTM with Embedding (128d) and Hidden (256d) layers.<br>
Training: Optimized using CrossEntropyLoss and Adam over 5 epochs with a seq_len of 30.<br>
Text Generation: Implemented a sampling function with Temperature to control randomness.<br>
## 3. Findings & Comparison
Coherence: Interestingly, the Trigram model produced more coherent local sequences (e.g., "Rhode Island") than the RNN in this specific setup.<br>
RNN Limitations: <br>
Grammar: While recognizable as English, the RNN's sentences lost cohesion quickly and struggled with long-term structure. <br>
Vocabulary: High frequency of the <unk> token made sentences less comprehensible, likely due to the min_freq=2 cutoff in the neural vocabulary.<br>
Logic: The RNN exhibited random behavior, such as listing proper names (e.g., "Homer") without context. <br>
Conclusion: While the RNN has a theoretically longer memory (30 tokens vs. 3), the Trigram model's exact-match probability for common news phrases provided better immediate readability for this dataset size.
