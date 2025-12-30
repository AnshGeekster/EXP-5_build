### 1. Introduction to Optimization Problems

In computer science, many real-world problems require finding the best possible solution among several available options. Such problems are known as optimization problems. The goal may be to minimize cost, time, distance, or the number of resources used, or to maximize profit, efficiency, or accuracy.

One common optimization problem is the Coin Change Problem, where the objective is to determine the minimum number of coins required to make a given amount using a set of available coin denominations. This problem appears in practical applications such as currency systems, vending machines, banking software, and digital payment systems.

To solve optimization problems efficiently, different algorithmic techniques are used. Two important approaches are:

* Greedy Algorithms
* Dynamic Programming

### 2. Greedy Algorithm
#### 2.1 Definition

A Greedy Algorithm is an algorithmic technique that constructs a solution incrementally by making the best possible choice at each step, based only on the information available at that moment. The decision made at each step is final and is never reconsidered later.

The core idea behind a greedy algorithm is:
A globally optimal solution can be achieved by repeatedly making locally optimal decisions.

#### 2.2 Characteristics of Greedy Algorithms

Greedy algorithms follow a straightforward and intuitive strategy. At every stage, the algorithm selects the option that appears to be the most beneficial at that moment. Once a choice is made, it cannot be altered in later stages, which distinguishes greedy algorithms from other optimization techniques.
The main characteristics of greedy algorithms are:

* **Local Optimization**: Decisions are made based on immediate benefit without considering the entire problem.
* **Irreversible Decisions**: Previously made choices are never reconsidered.
* **Incremental Construction**: The solution is built step by step.
* **Low Computational Overhead**: Greedy algorithms usually require less time and memory compared to other approaches.

#### 2.3 Conditions for Applicability of Greedy Algorithms

A greedy algorithm produces an optimal solution only when the problem satisfies certain conditions. If these conditions are met, making locally optimal decisions at each step will lead to a globally optimal solution. In the context of the Coin Change Problem, the following two conditions are essential.

**1. Greedy Choice Property**

The Greedy Choice Property states that a globally optimal solution can be obtained by making the best local decision at each step. This means that selecting the most favorable option at the current stage will not prevent the algorithm from reaching the optimal solution.

In the coin change problem, this property implies that choosing the largest denomination coin that does not exceed the remaining amount will always be part of an optimal solution, provided the coin system is suitable.
Mathematically, the greedy choice is defined as:

                                   d=max{di​∣di​≤A}
                            A=A−d

where:
* A is the remaining amount
* di represents the available coin denominations

At each step, the algorithm selects the coin with the maximum value that is less than or equal to the remaining amount and subtracts it from the total. If the greedy choice property holds, this decision leads to an optimal solution for the entire problem.

**2. Optimal Substructure**

A problem exhibits optimal substructure if the optimal solution to the problem can be constructed from the optimal solutions of its subproblems.

In the coin change problem, once a greedy choice is made (i.e., a coin is selected), the remaining task is to optimally solve the smaller coin change problem for the reduced amount. If the original problem has an optimal solution, then the subproblem created after the greedy choice must also have an optimal solution using the same strategy.

This property ensures that solving the problem step by step using optimal solutions of smaller amounts will eventually result in the optimal solution for the full amount.

#### 2.4 Time and Space Complexity

Time Complexity: **O(n+k)**
where, 
* n = number of denominations
* k = number of coins selected

Space Complexity: **O(1)**,since no extra memory is required.

This makes greedy algorithms fast and memory-efficient.

#### 2.5 Advantages of Greedy Algorithms

Greedy algorithms offer several benefits:

* Simple and easy to understand.
* Fast execution time.
* Requires minimal memory.
* Well-suited for real-time systems and large datasets.
* Effective for problems with clear local choices, such as scheduling and coin change in standard currency systems.

#### 2.6 Disadvantages of Greedy Algorithms

Despite their efficiency, greedy algorithms have limitations:

* Do not guarantee an optimal solution for all problems.
* Fail in cases where future decisions affect optimality.
* Not suitable for problems with complex dependencies.
* Performance depends heavily on problem structure.

