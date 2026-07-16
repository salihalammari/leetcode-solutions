<h2><a href="https://leetcode.com/problems/find-closest-number-to-zero">2350. Find Closest Number to Zero</a></h2><h3>Easy</h3><hr><p>Given an integer array <code>nums</code> of size <code>n</code>, return <em>the number with the value <strong>closest</strong> to </em><code>0</code><em> in </em><code>nums</code>. If there are multiple answers, return <em>the number with the <strong>largest</strong> value</em>.</p>
<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> nums = [-4,-2,1,4,8]
<strong>Output:</strong> 1
<strong>Explanation:</strong>
The distance from -4 to 0 is |-4| = 4.
The distance from -2 to 0 is |-2| = 2.
The distance from 1 to 0 is |1| = 1.
The distance from 4 to 0 is |4| = 4.
The distance from 8 to 0 is |8| = 8.
Thus, the closest number to 0 in the array is 1.
</pre>

<p><strong class="example">Example 2:</strong></p>

<pre>
<strong>Input:</strong> nums = [2,-1,1]
<strong>Output:</strong> 1
<strong>Explanation:</strong> 1 and -1 are both the closest numbers to 0, so 1 being larger is returned.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 1000</code></li>
	<li><code>-10<sup>5</sup> &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
</ul>


# 🔍 Find Closest Number to Zero

## 📌 Problem

Given an integer array `nums`, return the number that is **closest to zero**.

If two numbers are equally close to zero (for example `-2` and `2`), return the **positive** number.

### Example

```text
Input:
nums = [-4, -2, 1, 4, 2]

Output:
2
```

---

# 💡 Approach

The idea is to iterate through the array once while keeping track of the current closest value.

For every number:

- Compare its absolute value with the current closest number.
- If it is closer to zero, update the answer.
- If both numbers have the same distance from zero, choose the positive one.

This guarantees that the correct value is always stored in `closest`.

---

# 🧠 Algorithm

1. Initialize `closest` with the first element.
2. Traverse the array.
3. Compare absolute values using `abs()`.
4. Update `closest` if:
   - The current number is closer to zero.
   - Both numbers are equally close and the current one is positive.
5. Return `closest`.

---

# ⏱️ Complexity Analysis

| Complexity | Value |
|------------|-------|
| Time | **O(n)** |
| Space | **O(1)** |

- We scan the array only once.
- No extra data structures are used.

---

# ⚠️ Edge Cases

- Single element array

```text
[7]
```

Return:

```text
7
```

---

- All negative numbers

```text
[-8, -5, -2]
```

Return:

```text
-2
```

---

- All positive numbers

```text
[5, 9, 1]
```

Return:

```text
1
```

---

- Equal distance from zero

```text
[-3, 3]
```

Return:

```text
3
```

Positive wins when distances are equal.

---

# 🧪 Python Solution

```python
class Solution:
    def findClosestNumber(self, nums):
        closest = nums[0]

        for x in nums:
            if abs(x) < abs(closest):
                closest = x
            elif abs(x) == abs(closest) and x > closest:
                closest = x

        return closest
```

---

# 📚 Concepts Practiced

- Arrays
- Linear Search
- Absolute Value (`abs`)
- Comparison Operators
- Tie-breaking Logic
- Time Complexity Analysis

---

# 🚀 What I Learned

While solving this problem, I learned:

- How the `abs()` function works.
- How to compare distances from zero.
- How to handle tie-breaking conditions.
- How to solve a problem in **O(n)** time using a single loop.

---

## 🛠️ Language

- Python 🐍

---

⭐ If you found this repository helpful, consider giving it a star.
