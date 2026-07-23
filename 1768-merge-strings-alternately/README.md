<h2><a href="https://leetcode.com/problems/merge-strings-alternately">1894. Merge Strings Alternately</a></h2><h3>Easy</h3><hr><p>You are given two strings <code>word1</code> and <code>word2</code>. Merge the strings by adding letters in alternating order, starting with <code>word1</code>. If a string is longer than the other, append the additional letters onto the end of the merged string.</p>

<p>Return <em>the merged string.</em></p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> word1 = &quot;abc&quot;, word2 = &quot;pqr&quot;
<strong>Output:</strong> &quot;apbqcr&quot;
<strong>Explanation:</strong>&nbsp;The merged string will be merged as so:
word1:  a   b   c
word2:    p   q   r
merged: a p b q c r
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> word1 = &quot;ab&quot;, word2 = &quot;pqrs&quot;
<strong>Output:</strong> &quot;apbqrs&quot;
<strong>Explanation:</strong>&nbsp;Notice that as word2 is longer, &quot;rs&quot; is appended to the end.
word1:  a   b 
word2:    p   q   r   s
merged: a p b q   r   s
</pre>

<p><strong class="example">Example 3:</strong></p>

<pre>
<strong>Input:</strong> word1 = &quot;abcd&quot;, word2 = &quot;pq&quot;
<strong>Output:</strong> &quot;apbqcd&quot;
<strong>Explanation:</strong>&nbsp;Notice that as word1 is longer, &quot;cd&quot; is appended to the end.
word1:  a   b   c   d
word2:    p   q 
merged: a p b q c   d
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= word1.length, word2.length &lt;= 100</code></li>
	<li><code>word1</code> and <code>word2</code> consist of lowercase English letters.</li>
</ul>

# 🔀 Merge Strings Alternately

## 📌 Problem

You are given two strings `word1` and `word2`.

Merge the strings by alternating their characters, starting with the first character of `word1`.

If one string is longer than the other, append the remaining characters to the end.

---

## 📝 Example

### Example 1

```text
Input:
word1 = "abc"
word2 = "pqr"

Output:
"apbqcr"
```

---

### Example 2

```text
Input:
word1 = "ab"
word2 = "pqrs"

Output:
"apbqrs"
```

---

### Example 3

```text
Input:
word1 = "abcd"
word2 = "pq"

Output:
"apbqcd"
```

---

# 💡 Intuition

The idea is simple:

- Take one character from `word1`.
- Take one character from `word2`.
- Repeat until one string finishes.
- Append the remaining characters from the longer string.

This guarantees that every character appears exactly once in the final string.

---

# 🧠 Algorithm

1. Create two pointers (`a` and `b`).
2. Traverse both strings simultaneously.
3. Append one character from each string alternately.
4. If one string is longer, append the remaining characters.
5. Return the merged string.

---

# 🐍 Python Solution

```python
class Solution:
    def mergeAlternately(self, word1: str, word2: str) -> str:
        A, B = len(word1), len(word2)
        a, b = 0, 0
        s = []

        word = 1

        while a < A and b < B:
            if word == 1:
                s.append(word1[a])
                a += 1
                word = 2
            else:
                s.append(word2[b])
                b += 1
                word = 1

        while a < A:
            s.append(word1[a])
            a += 1

        while b < B:
            s.append(word2[b])
            b += 1

        return "".join(s)
```

---

# 🔍 Dry Run

Input

```text
word1 = "abc"
word2 = "xyz"
```

Iteration 1

```text
Result = "a"
```

Iteration 2

```text
Result = "ax"
```

Iteration 3

```text
Result = "axb"
```

Iteration 4

```text
Result = "axby"
```

Iteration 5

```text
Result = "axbyc"
```

Iteration 6

```text
Result = "axbycz"
```

Final Output

```text
axbycz
```

---

# ⏱ Complexity Analysis

| Complexity | Value |
|------------|-------|
| Time | **O(m + n)** |
| Space | **O(m + n)** |

Where:

- **m** = length of `word1`
- **n** = length of `word2`

Each character is visited exactly once.

---

# ⚠ Edge Cases

### Equal length

```text
abc
xyz
```

Output

```text
axbycz
```

---

### First string longer

```text
abcd
xy
```

Output

```text
axbycd
```

---

### Second string longer

```text
ab
wxyz
```

Output

```text
awbxyz
```

---

### One empty string

```text
word1 = ""
word2 = "abc"
```

Output

```text
abc
```

---

# 📚 Concepts Practiced

- Strings
- Two Pointers
- Array/List
- String Builder Pattern (`list + join`)
- Time Complexity Analysis

---

# 🎯 What I Learned

While solving this problem, I learned:

- How to traverse two strings simultaneously.
- Why using a list and `"".join()` is more efficient than repeated string concatenation.
- How to solve problems using the Two Pointers technique.
- How to handle strings with different lengths safely.

---

# 🚀 Key Takeaway

Instead of concatenating strings repeatedly, build a list of characters and join them once at the end.

This reduces the time complexity from **O(n²)** to **O(n)** and is the preferred approach in Python.

---

⭐ Problem Number: **1768**

Difficulty: **Easy**

Pattern: **Two Pointers**
