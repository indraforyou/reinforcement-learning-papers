# Reinforcement Learning Survey

This is a collection of my notes on reinforcement learning papers.

Typo corrections, additional points, new papers etc are all very welcome. You can either make a pull request or email me at einet89[at]postech.ac.kr


## Table of Contents

- [Policy Gradient](https://github.com/yoonholee/Reinforcement-Learning-Survey#policy-gradient)


## Policy Gradient

### Approximately Optimal Approximate Reinforcement Learning [[ICML 2002]](https://www.cs.cmu.edu/~./jcl/papers/aoarl/Final.pdf)
  - Sham Kakade, John Langford
  - Points out the inefficiency of policy gradients using two example MDPs(section 3.2)
  - Derives a conservative policy iteration scheme that finds a policy that is almost optimal(within epsilon) in polynomial(w.r.t. epsilon) time
  - The key idea is that by using a mixture between the current policy and a greedily improved policy, we can prove that the value function improves.

### A Natural Policy Gradient [[NIPS 2002]](http://papers.nips.cc/paper/2073-a-natural-policy-gradient.pdf)
  - Sham Kakade
  - Parameterizes Q(s,a) as a weighted sum of log p(a;s)
  - Proves that the weight vector(above) is the direction of steepest descent with respect to the expectation of the fisher information matrix(natural policy gradient)
  - Implicitly shows(first line of Theorem 3 proof) that the natural policy gradient is a linear approximation of policies with respect to policy parameters
  - Suggests a REINFORCE-style algorithm using the natural gradient
  
### Natural Actor-Critic [[Neurocomputing 2008]] (http://ac.els-cdn.com/S0925231208000532/1-s2.0-S0925231208000532-main.pdf?_tid=5001927e-69ce-11e6-87f9-00000aacb35f&acdnat=1472024730_f49e79f185266d4824826941cec13967)
  - Jan Peters, Stefan Schaal
  - Proves that the weight vector discussed in [A Natural Policy Gradient](https://github.com/yoonholee/Reinforcement-Learning-Survey#a-natural-policy-gradient) is in fact the natural gradient, rather than just a gradient defined by an average of point fisher information matrices
  - Suggests a actor-critic style algorithm using the natural gradient

### Reinforcement learning of motor skills with policy gradients [[Neural Networks 2008]](http://is.tuebingen.mpg.de/fileadmin/user_upload/files/publications/Neural-Netw-2008-21-682_4867[0].pdf)
  - Jan Peters, Stefan Schaal
  - An extensive survey of policy gradient methods
  - Covers naive finite-difference methods, REINFORCE, NAC(natural actor-critic)
  - NAC is shown to be the state of the art
  
### Deterministic Policy Gradient Algorithms [[ICML 2014]](http://jmlr.org/proceedings/papers/v32/silver14.pdf)
  - David Silver, Guy Lever, Nicolas Heess, Thomas Degris, Daan Wierstra, Martin Riedmiller
  - All proofs are in [a seperate document](http://jmlr.org/proceedings/papers/v32/silver14-supp.pdf)
  - Derives a gradient for deterministic policies(assuming a continuous action space)
  - Proves(under mild regularity conditions) that all previously developed machinery for stochastic policy gradients(i.e. compatible function approximation, actor-critic, natural gradients, and episodic/batch methods) are applicable to determinisic policy gradients.
  - Derives deterministic policy gradient algorithms using such machinery

### Continuous Control with Deep Reinforcement Learning [[ICLR 2016]](https://arxiv.org/pdf/1509.02971)
  - Google Deepmind(Timothy P. Lillicrap, Jonathan J. Hunt, Alexander Pritzel, Nicolas Heess, Tom Erez, Yuval Tassa, David Silver, Daan Wierstra)
  - Videos available [here](https://goo.gl/J4PIAz)
  - Suggests DDPG, which improves the actor-critic algorithm in [Deterministic Policy Gradient Algorithm](https://github.com/yoonholee/Reinforcement-Learning-Survey#deterministic-policy-gradient-algorithms) by using a DQN as the critic
  - Empirically shown to be far more efficient than DQN

### Trust Region Policy Optimization [[ICML 2015]](https://arxiv.org/pdf/1502.05477)
  - John Schulman, Sergey Levine, Philipp Moritz, Michael Jordan, Pieter Abbeel
  - 
