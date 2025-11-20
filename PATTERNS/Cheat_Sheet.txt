DSA Pattern Recognition Cheatsheet
=======================================

This file contains the complete pattern recognition guide for DSA.

---------------------------------------
1. Sliding Window
---------------------------------------
Used for: substrings/subarrays, longest/shortest, fixed or variable window.

Template:
left = 0
for right in range(len(nums)):
    # expand window
    while window_invalid:
        left += 1
    # update answer

---------------------------------------
2. Two Pointers
---------------------------------------
Used for: sorted arrays, pairs, triplets.

Template:
left, right = 0, len(nums)-1
while left < right:
    if condition:
        left += 1
    else:
        right -= 1

---------------------------------------
3. Fast & Slow Pointers
---------------------------------------
Used for: cycle detection, middle of list.

Template:
slow = fast = head
while fast and fast.next:
    slow = slow.next
    fast = fast.next.next

---------------------------------------
4. HashMap / Frequency Map
---------------------------------------
Used for: counting, prefix problems.

Template:
freq = {}
for x in nums:
    freq[x] = freq.get(x, 0) + 1

---------------------------------------
5. Prefix Sum
---------------------------------------
Used for: subarray = k.

Template:
prefix = 0
count = {0: 1}
for num in nums:
    prefix += num
    if prefix - k in count:
        ans += count[prefix - k]
    count[prefix] = count.get(prefix, 0) + 1

---------------------------------------
6. Monotonic Stack
---------------------------------------
Used for: next greater element.

Template:
stack = []
for i, num in enumerate(nums):
    while stack and nums[stack[-1]] < num:
        stack.pop()
    stack.append(i)

---------------------------------------
7. Intervals
---------------------------------------
Used for: merging, scheduling.

Template:
intervals.sort()
merged = []
for s, e in intervals:
    if not merged or merged[-1][1] < s:
        merged.append([s, e])
    else:
        merged[-1][1] = max(merged[-1][1], e)

---------------------------------------
8. Greedy
---------------------------------------
Used for: taking locally optimal choices.

---------------------------------------
9. Binary Search
---------------------------------------
Used for: sorted arrays, monotonic decisions.

Template:
l, r = low, high
while l <= r:
    mid = (l+r)//2
    if condition(mid):
        r = mid-1
    else:
        l = mid+1

---------------------------------------
10. Binary Search on Answer
---------------------------------------
Used for: Koko bananas, capacity.

Template:
def can(mid):
    pass
l, r = 1, max_value
while l <= r:
    mid = (l+r)//2
    if can(mid):
        r = mid-1
    else:
        l = mid+1

---------------------------------------
11. Trees — DFS
---------------------------------------
Template:
def dfs(root):
    if not root: return 0
    left = dfs(root.left)
    right = dfs(root.right)
    return f(left, right)

---------------------------------------
12. Trees — BFS
---------------------------------------
Template:
from collections import deque
q = deque([root])
while q:
    for _ in range(len(q)):
        node = q.popleft()

---------------------------------------
13. Graphs BFS/DFS
---------------------------------------
BFS:
visited = {start}
q = deque([start])

DFS:
def dfs(node):
    visited.add(node)

---------------------------------------
14. Backtracking
---------------------------------------
Used for: permutation, combination.

Template:
res = []
path = []
def backtrack(i):
    if i == goal:
        res.append(path.copy())
        return
    for choice in choices:
        path.append(choice)
        backtrack(i+1)
        path.pop()

---------------------------------------
15. Dynamic Programming (1D)
---------------------------------------
Template:
dp = [0]*(n+1)
for i in range(n):
    dp[i] = f(dp[i-1], dp[i-2], ...)

---------------------------------------
16. Dynamic Programming (2D)
---------------------------------------
Template:
dp = [[0]*m for _ in range(n)]
for i in range(n):
    for j in range(m):
        dp[i][j] = ...

---------------------------------------
17. Heap / Priority Queue
---------------------------------------
Template:
import heapq
heapq.heappush(heap, x)
heapq.heappop(heap)

---------------------------------------
18. Trie
---------------------------------------
class TrieNode:
    def __init__(self):
        self.children = {}
        self.end = False

---------------------------------------
19. Bit Manipulation
---------------------------------------
xor = 0
for n in nums:
    xor ^= n

---------------------------------------
END OF FILE