#### 2.7 Applications of Greedy Algorithms

Greedy algorithms are widely used in various computer science applications, including:

* Coin Change Problem (canonical coin systems).
* Selection Problem.
* Huffman Coding.
* Minimum Spanning Tree (Prim’s and Kruskal’s algorithms).
* Job Scheduling Problems.

### 3. Greedy Algorithm for the Coin Change Problem

The Coin Change Problem involves finding how a target amount can be formed using a given set of coin denominations, assuming an unlimited supply of each coin.

Greedy Strategy for Coin Change:

1. Sort the coin denominations in descending order.
2. Select the largest coin that does not exceed the remaining amount.
3. Subtract its value from the remaining. 
4. Repeat until the remaining amount become zero.

This approach attempts to reduce the remaining amount as quickly as possible by selecting high-value coins.

#### 3.1 Explanation of Coin Change Problem

In the greedy approach to the Coin Change Problem, the algorithm always tries to minimize the number of coins by prioritizing coins with higher denominations. The intuition behind this strategy is that larger coins cover a greater portion of the target amount, thereby reducing the total number of selections required.

At each step, the algorithm focuses only on the current remaining amount and chooses the coin that provides the maximum immediate reduction in that amount. This local decision is made without analyzing how it may affect future selections. Once a coin is chosen, the algorithm permanently commits to that choice and proceeds with the reduced amount.

The greedy approach works efficiently when the coin system is designed such that each higher denomination is either a multiple of or compatible with smaller denominations. In such cases, selecting the largest possible coin at every step naturally leads to the minimum number of coins. Most real-world currency systems follow this structure, which is why greedy algorithms are commonly used in practical applications like vending machines and cash transaction systems.

However, the greedy method does not evaluate all possible combinations of coins. It assumes that choosing the best coin at the current step will always contribute to the best overall solution. While this assumption holds true for standard currency systems, it may fail for irregular or non-canonical coin denominations.

Despite this limitation, the greedy coin change algorithm is preferred in many scenarios because of its simplicity, fast execution, and minimal memory usage. It provides a quick and efficient solution when optimality is guaranteed by the structure of the coin denominations.

#### 3.2 Examples (Greedy Approach)

1. Let the coin denominations be {₹1, ₹2, ₹5, ₹10} and the target amount be ₹28.

Steps:
* Select ₹10 → remaining ₹18
* Select ₹10 → remaining ₹8
* Select ₹5 → remaining ₹3
* Select ₹2 → remaining ₹1
* Select ₹1 → remaining ₹0

Total coins used: 5

This example shows how greedy algorithms make locally optimal decisions at each step.

**Explanation** - The greedy algorithm selects ₹10 first, leaving ₹18. It again selects ₹10, leaving ₹8. Then it selects ₹5, leaving ₹3, followed by ₹2 and ₹1. The final solution is 10 + 10 + 5 + 2 + 1, using 5 coins. In this case, the greedy approach gives an optimal solution and works efficiently.

2. Let the coin denominations be {₹1, ₹5, ₹10, ₹20} and the target amount be ₹63.

Steps:
* Select ₹20 → remaining ₹43
* Select ₹20 → remaining ₹23
* Select ₹20 → remaining ₹3
* Select ₹1 → remaining ₹2
* Select ₹1 → remaining ₹1
* Select ₹1 → remaining ₹0

Total coins used: 6

This example demonstrates how the greedy algorithm repeatedly selects the highest possible denomination to reduce the remaining amount.

**Explanation** - The greedy algorithm first selects ₹20, reducing the amount to ₹43. It again selects ₹20 twice, leaving ₹3. Since no higher denomination fits the remaining amount, the algorithm uses three ₹1 coins. The final solution is 20 + 20 + 20 + 1 + 1 + 1, using 6 coins. As this coin system is canonical, the greedy approach produces an optimal solution.

#### 3.3 Limitation of Greedy Approach

The greedy approach does not always guarantee an optimal solution because it makes decisions based only on immediate benefit and ignores future consequences. It assumes that selecting the locally optimal choice at each step will always lead to a globally optimal solution, which is not true for all coin systems.

