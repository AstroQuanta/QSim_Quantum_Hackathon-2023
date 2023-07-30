# Optimizing Quantum Algorithms: Paving the Way for Remarkable Results

Better algorithm is always the requirement in the world of computer science and computational physics. Building up a better algorithm with better time complexity and space complexity is of real importance for studies of the physical phenomena. 

## 1. Amplitude Estimation without Phase Estimation
We focus on the quantum amplitude estimation algorithm, which is a core subroutine in quantum computation for various applications. The conventional approach for amplitude estimation is to use the phase estimation algorithm, which consists of many controlled amplification operations followed by a quantum Fourier transform. However, the whole procedure is hard to implement with current and near-term quantum computers. We propose a quantum amplitude estimation algorithm without the use of expensive controlled operations; the key idea is to utilize the maximum likelihood estimation based on the combined measurement data produced from quantum circuits with different numbers of amplitude amplification operations.

Here, I demonstrate the amplitude estimation algorithm, which is a core subroutine in quantum computation for various applications, e.g., in chemistry, finance, and machine learning. In particular, quantum speedup of Monte Carlo sampling via amplitude estimation lies in the heart of these applications.

### 1.1 Prelims
We herein briefly describe the quantum amplitude amplification, which is the basis of our approach for the amplitude estimation problem. Our proposed algorithm mainly consists of two parts: 
- quantum amplitude amplification
- amplitude estimation based on likelihood analysis. 
The amplitude amplification is the generalization of the
Grover’s quantum searching algorithm. Similar to quantum searching, the amplitude amplification is known to achieve quadratic speedup over the corresponding classical algorithm.

### 1.2 Algorithm
The first stage of the algorithm is to make good or bad measurements on the quantum state $Q^{m_k}\left|\psi_i\right>$ for a chosen set of {$m_k$}. Let $N_k$ be the number of measurements (shots) and $h_k$ be the number of measuring good states for the state $Q^{m_k}\left|\psi_i\right>$ ; then, because the probability measuring the good state is $\sin^2((2m_k + 1)\theta_a$, the likelihood function representing this probabilistic event is given by:

$$
L_k(h_k;\theta_a) = \left( \sin^2((2m_k + 1)\theta_a) \right)^{h_k} \left( \cos^2((2m_k + 1)\theta_a) \right)^{N_k - h_k}. 
$$

The second stage of the algorithm is to combine the likelihood functions $L_k(h_k;\theta_a)$ for several $\{{m_0, m_1, \ldots, m_M\}}$ to construct a single likelihood function $L(h;\theta_a)$:

$$
L(\mathbf{h};\theta_a) = \prod_{k=0}^M L_k(h_k;\theta_a). 
$$

where $\mathbf{h} = \{{h_0, h_1, \ldots, h_M\}}$. The ML estimate is defined as the value that maximizes $L(h;\theta_a)$:

$$
\tilde{\theta}_a = \mbox{arg}~\mbox{max}_{\theta} L(\mathbf{h};\theta_a).
$$                                  
    
This algorithm has two caveats: 

(i) if only a single amplitude amplification circuit is used like in the Grover search algorithm, i.e., the case M = 0 and m0 6= 0, the ML estimate $\thetaˆa$ cannot be uniquely determined due to the periodicity of $L_0(h_0;\theta_a)$, and 

(ii) if no amplification operator is applied, i.e., $m_k = 0 ∀k$, then the ML estimate is unique, but it does not have any quantum advantages, as shown later. 

Hence, the heart of our algorithm can be regarded as the quantum circuit fusion technique that combines some
quantum circuits to determine the target value uniquely, while some quantum advantage is guaranteed.

### 1.3 Application: Monte-Carlo Integration

Here, I demonstrate Monte Carlo integration as an example of the application of our algorithm.

One purpose of the Monte Carlo integration is to calculate the expected value of real valued function 0 ≤ f(x) ≤ 1 defined for n-bit input x ∈ {0,1} n with probability p(x).




