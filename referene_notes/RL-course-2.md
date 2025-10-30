2025-10-26T16:32
## Contents
1. Markov Process is a memoryless random process, is a tuple (S, P): S is a finite set of states, and P is the state transition probability matrix $P_{ss'} = P[S_{t+1}=s' | S_t = s]$
2. Markov Reward Process
	1. A Markov Reward Process is a Markov chain with values, is a tuple (S, P, R, $\gamma$) 
	2. R is immediate reward is how much I get from the state at that moment. $R_s = E[R_{t+1}|S_t = s]$. Note this formula is confusing, the $R_{t+1}$ is actually the immediate reward I get from $S_t$. And it seems Expectation is redundant here. It might be this formula is defined for next reward, not immediate reward. 
	3. discount factor $\gamma \in [0, 1]$
		1. why discount function? Mathematically convenient, Avoid infinite returns, uncertainty about the future may not fully represented by models, financially makes sense, like animal/human behavior.
	4. The return $G_t = R_{t+1} + \gamma R_{t+2} + ...=\sum_{k=0}^{\inf} r^k R_{t+k+1}$
	5. Value function gives the long-term value of state s $v(s) = E[G_t |S_t=s]$ 
3. Bellman Equation for MRPs
	1. Use Law of total expectation to proof $E[X] = E[E[X|Y]]$
	2. $v(s)=E[G_t|S_t=s]=E[R_{t+1}+\gamma v(S_{t+1})|S_t=s]=R_s + r \sum_{s\in S} P_{ss'}(v(s'))$ 
	3. One step look-ahead to iteratively compute value function. For state at t time, compute Expected value, summation of each possible next state's probability times the each's value, then plus the expected value with the value of the state t.
	4. matrix formulation $v = R + rPv$, where $v$ is a vector of value of state 1 to state n.
4. Markov Decision Process
	1. A Markov Decision Process is a Markov reward process with decisions, is a tuple (S, A, P, R, $\gamma$), A is the finite set of actions
	2. P becomes $P^a_{ss'}=P[S_{t+1}=s'|S_t=s, A_t=a]$, R becomes $R_s^a=E[R_{t+1}|S_t=s, A_t=a]$
	3. A policy $\pi(a|s) = P[A_t=a|S_t=s]$, is a distribution over actions given states
	4. With policy, P becomes $P^{\pi}_{ss'} = \sum_{a \in A} \pi (a|s) P^a_{ss'}$, and R becomes $R^{\pi}_s=\sum_{a \in A} \pi(a|s) R^a_s$
	5. The state-value function $v_{\pi}(s)= E_{\pi} [G_t | S_t=s]$, is the expected return starting from state s, and then following policy $\pi$
	6. The action-value function $q_{\pi}(s, a)=E_{\pi}[G_t|S_t=s, A_t=a]$, is the expected return starting from state s, taking action a, and then following policy $\pi$
5. Bellman Expectation for MDP
	1. $v_{\pi}(s)=E_{\pi} [R_{t+1}+\gamma v_{\pi}(S_{t+1}) | S_t=s] =\sum_{a\in A}\pi (a|s) q(s, a)$
	2. $q_{\pi}(s, a)=E_{\pi}[R_{t+1}+\gamma q_{\pi}(S_{t+1}, A_{t+1})|S_t=s, A_t=a]=R^a_s + \gamma \sum_{s'\in S}P^a_{ss'}v_{\pi}(s')$. After executing action a, the environment makes agent to state $s'$, based on $P^a_{ss'}$
	3. Combine 1, 2, $v_{\pi}(s)=\sum_{a\in A}\pi(a|s)(R^a_s + \gamma \sum_{s'\in S}P^a_{ss'}v_{\pi}(s'))$
	4. Combine 1, 2, $q_{\pi}(s,a)=R^a_s + \gamma \sum_{s'\in S}P^a_{ss'}\sum_{a'\in A}\pi (a'|s') q(s', a')$
6. Optimal Policy for MDP
	1. Theorem. There exists an optimal policy $\pi_*$ that is better than or equal to all other policies, $\pi_* \geq \pi, \forall \pi$. All optimal policies $\pi_*$ achieve the optimal value function $v_{\pi_*}(s) = v_*(s)$. All optimal policies achieve the optimal action-value function $q_{\pi*}(s,a) = q_* (s, a)$
	2. An optimal policy can be found by maximising over $q_* (s, a)$, $\pi_* (a|s) = 1$ if $a=argmax_{a \in A} q_* (s, a)$; otherwise $\pi_* (a|s) = 0$
	3. If we know $q_* (s, a)$, we immediately know the optimal policy
7. Bellman Optimality for $v_*$, $Q^*$
	1. $v_*(s)=max_a q_* (s, a)$
	2. $q_*(s,a) = R^a_s + \gamma \sum_{s' \in S}P^a_{ss'}v_*(s')$
	3. combine 1, 2, $v_*(s)=max_a R^a_s + \gamma \sum_{s' \in S}P^a_{ss'}v_*(s')$
	4. combine 1, 2, $q_*(s,a)=R^a_s + \gamma \sum_{s' \in S} P^a_{ss'} max_a q_*(s',a')$
	5. 

## Reference

https://davidstarsilver.wordpress.com/teaching/
https://drive.google.com/drive/recent?dmr=1&ec=wgc-drive-hero-goto