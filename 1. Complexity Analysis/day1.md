# Day 1: Time Complexity Analysis - Beginner's Guide

**Duration: 2 Hours**  
**Goal: Understand how to measure algorithm efficiency**

---

## Hour 1: Understanding Time Complexity

---

### Part 1: What is Time Complexity? (15 mins)

#### The Problem
Imagine you have 2 ways to find your friend's phone number:

**Method 1:** Check every page one by one from start  
**Method 2:** Open middle page, decide left or right, repeat

Which is faster? How do we measure "faster"?

#### The Solution: Time Complexity

**Time Complexity** = How much time an algorithm takes as input grows

**Important Points:**
- We don't measure in seconds (depends on computer speed)
- We count **number of operations**
- We see how time changes when input size increases

#### Real Example

```
Task: Find number 7 in array [1, 3, 5, 7, 9]

Method 1 (Check each):
- Check 1? No
- Check 3? No  
- Check 5? No
- Check 7? Yes! Found!
Operations = 4

Method 2 (If sorted, jump):
Different approach, different operations!
```

**Key Idea:** More input = More operations = More time

---

### Part 2: Best, Average, Worst Case (20 mins)

Think of searching for a book in library:

#### Best Case - Lucky Day! 🍀
The book is right at the front!

**Example:** Find 5 in [5, 2, 8, 1, 9]
- Check first element: 5? YES!
- Operations = **1**
- **Best Case = Minimum operations possible**

#### Worst Case - Bad Luck! 😰
The book is at the very end or not there!

**Example:** Find 9 in [5, 2, 8, 1, 9]
- Check 5? No
- Check 2? No
- Check 8? No
- Check 1? No
- Check 9? YES!
- Operations = **5**
- **Worst Case = Maximum operations possible**

#### Average Case - Normal Day 😐
Book is somewhere in middle (on average)

**Example:** Find any number
- Sometimes 1 check, sometimes 2, sometimes 5
- Average = (1 + 2 + 3 + 4 + 5) / 5 = **3**
- **Average Case = Expected operations**

#### Which Case Do We Use?

**Most Important = Worst Case!** Why?
- We want to know the MAXIMUM time
- Guarantees algorithm won't be slower
- Used in real systems (Google, Facebook, etc.)

---

### Part 3: Big O Notation - The Language of Complexity (25 mins)

#### What is Big O?

Big O is a way to write time complexity using math notation.

**Think of it as:** "In worst case, my algorithm takes **at most** this much time"

#### Common Big O Notations

**1. O(1) - Constant Time** ⚡
"No matter how big input, same time!"

```javascript
// Example: Get first element
function getFirst(arr) {
    return arr[0];  // Always 1 operation
}

// Input size 10: 1 operation
// Input size 1000: 1 operation  
// Input size 1000000: 1 operation
```

**Real Life:** Opening your phone - same time whether you have 1 app or 100 apps

---

**2. O(n) - Linear Time** 📈
"Time grows directly with input size"

```javascript
// Example: Print all elements
function printAll(arr) {
    for(let i = 0; i < arr.length; i++) {
        console.log(arr[i]);  // n operations
    }
}

// Input size 10: 10 operations
// Input size 100: 100 operations
// Input size 1000: 1000 operations
```

**Real Life:** Reading every page of a book - more pages = more time

---

**3. O(n²) - Quadratic Time** 📊
"Time grows with square of input size"

```javascript
// Example: Compare every pair
function printPairs(arr) {
    for(let i = 0; i < arr.length; i++) {      // n times
        for(let j = 0; j < arr.length; j++) {  // n times each
            console.log(arr[i], arr[j]);
        }
    }
}

// Input size 10: 10 × 10 = 100 operations
// Input size 100: 100 × 100 = 10,000 operations
// Input size 1000: 1000 × 1000 = 1,000,000 operations
```

**Real Life:** Comparing every student with every other student in class

---

**4. O(log n) - Logarithmic Time** 🎯
"Time grows slowly even when input is huge"

```javascript
// Example: Binary Search (divide and conquer)
function binarySearch(arr, target) {
    let left = 0, right = arr.length - 1;
    
    while(left <= right) {
        let mid = Math.floor((left + right) / 2);
        
        if(arr[mid] === target) return mid;
        if(arr[mid] < target) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}

// Input size 10: ~3 operations
// Input size 100: ~7 operations
// Input size 1000: ~10 operations
// Input size 1000000: ~20 operations
```

