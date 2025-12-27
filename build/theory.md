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

#### 2.2 Greedy Choice Property

A problem is suitable for a greedy algorithm if it satisfies the Greedy Choice Property, which means:
Choosing the best option at the current step leads to an optimal solution for the entire problem.
Mathematically, in the context of the coin change problem, the greedy choice is:

                         d=max{dᵢ ∣ dᵢ ≤ A}
                  𝐴 = 𝐴 − 𝑑

where,
* 𝐴 is the remaining amount.
* dᵢ represents available denominations.
At each step, the algorithm selects the largest denomination that does not exceed the remaining amount.

#### 2.3 Time and Space Complexity

Time Complexity: **O(n+k)**
where, 
* n = number of denominations
* k = number of coins selected

Space Complexity: **O(1)**,since no extra memory is required.

This makes greedy algorithms fast and memory-efficient.

### 3. Greedy Algorithm for the Coin Change Problem

The Coin Change Problem involves finding how a target amount can be formed using a given set of coin denominations, assuming an unlimited supply of each coin.

Greedy Strategy for Coin Change:

1. Sort the coin denominations in descending order.
2. Select the largest coin that does not exceed the remaining amount.
3. Subtract its value from the remaining .
4. Repeat until the remaining amount becomes .

This approach attempts to reduce the remaining amount as quickly as possible by selecting high-value coins.

#### Example (Greedy Approach)

Let the coin denominations be {₹1, ₹2, ₹5, ₹10} and the target amount be ₹28.

Steps:
* Select ₹10 → remaining ₹18
* Select ₹10 → remaining ₹8
* Select ₹5 → remaining ₹3
* Select ₹2 → remaining ₹1
* Select ₹1 → remaining ₹0

Total coins used: 5

This example shows how greedy algorithms make locally optimal decisions at each step.

#### Limitation of Greedy Approach

Although greedy algorithms are simple and fast, they do not always produce the optimal solution, especially when coin denominations are non-standard. This is because greedy decisions are made without considering future consequences.

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

#### Example (Dynamic Programming)

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

#### Why Greedy Fails and Dynamic Programming Works

Greedy algorithms fail because:
* They do not reconsider earlier decisions.
* They do not explore alternative combinations.

Dynamic programming succeeds because:
* It evaluates multiple solution paths.
* It reuses previously computed results.
* It ensures global optimality.