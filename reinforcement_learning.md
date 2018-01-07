## Reinforcement Learning

### Parameter Space Noise for Exploration [[arXiv 2017]](https://arxiv.org/pdf/1706.01905.pdf)
  - Accompanying blog post(https://blog.openai.com/better-exploration-with-parameter-noise/)
  - Add noise to parameters instead of actions, fix noise for episode: more consistent exploration

### Evolution Strategies as a Scalable Alternative to Reinforcement Learning [[arXiv 2017]](https://arxiv.org/pdf/1703.03864.pdf)
  - Accompanying blog post(https://blog.openai.com/evolution-strategies/)
  - Score Function Gradient (REINFORCE) directly on parameters
  - Ignores all time structure in envs
  - Very parallelizable: many CPUs = fast training
  
### Model-Agnostic Meta-Learning for Fast Adaptation of Deep Networks [[ICML 2017]](https://arxiv.org/pdf/1703.03400.pdf)
  - Objective function is loss after one gradient step; initial weights are optimized
  - Applicable to all models using gradient descent: experiments include sinusoid regression, one-shot image classification, and fast adaptation in RL environments
  - (Meta-)Learned initial weights are sensitive to task identity

### Neural Episodic Control [[ICML 2017]](https://arxiv.org/pdf/1703.01988.pdf)
  - .

### Learning to Play in a Day: Faster Deep Reinforcement Learning by Optimality Tightening [[ICLR 2017]](https://arxiv.org/pdf/1611.01606.pdf)
  - Adds n-step optimality bounds to the Q-learning loss
  - Results in faster information propogation between different Q-values
  - Learns to play Atari games in ~24 hours(~10x speedup compared to DQN)
  
### PGQ: Combining policy gradient and Q-learning [[ICLR 2017]](https://arxiv.org/pdf/1611.01626.pdf)
  - We can estimate Q from policy and value function. Add a Q layer on an Actor-Critic NN, and run Q-Learning on the top layer in addition to the policy gradient update
  - Shows the parallel between the Dueling Network and entropy-regulated Actor-Critic
  
### Q-Prop: Sample-Efficient Policy Gradient with An Off-Policy Critic [[ICLR 2017]](https://arxiv.org/pdf/1611.02247.pdf)
  - Partitions the policy gradient of Actor-Critic into an off-policy part(DPG) and a residual REINFORCE gradient
  - Derived using the linearization of Q as a control variate
  
### Sample Efficient Actor-Critic with Experience Replay [[ICLR 2017]](https://arxiv.org/pdf/1611.01224.pdf)
  - Partitions the policy gradient of Actor-Critic into a stable off-policy part(Retrace) and its on-policy residual
  - Achieves better sample efficiency by using experience replay on the off-policy component 

### Unifying Count-Based Exploration and Intrinsic Motivation [[NIPS 2016]](https://arxiv.org/pdf/1606.01868v2.pdf)
  - Introduces 'pseudo-count': an approximation to count from an arbitrary density model
  - Pseudo-count enables us to use count based algorithms on large or continuous state space MDPs
  - Explores Montezuma's Revenge effectively(!)
  
### Mastering the game of Go with deep neural networks and tree search [[Nature 2016]](http://www.nature.com/nature/journal/v529/n7587/pdf/nature16961.pdf)
  - Use RL to play Go
  - Core algorithm is Monte Carlo Tree Search using a trained policy network to get action probabilities
  - Leaf nodes are evaluated using both a fast rollout policy network and a trained value network
  
### Asynchronous Methods for Deep Reinforcement Learning [[ICML 2016]](https://arxiv.org/pdf/1602.01783v2.pdf)
  - Suggests A3C(Asynchronous Advantage Actor-Critic), which is the standard Actor-Critic algorithm run by many instances in parallel
  - Surpasses current state-of-the-art in shorter time using a CPU
  
### Dueling Network Architectures for Deep Reinforcement Learning [[ICML 2016]](https://arxiv.org/pdf/1511.06581.pdf)
  - Two-stream DQN, each stream representing V (value function) and A (advantage function)
  - Eliminates the instability of adding two numbers of different scale(V is usually much larger than A)
  - By updating multiple Q values on each observation, effectively updates more frequently than a single-stream DQN
  - Implicitly splits the credit assignment problem into a recursive binary problem of "now or later"
  
### Deep Exploration via Bootstrapped DQN [[NIPS 2016]](https://arxiv.org/pdf/1602.04621v3.pdf)
  - Bootstraps DQN heads with shared lower layers
  - Results in more consistent('deep') exploration

### Continuous Control with Deep Reinforcement Learning [[ICLR 2016]](https://arxiv.org/pdf/1509.02971)
  - Videos available [here](https://goo.gl/J4PIAz)
  - Suggests DDPG, which improves the actor-critic algorithm in [Deterministic Policy Gradient Algorithms](https://github.com/yoonholee/Reinforcement-Learning-Survey/blob/master/policy_gradient.md#deterministic-policy-gradient-algorithms-icml-2014) by using a DQN as the critic
  
### High-dimensional Continuous Control Using Generalized Advantage Functions [[ICLR 2016]](https://arxiv.org/pdf/1506.02438)
  - Derives a class of estimators(GAE) of the advantage function, parameterized by two real numbers in [0,1]
  - Empirical performance of TRPO+GAE is better than TRPO in some tasks
  
### Connecting Generative Adversarial Networks and Actor-Critic Methods [[arxiv 2016]](https://arxiv.org/pdf/1610.01945v2.pdf)
  - Constructs an Actor-Critic architecture that is equivalent to GAN: randomly choose state between a real image and an image generated by the actor, action is setting every pixel in an image. Real image: reward 1, Synthetic image: reward 0
  - Cross-examines the approaches used to stabilize GANs and AC architectures
  
### Deep Reinforcement Learning with Double Q-Learning [[AAAI 2016]](https://arxiv.org/pdf/1509.06461.pdf)
  - Points out that once [DQN](https://github.com/yoonholee/Reinforcement-Learning-Survey/blob/master/q_learning.md#playing-atari-with-deep-reinforcement-learning-nips-2014-deep-learning-workshop) overestimates a Q value, the overestimation 'spills over' to states that precede it
  - Uses different Q networks for action selection and evaluation
  
### Action-Conditional Video Prediction using Deep Networks in Atari Games [[NIPS 2015]](https://arxiv.org/pdf/1507.08750v2.pdf)
  - Constructs a NN that predicts the next frame of an Atari game given the current frame and action
  - Exploration using predicted frames marginally increases score
  
### Human-level Control Through Deep Reinforcement Learning [[Nature 2015]](http://home.uchicago.edu/~arij/journalclub/papers/2015_Mnih_et_al.pdf)
  - Proposes using a deep neural network with Bellman backup as regression target
  - Uses three tricks for stability: separate prediction/target networks, experience replay, reward clipping
  - Points out that a scheme similar to experience replay happens in the hippocampus of the mammalian brain
  
### Trust Region Policy Optimization [[ICML 2015]](https://arxiv.org/pdf/1502.05477)
  - Builds on [Approximately Optimal Approximate Reinforcement Learning](https://github.com/yoonholee/Reinforcement-Learning-Survey/blob/master/policy_gradient.md#approximately-optimal-approximate-reinforcement-learning-icml-2002)
  - Instead of using a linear mixture, TRPO uses average KL divergence to ensure that the next policy is sufficiently close to current policy(in practice, approximate L linearly and KL divergence quadratically)
  - The natural policy gradient has the same direction as TRPO; the difference is that TRPO chooses a step size based on the trust region defined by KL divergence
  
### Deterministic Policy Gradient Algorithms [[ICML 2014]](http://jmlr.org/proceedings/papers/v32/silver14.pdf)
  - Derives a gradient for deterministic policies(assuming a continuous action space)
  - Proves(under mild regularity conditions) that all previously developed machinery for stochastic policy gradients(i.e. compatible function approximation, actor-critic, natural gradients, and episodic/batch methods) apply to deterministic policy gradients.
  - All proofs are in [a separate document](http://jmlr.org/proceedings/papers/v32/silver14-supp.pdf)

### Reinforcement learning of motor skills with policy gradients [[Neural Networks 2008]](http://is.tuebingen.mpg.de/fileadmin/user_upload/files/publications/Neural-Netw-2008-21-682_4867[0].pdf)
  - An extensive survey of policy gradient methods
  - Covers naive finite-difference methods, REINFORCE, NAC(Natural Actor-Critic)
  - NAC is shown to be the state of the art
  
### Natural Actor-Critic [[Neurocomputing 2008]](http://ac.els-cdn.com/S0925231208000532/1-s2.0-S0925231208000532-main.pdf?_tid=5001927e-69ce-11e6-87f9-00000aacb35f&acdnat=1472024730_f49e79f185266d4824826941cec13967)
  - Proves that the weight vector discussed in [A Natural Policy Gradient](https://github.com/yoonholee/Reinforcement-Learning-Survey/blob/master/policy_gradient.md#a-natural-policy-gradient-nips-2002) is actually the natural gradient, rather than just a gradient defined by an average of point Fisher information matrices
  - Suggests an Actor-Critic style algorithm using the natural gradient
  
### A Natural Policy Gradient [[NIPS 2002]](http://papers.nips.cc/paper/2073-a-natural-policy-gradient.pdf)
  - Parameterizes Q(s,a) as a weighted sum of log p(a|s)
  - Proves that the weight vector(above) is the direction of steepest descent w.r.t. the expectation of the Fisher information matrix(natural policy gradient)
  - Suggests a REINFORCE-style algorithm using the natural gradient
 
### Approximately Optimal Approximate Reinforcement Learning [[ICML 2002]](https://www.cs.cmu.edu/~./jcl/papers/aoarl/Final.pdf)
  - Points out the inefficiency of policy gradients using two example MDPs(section 3.2)
  - Derives a conservative policy iteration scheme that finds a policy that is almost optimal(within epsilon) in polynomial(w.r.t. epsilon) time
  - The key idea is that we can get a provably improved policy by using a linear mixture between the current policy and the greedily improved policy

### Convergence of Stochastic Iterative Dynamic Programming Algorithms [[NIPS 1994]](http://papers.nips.cc/paper/764-convergence-of-stochastic-iterative-dynamic-programming-algorithms.pdf)
  - Proves the convergence of Q-Learning to optimal Q values given some mild regulatory conditions
  - Gives a similar proof for TD(lambda)
