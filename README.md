# aig230_assignment6_TSoward
My submission for AIG 230 Assignment 6 <br>
assignment_part_b_starter.ipynb -> Part B <br>
Assignment6-PartD-PartA.ipynb -> Part D and Part A <br>

Language Modeling Report: Brown 'News' Corpus
## 1. Part A: Trigram Model (NLTK) - Assignment6-PartD-PartA.ipynb
<b>Model:</b> Trigram with Laplace (Add-1) Smoothing.<br>
<b>Smoothing:</b> Necessary to handle the "zero-probability" problem by reallocating probability mass to unseen word sequences, ensuring the model can evaluate new data.<br>
<b>Perplexity:</b> Achieved ~10,000 on the test set. <br>
<b>Findings:</b> Text generation was locally grammatical but "loopy" due to the short 2-word memory horizon.

## 2. Part B: Neural Language Model (RNN/LSTM) - assignment_part_b_starter.ipynb
<b>Architecture:</b> PyTorch LSTM with Embedding (128d) and Hidden (256d) layers.<br>
<b>Training:</b> Optimized using CrossEntropyLoss and Adam over 5 epochs with a seq_len of 30.<br>
<b>Text Generation:</b> Implemented a sampling function with Temperature to control randomness.<br>

## 3. Findings & Comparison
<b>Coherence:</b> Interestingly, the Trigram model produced more coherent local sequences (e.g., "Rhode Island") than the RNN in this specific setup.<br>
<b>RNN Limitations:</b> <br>
<b>Grammar:</b> While recognizable as English, the RNN's sentences lost cohesion quickly and struggled with long-term structure. <br>
<b>Vocabulary:</b> High frequency of the <unk> token made sentences less comprehensible, likely due to the min_freq=2 cutoff in the neural vocabulary.<br>
<b>Logic:</b> The RNN exhibited random behavior, such as listing proper names (e.g., "Homer") without context. <br>
<b>Conclusion:</b> While the RNN has a theoretically longer memory (30 tokens vs. 3), the Trigram model's exact-match probability for common news phrases provided better immediate readability for this dataset size.
