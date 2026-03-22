### 1. Greedy Algorithms
#### 1.1 Definition

A Greedy Algorithm is an algorithmic technique that constructs a solution incrementally by making the best possible choice at each step, based only on the information available at that moment. The decision made at each step is final and is never reconsidered later.

The core idea behind a greedy algorithm is:
A globally optimal solution can be achieved by repeatedly making locally optimal decisions.

#### 1.2 Characteristics of Greedy Algorithms

Greedy algorithms follow a straightforward and intuitive strategy. At every stage, the algorithm selects the option that appears to be the most beneficial at that moment. Once a choice is made, it cannot be altered in later stages, which distinguishes greedy algorithms from other optimization techniques.
The main characteristics of greedy algorithms are:

* **Local Optimization**: Decisions are made based on immediate benefit without considering the entire problem.
* **Irreversible Decisions**: Previously made choices are never reconsidered.
* **Incremental Construction**: The solution is built step by step.
* **Low Computational Overhead**: Greedy algorithms usually require less time and memory compared to other approaches.

#### 1.3 Conditions for Applicability of Greedy Algorithms

A greedy algorithm produces an optimal solution only when the problem satisfies certain conditions. If these conditions are met, making locally optimal decisions at each step will lead to a globally optimal solution. In the context of the Coin Change Problem, the following two conditions are essential.

**a. Greedy Choice Property**

The Greedy Choice Property states that a globally optimal solution can be obtained by making the best local decision at each step. This means that selecting the most favorable option at the current stage will not prevent the algorithm from reaching the optimal solution.


**b. Optimal Substructure**

A problem exhibits optimal substructure if the optimal solution to the problem can be constructed from the optimal solutions of its subproblems.

This property ensures that solving the problem step by step using optimal solutions of smaller amounts will eventually result in the optimal solution for the full amount.


#### 1.4 Advantages of Greedy Algorithms

Greedy algorithms offer several benefits:

* Simple and easy to understand.
* Fast execution time.
* Requires minimal memory.
* Well-suited for real-time systems and large datasets.
* Effective for problems with clear local choices, such as scheduling and coin change in standard currency systems.

#### 1.5 Disadvantages of Greedy Algorithms

Despite their efficiency, greedy algorithms have limitations:

* Do not guarantee an optimal solution for all problems.
* Fail in cases where future decisions affect optimality.
* Not suitable for problems with complex dependencies.
* Performance depends heavily on problem structure.

#### 1.6 Applications of Greedy Algorithms

Greedy algorithms are widely used in various computer science applications, including:

* Coin Change Problem (canonical coin systems).
* Selection Problem.
* Huffman Coding.
* Minimum Spanning Tree (Prim’s and Kruskal’s algorithms).
* Job Scheduling Problems.

### 2. Greedy Algorithm for the Coin Change Problem

The Coin Change Problem involves finding how a target amount can be formed using a given set of coin denominations, assuming an unlimited supply of each coin.

Greedy Strategy for Coin Change:

1. Sort the coin denominations in descending order.
2. Select the largest coin that does not exceed the remaining amount.
3. Subtract its value from the remaining. 
4. Repeat until the remaining amount becomes zero.

This approach attempts to reduce the remaining amount as quickly as possible by selecting high-value coins.

#### 2.1 Greedy Algorithm Properties in the Coin Change Problem

**a. Application of Greedy Choice Property in Coin Change**

In the coin change problem, this property implies that choosing the largest denomination coin that does not exceed the remaining amount will always be part of an optimal solution, provided the coin system is suitable.
Mathematically, the greedy choice is defined as:

                                   d=max{di​∣di​≤A}
                            A=A−d

where:
* A is the remaining amount
* di represents the available coin denominations

At each step, the algorithm selects the coin with the maximum value that is less than or equal to the remaining amount and subtracts it from the total. If the greedy choice property holds, this decision leads to an optimal solution for the entire problem.

**b. Application of Optimal Substructure in Coin Change**

In the coin change problem, once a greedy choice is made (i.e., a coin is selected), the remaining task is to optimally solve the smaller coin change problem for the reduced amount. If the original problem has an optimal solution, then the subproblem created after the greedy choice must also have an optimal solution using the same strategy.

#### 2.2 Time and Space Complexity

**Time Complexity (Greedy Approach):** **O(n + k)**  

where,  
* n = number of denominations (coins checked once)  
* k = number of coins selected in the final solution  

**Explanation:**  
The algorithm iterates through all denominations once (**O(n)**) and, for each denomination, selects coins until the required amount is reduced to zero (**O(k)** in total across all denominations). Hence, the overall time complexity is **O(n + k)**.

**Space Complexity:** **O(1)**  

The algorithm uses a constant amount of extra space, as it does not require any additional data structures apart from a few variables.

This makes the greedy approach both time-efficient and memory-efficient.

#### 2.3 Examples (Greedy Approach)

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

#### 2.4 Limitation of Greedy Approach

The greedy approach does not always guarantee an optimal solution because it makes decisions based only on the current step and ignores future outcomes. It assumes that a locally optimal choice will lead to a globally optimal solution, which is not always true.

Greedy algorithms may fail for non-canonical or irregular coin systems, where selecting the largest coin first can lead to a suboptimal result. Since greedy methods do not reconsider previous choices or explore all possible combinations, they may miss the best solution. In such cases, Dynamic Programming is used as it evaluates all possible subproblems and guarantees an optimal solution.

**Example Where Greedy Algorithm Fails**

Consider the coin denominations {1, 3, 4} and a target amount of 6.

* Greedy Solution:
  4 + 1 + 1 → Total coins = 3

* Optimal Solution:
  3 + 3 → Total coins = 2

  In this case, the greedy algorithm fails because selecting the largest coin (4) first leads to a suboptimal solution. This example clearly demonstrates that greedy algorithms are not reliable for all coin change problems.

 ### 3. Why Greedy Fails and Dynamic Programming Works

Greedy algorithms fail because:
* They do not reconsider earlier decisions.
* They do not explore alternative combinations.

Dynamic programming succeeds because:
* It evaluates multiple solution paths.
* It reuses previously computed results.
* It ensures global optimality. 

### 4. Comparison Between Greedy and Dynamic Programming
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




