2025-10-19T16:58
## Contents
1. A reward $R_t$  is a scalar feedback signal at step t. 
	1. All goals can be describe by the maximisation of expected cumulative reward 
2. At each step t the agent:
	1. Executes action $A_t$
	2. Receives observation $O_t$
	3. Receives scalar reward $R_t$
3. And the environment:
	1. Receives action $A_t$
	2. Emits observation $O_{t+1}$
	3. Emits scalar reward $R_{t+1}$
4. The history is the sequence of observations, actions, rewards
	1. $H_{t} = O_1, R_1, A_1, ...., A_{t-1}, O_{t}, R_{t}$
	2. What happens next depends on the history, the agent selects actions, and the environment selects observations/rewards
5. State is the information used to determine what happens next. $S_t = f(H_t)$
	1. Our job is building useful representation of history (state) such that is helpful to predict the env
6. The information state (Markov state) contains all useful information from the history
	1.  $P[S_{t+1} | S_{t}] = P[S_{t+1} | S_1, ..., S_t]$. Once the state is known, the history might throw away.
7. Markov decision process (MDP), fully observability: Agent state = environment state = information state
8. Partially observable Markov decision process (POMDP) partially observability, agent indirectly observes environments : Agent state not equals to environment state
9. Major components of RL agents
	1. Policy, a mapping function from state to action, e.g. $\pi(a|s) = P[A_t = a | S_t = s]$
	2. Value function is a prediction of future reward, e.g. $v_{\pi}(s) = E_{\pi} [R_{t+1}+\gamma R_{t+2} + \gamma^2 R_{t+3} + ... | S_t= s]$
	3. model predicts what environment will do next
		1. P predicts next state $P^a_{ss'} = P[S_{t+1}=s' | S_t=s, A_t=a]$
		2. R predicts the next/immediate reward $R^a_s = E[R_{t+1}|S_t=s, A_t=a]$
			1. Note: expectation means it considers all possible states for $S_{t+1}$
10. Two fundamental problems in sequential decision making
	1. Reinforcement learning: Environment initially unknown, agent interacts with the env, agent improves policy
	2. Planning: A model of environment is known, agent improves policy
11. Exploration and Exploitation tradeoff
	1. Exploration: find more information about environment
	2. Exploitation: exploits the information to maximize reward.
12. Prediction vs Control
	1. Prediction: Predict future given policy
	2. Control: Find the best value function over all possible policy

## Reference
https://davidstarsilver.wordpress.com/teaching/
https://drive.google.com/file/d/1b6zqn-5b3rieiLHDyi2LCn2-MVNQ4t4b/view?usp=sharing


