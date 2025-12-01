2025-11-30T16:55
## Contents
1. Model-free prediction: We don't know the transition function, but we still want to predict the value function of a given policy.
2. Monte-Carlo (MC) methods learn directly from episodes of experience.
	1. episodes: A rollout that is in the terminal state.
	2. MC policy evaluation uses empirical mean return instead of expected return.
		1. First-Visit MC policy evaluation. The first time-step t that state s is visited in an episode, increment counter $N(s) = N(s) + 1$, increment total return $S(s) = S(s) + G_t$, and value is estimated by mean return $V(s) = S(s)/N(s)$
		2. The update formula can be rewritten as $V(S_t)=V(S_t) + \frac{1}{N(S_t)}(G_t-V(S_t))$ = $V(S_t) = V(S_t) + \alpha(G_t - V(S_t))$
3. Temporal-Difference methods learns from incomplete episodes, by bootstrapping
	1. Bootstrapping, a guess of real value function S(t)
	2. $V(S_t) = V(S_t) + \alpha(R_{t+1}+\gamma V(S_{t+1}) - V(S_t))$
	3. $\delta_t=R_{t+1}+\gamma V(S_{t+1}) - V(S_t)$ is called the TD error
	4. True TD target $R_{t+1}+\gamma V_{\pi}(S_{t+1})$ is unbiased estimate of $V_{\pi}(S_t)$, TD target $R_{t+1}+\gamma V(S_{t+1})$ is biased estimate of $V_{\pi}(S_t)$
4. MC  converges to solution with minimum mean-squared error, while TD(0) converges to solution of max likelihood Markov model. So TD is more efficient in Markov env while MC is not.
5. Bootstrap: MC does not bootstrap, but TD and DP bootstrap
6. Sampling: MC and TD samples, but DP does not sample.
7. Let TD target looks n steps into the future
	1. n = 1, $G_t^{(1)}=R_{t+1}+\gamma V(S_{t+1})$
	2. n = 2, $G_t^{(2)}=R_{t+1}+\gamma R_{t+2} + \gamma^2V(S_{t+2})$
	3. n = inf, this case equals to MC
8. If we average over $G_t^{(n)}$, with weight $(1-\lambda)\lambda^{n-1}$, this is $TD(\lambda)$ algorithm. This $\lambda$ is more stable than $n$ because n depends on the number of states, whereas $\lambda$ normalizes that out.
	1. average over $G_t^{(n)}$, with weight $(1-\lambda)\lambda^{n-1}$ is the forward-view of $TD(\lambda)$ algorithm
	2. backward-view of $TD(\lambda)$ algorithm
		1. $E_0(s)=0$, $E_t(s)=\gamma \lambda E_{t-1}(s) + 1(S_t=s)$
		2. $\delta_t=R_{t+1}+\gamma V(S_{t+1})-V(S_{t})$
		3. $V(s)=V(s)+\alpha \delta_t E_t(s)$
## Reference
https://davidstarsilver.wordpress.com/teaching/
https://drive.google.com/drive/folders/1F7x3X9PhKb2LbX7GymuNZsR8_xev6gVI?usp=drive_link