Greedy algorithms fail in cases where coin denominations are non-canonical or irregular. In such systems, choosing the largest available coin at an early stage may prevent the formation of a better combination later, resulting in the use of more coins than necessary. Since greedy algorithms do not explore alternative combinations and do not revise previous decisions, they may miss the optimal solution.

**Example Where Greedy Algorithm Fails**

Consider the coin denominations {1, 3, 4} and a target amount of 6.

* Greedy Solution:
  4 + 1 + 1 → Total coins = 3

* Optimal Solution:
  3 + 3 → Total coins = 2

  In this case, the greedy algorithm fails because selecting the largest coin (4) first leads to a suboptimal solution. This example clearly demonstrates that greedy algorithms are not reliable for all coin change problems.

### 4. Dynamic Programming Approach
#### 4.1 Definition

Dynamic Programming (DP) is an algorithmic technique used to solve complex problems by breaking them down into smaller overlapping subproblems and storing their solutions to avoid repeated computation.

Dynamic programming guarantees an optimal solution when the problem exhibits:

* Optimal Substructure – an optimal solution can be built from optimal solutions of subproblems.
* Overlapping Subproblems – the same subproblems occur multiple times.

#### 4.2 Dynamic Programming for Coin Change Problem

In the coin change problem, DP computes the minimum number of coins required for every amount from 0 to the target value.

A table (or array) is created where:
* Each entry represents the minimum coins needed for a particular .
* Previously computed results are reused to build solutions for larger amounts.

This systematic exploration ensures that all possible combinations are considered.

#### 4.3 Example (Dynamic Programming)

Consider coin denominations {1, 3, 4} and target amount = 6.

* Greedy solution: 4 + 1 + 1 → 3 coins
* DP solution: 3 + 3 → 2 coins (optimal)

Dynamic programming evaluates all valid possibilities and selects the solution with the minimum number of coins.

### 5. Comparison Between Greedy and Dynamic Programming
**Greedy Approach**

* Makes locally optimal decisions.
* Fast and easy to implement.
* Works well for standard currency systems.
* Does not guarantee optimal solution.

**Dynamic Programming Approach**

* Considers all possible combinations.
* Uses memory to store intermediate results.
* Guarantees optimal solution.
* Slightly higher time and space complexity.

### 6. Why Greedy Fails and Dynamic Programming Works

Greedy algorithms fail because:
* They do not reconsider earlier decisions.
* They do not explore alternative combinations.

Dynamic programming succeeds because:
* It evaluates multiple solution paths.
* It reuses previously computed results.
* It ensures global optimality.

### 7.Difference Between Greedy Algorithm and Dynamic Programming

| Aspect | Greedy Algorithm | Dynamic Programming (Optimal) |
|------|------------------|-------------------------------|
| Basic Idea | Chooses the best local option at each step | Evaluates all possible subproblems |
| Decision Making | Local and immediate | Global and systematic |
| Consideration of Future | Not considered | Fully considered |
| Optimality Guarantee | Not guaranteed for all cases | Always guarantees optimal solution |
| Backtracking | Not allowed | Implicitly allowed through DP table |
| Reconsideration of Choices | Not possible | Possible via stored subproblem results |
| Problem Requirements | Requires greedy choice property | Requires optimal substructure |
| Handling Non-Canonical Coins | Often fails | Works correctly |
| Solution Accuracy | May be suboptimal | Always optimal |
| Time Complexity | O(n + k) | O(n × A) |
| Space Complexity | O(1) | O(A) |
| Memory Usage | Very low | Higher due to DP table |
| Implementation Difficulty | Simple | Moderate |
| Execution Speed | Very fast | Slower compared to greedy |
| Use of Extra Storage | No | Yes |
| Flexibility | Low | High |
| Suitability for Large Inputs | Good when greedy works | Limited by memory constraints |
| Real-World Usage | Currency systems, vending machines | Financial systems requiring accuracy |
| Example Outcome (Coin Change) | May give non-optimal result | Always gives minimum coins |
| Overall Reliability | Problem-dependent | Highly reliable |

