**Date time:** 2025-11-26T
## Contents
1. Planning/Prediction by Dynamic Programming (DP)
	1. It must knows the full knowledge of MDP  (S, A, P, R, $\gamma$)
	2. Planning: for a policy $\pi$, a function of action given state, what is the value for that ($v_{\pi}$)
	3. Control: what is the optimal policy $\pi_{*}$ and optimal value function $v_{*}$
2. Policy evaluation: evaluate a given policy $\pi$
	1. iterative application of Bellman expectation backup
		1. $v_{k+1} = \sum_{a \in A} \pi(a|s) (R^a_s + \gamma \sum_{s' \in S} P^a_{ss'}v_k(s'))$
		2. synchronous vs asynchronous backup. Synchronous here means will update all states at each iteration. Asynchronous way only updates the crucial states at each iteration.
		3. Evaluate the policy $\pi$ several iterations -> then improve the policy by acting greedily with respect to $v_{\pi}$, $\pi'=greedy(v_{\pi})$, -> then evaluate policy $\pi'$ several iterations -> .... 
		4. This policy iteration always converges to $\pi_{*}$
3. Principle of Optimality. A policy $\pi(a|s)$ achieves the optimal value from state s, $v_{\pi}(s)=v_{*}(s)$ if and only if 
	1. For any state s' reachable from s
	2. $\pi$ achieves the optimal value from state s', $v_{\pi}(s')=v_{*}(s')$
	3. Use Principle of Optimality to come up with value iteration.
4. Value iteration: if we know the solution to subproblems $v_{*}(s')$, The solution $v_{*}(s)$ can be found by one-step lookahead
	1. $v_{*}(s)=max_{a \in A} R^a_s + \gamma P^a_{ss'}v_{*}(s')$, iterative application of Bellman optimality backup
	2. Relation with policy iteration. If k = 1 in policy iteration (k is the number of iteration in policy evaluation), then policy iteration equals to value iteration.
5. Extension of DP: asynchronous DP. 
	1. In-place value iteration: Only have one copy of value in each state
	2. Priority Sweeping: Use magnitude of Bellman error to guide state selection, and update the state with the largest remaining Bellman error.
	3. Real-time dynamic programming: only update states relevant to the agent at that time
6. Sample Backup: for each backup (either synchronous or asynchronous), every successor state and action is considered. For this, we are using knowledge of MDP transitions and reward function.
	1. For large problems DP suffers Bellman's curse of dimensionality: number of states grows exponentially with the number of states variables. Even one backup can be too expensive.
	2. We can use sample reward and sample transition instead of real reward R and real transition P. We call this model-free

## References
https://davidstarsilver.wordpress.com/teaching/
https://drive.google.com/drive/folders/1F7x3X9PhKb2LbX7GymuNZsR8_xev6gVI?usp=drive_link

