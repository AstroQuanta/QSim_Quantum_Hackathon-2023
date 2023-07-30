# Optimizing Quantum Algorithms: Paving the Way for Remarkable Results

Better algorithm is always the requirement in the world of computer science and computational physics. Building up a better algorithm with better time complexity and space complexity is of real importance for studies of the physical phenomena. 

## 1. Amplitude Estimation without Phase Estimation
We focus on the quantum amplitude estimation algorithm, which is a core subroutine in quantum computation for various applications. The conventional approach for amplitude estimation is to use the phase estimation algorithm, which consists of many controlled amplification operations followed by a quantum Fourier transform. However, the whole procedure is hard to implement with current and near-term quantum computers. We propose a quantum amplitude estimation algorithm without the use of expensive controlled operations; the key idea is to utilize the maximum likelihood estimation based on the combined measurement data produced from quantum circuits with different numbers of amplitude amplification operations.

Here, I demonstrate the amplitude estimation algorithm, which is a core subroutine in quantum computation for various applications, e.g., in chemistry, finance, and machine learning. In particular, quantum speedup of Monte Carlo sampling via amplitude estimation lies in the heart of these applications.



## 1.1 Prelims
We herein briefly describe the quantum amplitude amplification, which is the basis of our approach for the amplitude estimation problem. Our proposed algorithm mainly consists of two parts: 
- quantum amplitude amplification
- amplitude estimation based on likelihood analysis. 
The amplitude amplification is the generalization of the
Grover’s quantum searching algorithm. Similar to quantum searching, the amplitude amplification is known to achieve quadratic speedup over the corresponding classical algorithm.

## 1.2 Algorithm
The first stage of the algorithm is to make good or bad measurements on the quantum state Q^mk|Ψi> for a chosen set of {mk}. Let Nk be the number of measurements (shots) and hk
be the number of measuring good states for the state Qmk |Ψi; then, because the probability measuring the good state is sin^2 ((2mk +1)θa), the likelihood function representing this probabilistic event is given by:

                                                Lk(hk;θa) = [sin2((2mk +1)θa)]^hk[cos2((2mk +1)θa)]^Nk−hk

The second stage of the algorithm is to combine the likelihood functions Lk(hk;θa)for several {m0,...,mM} to construct a single likelihood function L(h;θa):

                                                            L(h;θa) =  ∏ Lk(hk;θa) {k=[0,M]}

where h = (h0,h1,··· ,hM). The ML estimate is defined as the value that maximizes L(h;θa):

                                                          θˆa = arg max(L(h;θa)) = arg max(lnL(h;θa))
    
This algorithm has two caveats: 

(i) if only a single amplitude amplification circuit is used like in the Grover search algorithm, i.e., the case M = 0 and m0 6= 0, the ML estimate θˆa cannot be uniquely determined due to the periodicity of L0(h0;θa), and 

(ii) if no amplification operator is applied, i.e., mk = 0 ∀k, then the ML estimate is unique, but it does not have any quantum advantages, as shown later. 

Hence, the heart of our algorithm can be regarded as the quantum circuit fusion technique that combines some
quantum circuits to determine the target value uniquely, while some quantum advantage is guaranteed.

## 1.3 Application: Monte-Carlo Integration

Here, I demonstrate Monte Carlo integration as an example of the application of our algorithm.

One purpose of the Monte Carlo integration is to calculate the expected value of real valued function 0 ≤ f(x) ≤ 1 defined for n-bit input x ∈ {0,1} n with probability p(x).