**Real Life:** Finding word in dictionary - open middle, go left/right, repeat

---

**5. O(n log n) - Linearithmic Time** 🔄
"Better than O(n²) but slower than O(n)"

```javascript
// Example: Merge Sort, Quick Sort
// Divides array + processes all elements

// Input size 10: ~30 operations
// Input size 100: ~700 operations
// Input size 1000: ~10,000 operations
```

**Real Life:** Efficiently sorting a deck of cards

---

#### Big O Comparison Chart

```
From Fastest to Slowest:

O(1)      - Instant! ⚡
O(log n)  - Very Fast 🚀
O(n)      - Fast 🏃
O(n log n)- Moderate 🚶
O(n²)     - Slow 🐢
O(n³)     - Very Slow 🐌
O(2ⁿ)     - Extremely Slow 🦥
O(n!)     - Impossibly Slow 💀
```

#### Visual Understanding

For n = 100:
```
O(1)      = 1 operation
O(log n)  = 7 operations
O(n)      = 100 operations
O(n log n)= 700 operations
O(n²)     = 10,000 operations
O(2ⁿ)     = 1,267,650,600,228,229,401,496,703,205,376 operations 💀
```

---

## Hour 2: More Notations and Practice

---

### Part 4: Big Omega (Ω) Notation (15 mins)

#### What is Big Omega?

Big O says: "**At most** this much time" (Upper bound)  
Big Omega says: "**At least** this much time" (Lower bound)

**Think:** Big O = Maximum speed limit, Big Omega = Minimum speed limit

#### Example

```javascript
function findElement(arr, target) {
    for(let i = 0; i < arr.length; i++) {
        if(arr[i] === target) return i;
    }
    return -1;
}
```

**Best Case (Ω):** Element at first position = **Ω(1)**  
**Worst Case (O):** Element at last position = **O(n)**

#### When to Use?

- Big O: Most common (worst case)
- Big Omega: When you want to show best case
- Used less in practice

---

### Part 5: Big Theta (Θ) Notation (15 mins)

#### What is Big Theta?

When **Best Case = Worst Case**, we use Theta!

**Think:** Algorithm takes EXACTLY this much time (tight bound)

#### Example 1: Print All Elements

```javascript
function printAll(arr) {
    for(let i = 0; i < arr.length; i++) {
        console.log(arr[i]);
    }
}
```

- Best Case: Must print all n elements = Ω(n)
- Worst Case: Must print all n elements = O(n)
- Both same? Yes! So **Θ(n)**

#### Example 2: Find Element

```javascript
function findElement(arr, target) {
    for(let i = 0; i < arr.length; i++) {
        if(arr[i] === target) return i;
    }
    return -1;
}
```

