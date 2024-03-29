# Coding Problem-Solving Techniques

Approaching coding problems during technical tests can be made more efficient with certain strategies or "hacks." Here's a guide to some common problem-solving techniques, including the sliding window technique, using dictionaries, and more:

## 1. Sliding Window for Array/String Problems

- Use Case: Efficiently solving problems related to contiguous subarrays or substrings, especially when dealing with sums or lengths.
- Approach: Maintain a window that satisfies the problem condition and slide it through the data. Adjust the window size or position based on specific conditions.
- Example: Finding the longest substring without repeating characters.

    ```python
    def longest_substring(s):
        char_set = set()
        left = 0
        result = 0

        for right in range(len(s)):
            while s[right] in char_set:
                char_set.remove(s[left])
                left += 1
            char_set.add(s[right])
            result = max(result, right - left + 1)

        return result
    ```

## 2. Using Hash Tables (Dictionaries)

- Use Case: When you need to efficiently store and access data based on keys, especially for frequency counting or unique item tracking.
- Approach: Use Python dictionaries to map keys to values. This is particularly useful for problems that involve counting or fast lookups.
- Example: Finding the first non-repeating character in a string.

    ```python
    def first_unique_char(s):
        frequency = {}
        for char in s:
            frequency[char] = frequency.get(char, 0) + 1

        for i, char in enumerate(s):
            if frequency[char] == 1:
                return i
        return -1
    ```

## 3. Two Pointers Technique

- Use Case: Useful in sorted arrays or linked lists, especially for finding pairs, reversing structures, or merging sorted lists.
- Approach: Use two pointers (like start and end) to scan the structure, adjusting them based on certain conditions.
- Example: Reversing a list in-place.

    ```python
    def reverse_list(lst):
        left, right = 0, len(lst) - 1
        while left < right:
            lst[left], lst[right] = lst[right], lst[left]
            left, right = left + 1, right - 1
        return lst
    ```

## 4. Depth-First Search (DFS) and Breadth-First Search (BFS)

- Use Case: Traversing or searching tree or graph data structures.
- DFS Approach: Use a stack (or recursion) to explore nodes and backtrack.
- BFS Approach: Use a queue to explore nodes level by level.
- Example: Checking if a path exists in a graph.

    ```python
    def path_exists(graph, start, end):
        visited = set()
        def dfs(node):
            if node == end:
                return True
            visited.add(node)
            return any(neighbor not in visited and dfs(neighbor) for neighbor in graph[node])
        return dfs(start)
    ```

## 5. Dynamic Programming

- Use Case: Solving problems that involve breaking them down into overlapping subproblems and building up solutions to larger problems.
- Approach: Typically involves either a top-down (memoization) or bottom-up (tabulation) approach.
- Example: Fibonacci sequence.

    ```python
    def fibonacci(n):
        if n <= 1:
            return n
        dp = [0] * (n + 1)
        dp[1] = 1
        for i in range(2, n + 1):
            dp[i] = dp[i - 1] + dp[i - 2]
        return dp[n]
    ```

## 6. Greedy Algorithms

- Use Case: Problems where locally optimal choices lead to a globally optimal solution.
- Approach: Choose the best option at the current time, without reconsidering previous choices.
- Example: Coin change problem for minimum coins.

    ```python
    def coinChange(coins, amount):
        coins.sort(reverse=True)
        count = 0
        for coin in coins:
            if amount >= coin:
                count += amount // coin
                amount %= coin
        return count if amount == 0 else -1
    ```

## 7. Binary Search

- Use Case: Searching in a sorted array.
- Approach: Repeatedly divide the search interval in half.
- Example: Finding an element in a sorted array.

    ```python
    def binary_search(arr, target):
        left, right = 0, len(arr) - 1
        while left <= right:
            mid = left + (right - left) // 2
            if arr[mid] == target:
                return mid
            elif arr[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
        return -1
    ```

## General Tips:

- Understand the Problem: Ensure you fully understand the problem before starting to code.
- Choose the Right Data Structure: Picking the right data structure can significantly simplify the solution.
- Think About Edge Cases: Consider empty inputs, negative numbers, or extremely large values.
- Write Clean and Readable Code: Focus on writing clear and understandable code.
- Optimize Later: Get a working solution first, then optimize if needed.

By mastering these techniques, you'll be well-equipped to tackle a wide range of coding problems in technical assessments. Remember, practice is key to becoming proficient in applying these strategies.
