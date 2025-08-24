---
title: Cyclical Learning Rates for Training Neural Networks
date: 2025-08-24
permalink: /posts/2025/08/Cyclical-Learning-Rates-for-Training-Neural-Networks/
tags:
  - deep_learning
  - learning_rate
---

Paper: https://arxiv.org/abs/1506.01186

<div align="center">
  <iframe width="560" height="315" src="https://youtu.be/9-PQ8PZiA_A?si=uLRCjhRrV7HvRsJS" 
  title="YouTube video" frameborder="0" allowfullscreen></iframe>
</div>

It is known that the learning rate is the most important hyper-parameter to tune for training deep neural networks.

**

too small a learning rate will make a training algorithm converge slowly 

while too large a learning rate will make the training algorithm diverge.

Hence, one must experiment with a variety of learning rates and schedules.

**

This paper describes a new method for setting the learning rate, named **cyclical learning rates**, which practically eliminates the need to experimentally find the best values and schedule for the global learning rates. Instead of monotonically decreasing the learning rate, this method lets the learning rate cyclically vary between reasonable **boundary values**. 

Training with cyclical learning rates instead
of fixed values achieves improved classification accuracy
without a need to tune and often in fewer iterations. This
paper also describes a simple way to estimate “reasonable
bounds” – linearly increasing the learning rate of the net-
work for a few epochs.

![clr](/images/clr1.png)
# How it Works

**1.** **Cycle Length:**
	The training process is divided into cycles, each defined by a `step_size` parameter, which is the number of iterations for half a cycle. 

**2.** **Linear Increase:**
    The learning rate begins at a minimum (base) learning rate and increases linearly over a specified number of steps until it reaches a maximum learning rate. 
    
**3.** **Linear Decrease:**
    The learning rate then decreases linearly with the same constant, returning to the minimum learning rate over the next number of steps, completing the triangle shape. 
![clr](/images/clr2.png)
- - - 
An intuitive understanding of why CLR methods work is that the difficulty in minimizing the loss arises from saddle points rather than poor local minima.

Saddle points have small gradients that slow the learning process. 

However, increasing the learning rate allows more rapid traversal of saddle point plateaus.

# **How can one estimate a good value for the cycle length?**

The length of a cycle and the input parameter stepsize can be easily computed from the number of iterations in an epoch. An epoch is calculated by dividing the number of training images by the batchsize used.

accuracy results are actually quite robust to cycle length but experiments show that it often is good to set stepsize equal to 2 − 10 times the number of iterations in an epoch.

# **How can one estimate reasonable minimum and maximum boundary values?**

There is a simple way to estimate reasonable minimum and maximum boundary values with one training run of the network for a few epochs. 

It is a “LR range test”; run your model for several epochs while letting the learning rate increase linearly between low and high LR values. 

This test is enormously valuable whenever you are facing a new architecture or dataset.

![clr](/images/clr3.png)

![clr](/images/clr4.png)


# Conclusion

A short run of only a few epochs where the learning rate linearly increases is sufficient to estimate boundary learning rates for the CLR policies. Then a policy where the learning rate cyclically varies between these bounds is sufficient to obtain near optimal classification results, often with fewer iterations. This policy is easy to implement and unlike adaptive learning rate methods, incurs essentially no additional computational expense.





