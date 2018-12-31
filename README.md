# AI-Reinforcement-Learning-06-Planning-Dynamic-Programming
Lecture 3: Planning by Dynamic Programming by David Silver

- Iterative Policy Evaluation
  - Problem: evaluate a given policy π
  - Solution: iterative application of Bellman expectation backup
  - Using synchronous backups,
     - At each iteration k + 1
     - For all states s ∈ S
     - Update vk+1(s) from vk (s0) where s0 is a successor state of s

- Policy Iteration (How to Improve a Policy)
   - Given a policy π
     - Policy evaluation
       - Estimate vπ
       - vπ(s) = E [Rt+1 + γRt+2 + ...|St = s]
     - Policy improvement
       - Improve the policy by acting greedily with respect to vπ
       - π0 = greedy(vπ)
       - Generate π0 ≥ π
       - π0(s) = argmax qπ(s, a)
       - This improves the value from any state s over one step,
         - qπ(s, π0(s)) = max qπ(s, a) ≥ qπ(s, π(s)) = vπ(s)
       - It therefore improves the value function, vπ0(s) ≥ vπ(s)
    
- Value Iteration
