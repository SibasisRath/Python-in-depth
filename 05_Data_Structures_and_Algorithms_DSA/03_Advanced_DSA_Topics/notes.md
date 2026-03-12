# Advanced DSA Topics

## Explanation

Once you've mastered the basics, you can explore specialized data structures and advanced techniques:

- **Trie (Prefix Tree)**: A tree data structure used for efficient retrieval of strings, often employed in autocomplete and spell-check features.
- **Segment Tree / Fenwick Tree (Binary Indexed Tree)**: Trees that allow fast range queries and updates (e.g., sum over interval) on an array.
- **Disjoint Set Union (Union-Find)**: Keeps track of a set of elements partitioned into disjoint subsets; useful in Kruskal's MST algorithm and connectivity queries.
- **Advanced Graph Algorithms**: Algorithms for MST (Prim, Kruskal), strongly connected components (Kosaraju, Tarjan), cycle detection, and flow problems.
- **Computational Geometry Basics**: Points, lines, convex hulls, and algorithms like Graham scan.

These structures often underpin competitive programming and high-performance applications.

## Examples

### Simple Trie implementation
```python
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end = False

class Trie:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        node = self.root
        for ch in word:
            if ch not in node.children:
                node.children[ch] = TrieNode()
            node = node.children[ch]
        node.is_end = True

    def search(self, word):
        node = self.root
        for ch in word:
            if ch not in node.children:
                return False
            node = node.children[ch]
        return node.is_end

trie = Trie()
trie.insert("hello")
print(trie.search("hello"))  # True
print(trie.search("hell"))   # False
```

### Union-Find (Disjoint Set)
```python
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank = [0] * n

    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])
        return self.parent[x]

    def union(self, x, y):
        rx, ry = self.find(x), self.find(y)
        if rx == ry:
            return
        if self.rank[rx] < self.rank[ry]:
            self.parent[rx] = ry
        elif self.rank[ry] < self.rank[rx]:
            self.parent[ry] = rx
        else:
            self.parent[ry] = rx
            self.rank[rx] += 1

uf = UnionFind(5)
uf.union(0, 1)
uf.union(1, 2)
print(uf.find(2))  # 0
```

### Segment tree for range sum
```python
class SegmentTree:
    def __init__(self, data):
        self.n = len(data)
        self.tree = [0] * (2 * self.n)
        for i in range(self.n):
            self.tree[self.n + i] = data[i]
        for i in range(self.n - 1, 0, -1):
            self.tree[i] = self.tree[2*i] + self.tree[2*i+1]

    def update(self, idx, val):
        i = idx + self.n
        self.tree[i] = val
        while i > 1:
            i //= 2
            self.tree[i] = self.tree[2*i] + self.tree[2*i+1]

    def query(self, left, right):
        # inclusive left, exclusive right
        res = 0
        l, r = left + self.n, right + self.n
        while l < r:
            if l & 1:
                res += self.tree[l]
                l += 1
            if r & 1:
                r -= 1
                res += self.tree[r]
            l //= 2; r //= 2
        return res

seg = SegmentTree([1,2,3,4])
print(seg.query(1,3))  # sum of indices 1 and 2 -> 5
```

## Tasks

### Beginner
1. Build a Trie and insert a small dictionary of words; search for prefixes.
2. Implement a basic Union-Find and perform a few unions/finds manually.
3. Use `heapq` to build a max‑heap by pushing negative values and pop the largest.

### Intermediate
1. Implement a Fenwick Tree for prefix sums and update operations.
2. Write code to find connected components in a graph using DFS/BFS.
3. Solve the ``word ladder`` problem using BFS on word transformations.

### Advanced
1. Implement Kruskal's algorithm for Minimum Spanning Tree with Union-Find.
2. Create a 2D segment tree for range queries on a matrix.
3. Solve a computational geometry problem such as computing the convex hull of a set of points using Graham scan.

## Quick Review
- What advantages does a Trie offer over a hash table for prefix searches?
- How does path compression help Union-Find operations?
- Explain how a segment tree can perform range queries faster than naive iteration.
- In what situations would you prefer Fenwick Tree to Segment Tree?

---

These advanced tools round out your DSA toolkit and prepare you for high-level algorithmic challenges.