- Best Case: Ω(1) - found at first
- Worst Case: O(n) - found at last
- Both same? NO! So **NO Theta** (can't use)

#### Summary

```
Big O (O)     = Upper Bound = "At most"    = Worst Case
Big Omega (Ω) = Lower Bound = "At least"   = Best Case  
Big Theta (Θ) = Tight Bound = "Exactly"    = Both same
```

---

### Part 6: Practice - Find Time Complexity (30 mins)

#### Example 1: Simple Loop

```javascript
function example1(n) {
    for(let i = 0; i < n; i++) {
        console.log(i);
    }
}
```

**Analysis:**
- Loop runs n times
- Each iteration: 1 operation
- Total: n operations
- **Answer: O(n)**

---

#### Example 2: Nested Loop

```javascript
function example2(n) {
    for(let i = 0; i < n; i++) {
        for(let j = 0; j < n; j++) {
            console.log(i, j);
        }
    }
}
```

**Analysis:**
- Outer loop: n times
- Inner loop: n times for each outer
- Total: n × n = n²
- **Answer: O(n²)**

---

#### Example 3: Two Separate Loops

```javascript
function example3(n) {
    for(let i = 0; i < n; i++) {
        console.log(i);
    }
    
    for(let j = 0; j < n; j++) {
        console.log(j);
    }
}
```

**Analysis:**
- First loop: n operations
- Second loop: n operations
- Total: n + n = 2n
- Drop constant: **Answer: O(n)**

---

#### Example 4: Loop with Division

```javascript
function example4(n) {
    for(let i = n; i > 1; i = i / 2) {
        console.log(i);
    }
}
```

**Analysis:**
- i starts at n
- Each iteration: i = i/2
- n → n/2 → n/4 → n/8 → ... → 1
- How many divisions? log₂(n)
- **Answer: O(log n)**

---

#### Example 5: Constant Operations

```javascript
function example5(arr) {
    console.log(arr[0]);
    console.log(arr[1]);
    console.log(arr[2]);
}
```

**Analysis:**
- 3 operations only
- No loop, no recursion
- Same operations regardless of array size
- **Answer: O(1)**

---

#### Example 6: Mixed Complexity

```javascript
function example6(n) {
    for(let i = 0; i < n; i++) {       // O(n)
        console.log(i);
    }
    
    for(let i = 0; i < n; i++) {       // O(n²)
        for(let j = 0; j < n; j++) {
            console.log(i, j);
        }
    }
}
```

**Analysis:**
- First part: O(n)
- Second part: O(n²)
- Total: O(n) + O(n²) = O(n²)
- Take highest order
- **Answer: O(n²)**

---

## Quick Rules for Finding Big O

### Rule 1: Drop Constants
O(2n) → **O(n)**  
O(3n² + 5n) → **O(n²)**

### Rule 2: Drop Lower Order Terms
O(n² + n) → **O(n²)**  
O(n³ + n² + n) → **O(n³)**

### Rule 3: Different Inputs = Different Variables
```javascript
function example(arr1, arr2) {
    for(let i = 0; i < arr1.length; i++) {}  // O(n)
    for(let j = 0; j < arr2.length; j++) {}  // O(m)
}
// Answer: O(n + m), NOT O(n)
```

### Rule 4: Nested Loops = Multiply
```javascript
for(let i = 0; i < n; i++) {
    for(let j = 0; j < n; j++) {
        // O(n × n) = O(n²)
    }
}
```

### Rule 5: Sequential Loops = Add
```javascript
for(let i = 0; i < n; i++) {}  // O(n)
for(let j = 0; j < n; j++) {}  // O(n)
// Total: O(n + n) = O(n)
```

---

## Day 1 Summary - Key Takeaways

✅ **Time Complexity** = How algorithm's time grows with input size

✅ **Best Case** = Minimum operations (lucky scenario)  
✅ **Worst Case** = Maximum operations (unlucky scenario)  
✅ **Average Case** = Expected operations (normal scenario)

✅ **Big O (O)** = Upper bound = "At most" = Most used!  
✅ **Big Omega (Ω)** = Lower bound = "At least"  
✅ **Big Theta (Θ)** = Tight bound = "Exactly"

✅ **Common Complexities:**
- O(1) - Constant
- O(log n) - Logarithmic  
- O(n) - Linear
- O(n log n) - Linearithmic
- O(n²) - Quadratic

✅ **Rules:**
- Drop constants
- Drop lower terms
- Different inputs = different variables
- Nested = multiply, Sequential = add

---

## Practice Problems for Day 1

Try finding time complexity of these:

```javascript
// Problem 1
function prob1(n) {
    let sum = 0;
    for(let i = 0; i < n; i++) {
        sum += i;
    }
    return sum;
}

// Problem 2
function prob2(n) {
    for(let i = 1; i < n; i = i * 2) {
        console.log(i);
    }
}

// Problem 3
function prob3(n) {
    for(let i = 0; i < n; i++) {
        for(let j = 0; j < i; j++) {
            console.log(i, j);
        }
    }
}

// Problem 4
function prob4(arr) {
    if(arr.length === 0) return;
    console.log(arr[0]);
}

// Problem 5
function prob5(n) {
    for(let i = 0; i < n; i++) {
        for(let j = 0; j < 100; j++) {
            console.log(i, j);
        }
    }
}
```

**Answers:**
1. O(n)
2. O(log n)
3. O(n²)
4. O(1)
5. O(n) - inner loop is constant!

---

## Tomorrow: Day 2
- Space Complexity
- Auxiliary Space vs Total Space
- Amortized Analysis
- Complete Revision

**Good luck! Practice the examples! 🚀**