# Final Year Project Blog

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
