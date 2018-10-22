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
- [ ] Read [Question answering on the Facebook bAbi dataset using recurrent neural networks and 175 lines of Python + Keras](https://smerity.com/articles/2015/keras_qa.html)

### Code
- [ ] Read, and understand [GGNN code](https://github.com/yujiali/ggnn)
- [x] Read, and understand [PyTorch GGNN Code](https://github.com/JamesChuanggg/ggnn.pytorch)
- [ ] Fork, read, and understand [RGGC code](https://github.com/xbresson/spatial_graph_convnets)

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
