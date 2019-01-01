# AI-Reinforcement-Learning-06-Planning-Dynamic-Programming
Lecture 3: Planning by Dynamic Programming by David Silver

https://www.bilibili.com/video/av32149008/?p=4

http://www0.cs.ucl.ac.uk/staff/D.Silver/web/Teaching.html

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
  - Problem: find optimal policy π
  - Solution: iterative application of Bellman optimality backup
  - If we know the solution to subproblems v∗(s0), Then solution v∗(s) can be found by one-step lookahead. The idea of value iteration is to apply these updates iteratively
    - Using synchronous backups
      - At each iteration k + 1
      - For all states s ∈ S
      - Update vk+1(s) from vk (s0)

- Synchronous Dynamic Programming
  - all states are backed up in paralle
  
- Asynchronous Dynamic Programming
  - backs up states individually, in any order
  - Can significantly reduce computation
  - Guaranteed to converge if all states continue to be selected
  
- Three simple ideas for asynchronous dynamic programming:
  - In-place dynamic programming
    - Synchronous value iteration stores two copies of value function
    - In-place value iteration only stores one copy of value function
  - Prioritised sweeping
    - Use magnitude of Bellman error to guide state selection
    - Backup the state with the largest remaining Bellman error
    - Update Bellman error of affected states after each backup
    - Requires knowledge of reverse dynamics (predecessor states)
    - Can be implemented efficiently by maintaining a priority queue
  - Real-time dynamic programming
    - Idea: only states that are relevant to agent
    - Use agent’s experience to guide the selection of states
    - After each time-step St, At, Rt+1
    - Backup the state St
