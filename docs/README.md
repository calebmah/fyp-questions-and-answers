# Final Year Project Blog

## GitHub
[Work in progress GitHub link](https://github.com/calebmah/ggnn.pytorch)

## Todo List

### Papers
- [x] Read [Gated Graph Sequence Neural Networks](https://arxiv.org/pdf/1511.05493.pdf) by Yujia Li, Daniel Tarlow, Marc Brockschmidt, Richard Zemel
- [x] Read accompanying [presentation slides](https://katefvision.github.io/LanguageGrounding/Slides/27.pdf)
- [x] Read [Residual Gated Graph ConvNets](https://arxiv.org/pdf/1711.07553.pdf) by Xavier Bresson, Thomas Laurent
- [ ] Read [Learning Conditioned Graph Structures for Interpretable Visual Question Answering](https://arxiv.org/pdf/1806.07243.pdf) by Will Norcliffe-Brown, Efstathios Vafeias, Sarah Parisot to check relevance
- [ ] Read [Towards AI-Complete Question Answering: A Set of Prerequisite Toy Tasks](https://arxiv.org/pdf/1502.05698.pdf) by Jason Weston, Antoine Bordes, Sumit Chopra, Alexander M. Rush, Bart van Merriënboer, Armand Joulin, Tomas Mikolov to check relevance.
- [ ] Read [A new model for learning in graph domains](https://ieeexplore.ieee.org/document/1555942/)

### Websites
- [x] Read [Question answering on the Facebook bAbi dataset using recurrent neural networks and 175 lines of Python + Keras](https://smerity.com/articles/2015/keras_qa.html)

### Code
- [ ] Read, and understand [GGNN code](https://github.com/yujiali/ggnn)
- [x] Fork, Read, and understand [PyTorch GGNN Code](https://github.com/JamesChuanggg/ggnn.pytorch)
- [x] Fork, read, and understand [RGGC code](https://github.com/xbresson/spatial_graph_convnets)

## 1 Mar 2019

### Progress
- [x] Updated model to handle graphs of with multiple edge types by labelling edges (1, 2, 3, etc.)
- [x] Ran experiments using RGGC on all available tasks again, results below:

| Task ID | GGNN | RGGC |
| --- | --- | --- |
| 1 | 45%| 47%|
| 2 | 32%| 42%|
| 4* | 100%| 55%|
| 9 | 16%| 38%|
| 11 | 32%| 33%|
| 12 | 28%| 30%|
| 13 | 29%| 27%|
| 15* | 100%| 74%|
| 16* | 100%| 100%|
| 17 | 9%| 16%|
| 18* | 29%| 28%|

- The above experiments with RGGC were done with the same training parameters as before. (training data = 50, learning rate = 0.01, epochs = 10, propagation steps = 5, batch size = 1)

### Next steps
- Optimize code for cuda gpu processing (currently cpu faster than gpu)
- Perform more in depth experiments with different hyperparameters
- Update implementation to handle batch sizes larger than 1.
- Fix preprocessing code to remove incorrect data.

## 14 Feb 2019

### Progress
- [x] Completed and submitted Interim Report
- [x] Further examining of GGNN and RGGC code.
- [x] Implemented RGGC for bAbi tasks 1, 2, 11, 12, 13, 18.
- [x] Ran initial experiments using RGGC, results below.

| Task ID | GGNN | RGGC |
| --- | --- | --- |
| 1 | 45%| 47%|
| 2 | 32%| 43%|
| 4* | 100%| - |
| 9 | 16%| - |
| 11 | 32%| 36%|
| 12 | 28%| 28%|
| 13 | 29%| 26%|
| 15* | 100%| - |
| 16* | 100%| - |
| 17 | 9%| - |
| 18* | 29%| 29%|

- The above experiments with RGGC were done with the same training parameters as the experiments with GGNN. (training data = 50, learning rate = 0.01, epochs = 10, propagation steps = 5)
- Batch size is the only exception. GGNN were trained with batch size = 10 while RGGC were trained with batch size = 1. This is a limitation of the current implementation of RGGC experiments.

### Notes

The RGGC experiments were only conducted for tasks 1, 2, 11, 12, 13, 18 because they are the only available tasks with only one edge type. The image below shows samples from each of these tasks. The current implementation is limited in that it can only operate on graphs with a single edge type.

![Sample of tasks with one edge type](http://calebmah.me/fyp-questions-and-answers/images/sample_1edge.png)

Comparing the results, we observe that RGGCs perform generally similar to GGNNs, with only marginal performance improvements in some tasks. This could possibly be attributed to an error in the preprocessing of the dataset. Since positional order in a story for each task is not preserved, there may be data that is incorrect because the data depends upon the sequence in which it was applied. For example in the data below, questions are asked after every 2 facts, but are consolidated at the bottom after preprocessing.

```
1 1 2
3 1 4
5 1 2
1 1 4
5 1 6
5 1 7
1 1 2
1 1 8
1 1 9
5 1 8
? 1 1 2
? 1 5 2
? 1 5 7
? 1 3 4
? 1 3 4
```
### Summary of issues for RGGC
- Batch size limited to 1, have to generate E_start and E_end for batches.
- Only works when there is 1 edge type. Need to find a way to include multiple edge types.
- Error in preprocessing data.

### Questions
- How to best resolve tasks with multiple edge types? Use same adjacency matrix with different numbers or use different adjacency matrices altogether?
- How to best handle sequence data with RGGCs?

### Next steps
- Fix minor bug in current implementation that prevents cuda
- Update implementation to include remaining tasks with more than 1 edge type.
- Update implementation to handle batch sizes larger than 1.
- Fix preprocessing code to remove incorrect data.

## 25 Jan 2019

### Progress
- [x] Fork, read, and understand [RGGC code](https://github.com/xbresson/spatial_graph_convnets)
- [x] Read deeper and understand both papers ([Gated Graph Sequence Neural Networks](https://arxiv.org/pdf/1511.05493.pdf) and [Residual Gated Graph ConvNets](https://arxiv.org/pdf/1711.07553.pdf)) and accompanying code
- [x] Replicate RGGC experiments
- [x] Begin integrating RGGC code into PyTorch GGNN Code
- [x] Read [Question answering on the Facebook bAbi dataset using recurrent neural networks and 175 lines of Python + Keras](https://smerity.com/articles/2015/keras_qa.html)

### Issues
- Task 18 is reported to obtain 100% accuracy using GGNN. Replicating the experiment yielded much lower accuracy of 29%. This is because for task 18, a different graph level classification version is used instead of a node selection GGNN. This version is not implemented in the PyTorch implementation.
- Similarly, task 19 (path evaluation) uses a GGSNN dealing with sequences, which is not implemented in the PyTorch implementation.

### Questions
- In RGGC code example, why does each convnet cell use two conv operations?
- Generally more advisable to adapt RGGC structure to GGNN code or adapt GGNN data to RGGC code?
- Does RGGC code allow for edge labels or edges of different types?

### Next steps
- Get best performance for GGNN code using grid search (learning rate, training size, hidden state size, training epochs) (maybe)
- Continue integrating RGGC code into PyTorch GGNN Code

## 5 Nov 2018

### Progress
- Generated symbolic bAbi dataset for experiments
- Ran experiments on dataset, results shown below.

| Task ID | Test Accuracy |
| --- | --- |
| 1 | 45%|
| 2 | 32%|
| 4* | 100%|
| 9 | 16%|
| 11 | 32%|
| 12 | 28%|
| 13 | 29%|
| 15* | 100%|
| 16* | 100%|
| 17 | 9%|
| 18* | 29%|

- Note: All training done with learning rate = 0.01, epochs = 10, propagation steps = 5.
- Note: Tasks with no results require further preprocessing or data generation.

### Next steps
- Implement RGGC Code for bAbi Tasks
- Compare results


## 22 Oct 2018

### Progress
- [x] Read, and understand [PyTorch GGNN Code](https://github.com/JamesChuanggg/ggnn.pytorch), especially preprocessing code.
- Attempted to conduct experiments for other 20 bAbi tasks, but facing some issues getting the dataset.

### Issues
- Current code uses the symbolic form of the bAbi dataset, which is generated with torch (lua), which is not supported on windows.
- Looking at other ways of obtaining the dataset online or through a VM.

## 8 Oct 2018

### Progress
- [x] Read [Residual Gated Graph ConvNets](https://arxiv.org/pdf/1711.07553.pdf) by Xavier Bresson, Thomas Laurent
- [x] Forked [PyTorch GGNN Code](https://github.com/JamesChuanggg/ggnn.pytorch)
- [x] Replicated experiments from [GGNN paper](https://arxiv.org/pdf/1511.05493.pdf) for bAbi tasks 4, 15 and 16. Need to edit code to replicate results for tasks 18 and 19.

### Questions
- Clarify difference between layers l and timesteps t.
- Not very clear what it means to apply a ConvNet to graphs. Only look at feature vector of neighboring nodes and itself?

## 24 Sep 2018

### Progress
- [x] Read [Gated Graph Sequence Neural Networks](https://arxiv.org/pdf/1511.05493.pdf) by Yujia Li, Daniel Tarlow, Marc Brockschmidt, Richard Zemel
- [x] Read accompanying [presentation slides](https://katefvision.github.io/LanguageGrounding/Slides/27.pdf)
- [x] Forked [GGNN code](https://github.com/yujiali/ggnn)

#### Added to Todo List
- [ ] Read [A new model for learning in graph domains](https://ieeexplore.ieee.org/document/1555942/)

### Questions
- What exactly is the difference between node annotations (X) and node representations (H)?
- Is the previous node representation hv (t-1) used in the propagation model or just the neighbors?
- How to best run code? (Torch not supported on windows, currently using VM, consider online)

## 10 Sep 2018

### Project Overview

The goal of this project is to develop and evaluate a convolutional neural network algorithm to generate questions and answers. In particular, the algorithm will be evaluated using the benchmark [bAbi dataset](https://research.fb.com/downloads/babi/).

Two main methods for generating questions and answers will be compared:
1. [Gated Graph Sequence Neural Networks](https://arxiv.org/pdf/1511.05493.pdf) by Yujia Li, Daniel Tarlow, Marc Brockschmidt, Richard Zemel
2. [Residual Gated Graph ConvNets](https://arxiv.org/pdf/1711.07553.pdf) by Xavier Bresson, Thomas Laurent

The first method has been applied to question and answer generation, whereas the second approach using Residual Gated Graph ConvNets proposes a new approach for tasks involving graph learning. The primary challenge for this project will be to apply this approach to the generation of questions and answers.

### Progress

- Created [github repository](https://github.com/calebmah/fyp-questions-and-answers)
- Created this blog
- Completed project plan
