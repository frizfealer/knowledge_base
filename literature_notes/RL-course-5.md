2025-12-08T19:52
## Contents
1. Model-free control: Don't know the environments, but want to find the optimal policy
	1. Many problems can be modeled as MDPs; but either we don't know the MDP model, or the model is too big to use. Instead we usually can sample experience.
2. On-policy learning: Learn about policy $\pi$ from experience sampled from $\pi$. Off-policy learning: Learn about $\pi$ from experience sampled from $\mu$
3. Generalized policy iteration
	1. When improving policy on value function $V(s)$, $\pi^{'}(s)=argmax_{a \in A} R^a_s + P^a_{ss'} V(s')$, that requires models of MDP.
	2. Instead we have greedy policy improvement over $Q(s,a)$ (model-free), $\pi^{'}(s)=argmax_{a\in A} Q(s,a)$
		1. Policy evaluation: Monte-Carlo policy evaluation. 
		2. We can update the Q function evaluation for any states/actions with only one episode to make update faster.
	3. When improving policy, to avoid stuck in local optimal, we do $\epsilon$ greedy instead. That is we randomly choose an action with probability $\epsilon$, and we act greedy with probability $1-\epsilon$
			1. $\epsilon$-greedy is GLIE if $\epsilon$ reduces to zero at $\epsilon_k=\frac{1}{k}$ (k episode)
			2. GLIE first statement: all state-action pairs are explored infinitely many times
			3. GLIE second statement: The policy eventually converges on a greedy policy
	4. Using Temporal-difference (TD) instead of MC, motivation
		1. low variance, online (means update per time-step), incomplete sequence
		2. Sarsa: $Q(S, A) \leftarrow Q(S,A) + \alpha(R + \gamma Q(S', A') - Q(S,A))$
		3. Substitute MC with Sarsa
4. n-Step Sarsa, as in TC in prediction problem, we can also define
	1. $q_t^{(n)}=R_{t+1}+\gamma R_{t+2}+...+\gamma^{n-1}R_{t+n}+\gamma^nQ(S_{t+n})$
	2. $Q(S_t,A_t) \leftarrow Q(S_t,A_t)+\alpha(q_t^{(n)}-Q(S_t, A_t))$
	3. Also we can apply forward view Sarsa($\lambda$), $q_t^{(\lambda)}=(1-\lambda)\sum_{n=1}^{\inf}\lambda^{n-1}q_t^{(n)}$
	4. Also we can apply backward view Sarsa($\lambda$), with eligibility trace $E_t$
		1. $E_0(s,a)=0$
		2. $E_t(s,a)=\gamma \lambda E_{t-1}(s,a)+ 1(S_t=s, A_t=a)$
		3. $Q(s,a)$ is updated for every state s and action a with $E_t$
		4. In proportion to TD-error $\delta_t$ and $E_t(s,a)$, $\delta_t=R_{t+1}+\gamma Q(S_{t+1}, A_{t+1})-Q(S_t, A_t)$, $Q(s,a) \leftarrow Q(s,a) + \alpha \delta_t E_t(s,a)$
5. Off-policy learning
	1. Learn from observing humans or other agents
	2. Re-use experience generated from old policies
	3. Learn about optimal policy while following exploratory policy
	4. Learn about multiple policies 
6. Importance sampling, estimate the expectation of a different distribution $E_{X \sim P} [f(X)]= E_{X \sim Q}[\frac{P(X)}{Q(X)}f(X)]$
7. Using importance sampling with MC does not work because variance is too high, instead we use it in TD: $V(S_t) \leftarrow V(S_t) + \alpha (\frac{\pi (A_t|S_t)}{\mu (A_t|S_t)}(R_{t+1}+\gamma V(S_{t+1})) - V(S_t) )$
8. Q-learning (SARSAMAX): $Q(S,A) \leftarrow Q(S,A) + \alpha (R + \gamma  max_{a'}Q(S', a')-Q(S,A) )$
	1. The target policy $\pi$ is greedy w.r.t $Q(S,A)$, while the behavior policy $\mu$ is e.g. $\epsilon$-greedy w.r.t. $Q(S,A)$
	2. No importance sampling is required. We choose the next action using behavior policy, while update using the alternative successor action from target policy

## Reference
https://davidstarsilver.wordpress.com/teaching/
https://drive.google.com/drive/folders/1F7x3X9PhKb2LbX7GymuNZsR8_xev6gVI?usp=drive_link


