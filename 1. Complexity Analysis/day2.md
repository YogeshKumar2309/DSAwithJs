# Day 2: Space Complexity & Amortized Analysis - Beginner's Guide

**Duration: 2 Hours**  
**Goal: Understand memory usage and special time analysis**

---

## Hour 1: Space Complexity

---

### Part 1: What is Space Complexity? (20 mins)

#### Yesterday vs Today

**Yesterday (Day 1):** How much **TIME** does algorithm take?  
**Today (Day 2):** How much **MEMORY/SPACE** does algorithm use?

#### The Problem

Imagine you're solving a puzzle:
- **Method 1:** Keep all pieces on table (needs big table)
- **Method 2:** Keep only current pieces, store rest in box (needs small table)

Which uses less space? That's Space Complexity!

#### Definition

**Space Complexity** = Total memory used by algorithm as input grows

#### What Takes Space?

1. **Input Data** - The array/list you're working with
2. **Variables** - int, float, boolean you create
3. **Data Structures** - Arrays, objects you create
4. **Function Calls** - Recursion stack
5. **Return Values** - What function returns

---

### Part 2: Understanding Space with Examples (30 mins)

#### Example 1: O(1) - Constant Space ⚡

```javascript
function sum(arr) {
    let total = 0;           // 1 variable
    
    for(let i = 0; i < arr.length; i++) {  // 1 variable (i)
        total += arr[i];
    }
    
    return total;
}

// Input: [1, 2, 3, 4, 5]
```

**Space Analysis:**
- `total` = 1 variable
- `i` = 1 variable
- No new array created
- No recursion
- Total extra space = 2 variables = **O(1)**

**Key Point:** Loop doesn't create new space each iteration!

---

#### Example 2: O(n) - Linear Space 📈

```javascript
function doubleArray(arr) {
    let result = [];         // New array
    
    for(let i = 0; i < arr.length; i++) {
        result.push(arr[i] * 2);  // Adding n elements
    }
    
    return result;
}

// Input: [1, 2, 3, 4, 5]
// Output: [2, 4, 6, 8, 10]
```

**Space Analysis:**
- `result` array = n elements
- `i` = 1 variable
- Total extra space = n + 1 ≈ **O(n)**

**Key Point:** Creating new array of size n = O(n) space!

---

#### Example 3: O(n) - Recursion Space 🔄

```javascript
function factorial(n) {
    if(n === 0) return 1;           // Base case
    return n * factorial(n - 1);    // Recursive call
}

// factorial(5)
// Call stack:
// factorial(5)
//   factorial(4)
//     factorial(3)
//       factorial(2)
//         factorial(1)
//           factorial(0)
```

**Space Analysis:**
- Each call waits for next call to complete
- Maximum n calls on stack at once
- Total space = **O(n)** for call stack

**Key Point:** Recursion depth = Space complexity!

---

#### Example 4: O(n²) - Quadratic Space 📊

```javascript
function create2DArray(n) {
    let matrix = [];
    
    for(let i = 0; i < n; i++) {
        matrix[i] = [];
        for(let j = 0; j < n; j++) {
            matrix[i][j] = i * j;
        }
    }
    
    return matrix;
}

// n = 3
// Result: [[0,0,0], [0,1,2], [0,2,4]]
```

**Space Analysis:**
- Creating n × n matrix
- Total elements = n²
- Total space = **O(n²)**

**Key Point:** 2D array of size n×n = O(n²) space!

---

#### Example 5: O(log n) - Logarithmic Space 🎯

```javascript
function binarySearchRecursive(arr, target, left, right) {
    if(left > right) return -1;
    
    let mid = Math.floor((left + right) / 2);
    
    if(arr[mid] === target) return mid;
    
    if(arr[mid] > target) {
        return binarySearchRecursive(arr, target, left, mid - 1);
    } else {
        return binarySearchRecursive(arr, target, mid + 1, right);
    }
}

// Each call eliminates half the array
```

**Space Analysis:**
- Recursion depth = log₂(n)
- Each call stores few variables
- Total space = **O(log n)**

**Key Point:** Halving problem each time = O(log n) recursive calls!

---

### Part 3: Auxiliary Space vs Total Space (30 mins)

#### What's the Difference?

Think of cooking:
- **Total Space** = All ingredients + cooking utensils + plates
- **Auxiliary Space** = Only the extra utensils you needed (not ingredients)

#### Definitions

**Total Space** = Input Space + Auxiliary Space  
**Auxiliary Space** = Extra space used (excluding input)

**Important:** We usually care about **Auxiliary Space**!

---

#### Example 1: Understanding the Difference

```javascript
function reverseArray(arr) {
    let reversed = [];                    // Extra array
    
    for(let i = arr.length - 1; i >= 0; i--) {
        reversed.push(arr[i]);
    }
    
    return reversed;
}

// Input: [1, 2, 3, 4, 5]
```

**Space Analysis:**

**Input Space:**
- `arr` = n elements = O(n)

**Auxiliary Space:**
- `reversed` = n elements = O(n)
- `i` = 1 variable = O(1)
- Total auxiliary = **O(n)**

**Total Space:**
- Input + Auxiliary = O(n) + O(n) = **O(n)**

**What we report:** Auxiliary Space = **O(n)**

---

#### Example 2: In-Place Algorithm

```javascript
function reverseInPlace(arr) {
    let left = 0;
    let right = arr.length - 1;
    
    while(left < right) {
        // Swap elements
        let temp = arr[left];
        arr[left] = arr[right];
        arr[right] = temp;
        
        left++;
        right--;
    }
    
    return arr;
}

// Input: [1, 2, 3, 4, 5]
// Output: [5, 4, 3, 2, 1] (same array modified)
```

**Space Analysis:**

**Input Space:**
- `arr` = n elements = O(n)

**Auxiliary Space:**
- `left` = 1 variable
- `right` = 1 variable
- `temp` = 1 variable
- Total auxiliary = **O(1)**

**Total Space:**
- O(n) + O(1) = **O(n)**

**What we report:** Auxiliary Space = **O(1)**

**This is "In-Place" algorithm!** ✅

---

#### Example 3: Comparing Two Approaches

**Approach 1: Extra Space**
```javascript
function removeDuplicates1(arr) {
    let unique = [];
    
    for(let i = 0; i < arr.length; i++) {
        if(!unique.includes(arr[i])) {
            unique.push(arr[i]);
        }
    }
    
    return unique;
}

// Auxiliary Space: O(n) - new array
```

**Approach 2: In-Place**
```javascript
function removeDuplicates2(arr) {
    // Assuming sorted array
    let i = 0;
    
    for(let j = 1; j < arr.length; j++) {
        if(arr[j] !== arr[i]) {
            i++;
            arr[i] = arr[j];
        }
    }
    
    arr.length = i + 1;  // Trim array
    return arr;
}

// Auxiliary Space: O(1) - in-place
```

**Which is better?**
- Approach 2 uses **O(1) auxiliary space** ✅
- More memory efficient!

---

### Quick Comparison Table

| Algorithm | Input Space | Auxiliary Space | Total Space |
|-----------|-------------|-----------------|-------------|
| Sum array | O(n) | O(1) | O(n) |
| Copy array | O(n) | O(n) | O(n) |
| Reverse in-place | O(n) | O(1) | O(n) |
| Factorial recursive | O(1) | O(n) | O(n) |
| 2D matrix | O(1) | O(n²) | O(n²) |

---

## Hour 2: Amortized Analysis

---

### Part 1: What is Amortized Analysis? (20 mins)

#### The Problem

Sometimes an operation is:
- Usually fast (cheap)
- Occasionally slow (expensive)

How do we measure its "average" cost?

#### Real-Life Example: Coffee Shop ☕

**Scenario:** You buy coffee daily
- **Most days:** Pay ₹50 (normal)
- **Every 10th day:** Free coffee! (reward card)

**Cost per coffee over 10 days:**
- Total paid = 9 × ₹50 = ₹450
- Total coffees = 10
- **Amortized cost = ₹450 / 10 = ₹45 per coffee**

Not ₹50, not ₹0, but **average ₹45**!

#### Definition

**Amortized Analysis** = Average cost per operation over a sequence of operations

**Not the same as Average Case!**
- Average Case = Probability-based
- Amortized = Worst case averaged over many operations

---

### Part 2: Dynamic Array Example (40 mins)

#### The Classic Problem: Array Doubling

When array is full, we need to resize it!

```javascript
class DynamicArray {
    constructor() {
        this.array = new Array(1);  // Start with size 1
        this.size = 0;              // Number of elements
        this.capacity = 1;          // Current capacity
    }
    
    push(value) {
        // If array is full, double its size
        if(this.size === this.capacity) {
            this.resize();
        }
        
        this.array[this.size] = value;
        this.size++;
    }
    
    resize() {
        // Create new array with double capacity
        let newCapacity = this.capacity * 2;
        let newArray = new Array(newCapacity);
        
        // Copy all elements
        for(let i = 0; i < this.size; i++) {
            newArray[i] = this.array[i];
        }
        
        this.array = newArray;
        this.capacity = newCapacity;
    }
}
```

#### Cost Analysis

Let's add 8 elements: [A, B, C, D, E, F, G, H]

| Operation | Capacity Before | Need Resize? | Copy Cost | Insert Cost | Total Cost |
|-----------|-----------------|--------------|-----------|-------------|------------|
| push(A) | 1 | No | 0 | 1 | 1 |
| push(B) | 1 | Yes | 1 | 1 | 2 |
| push(C) | 2 | No | 0 | 1 | 1 |
| push(D) | 2 | Yes | 2 | 1 | 3 |
| push(E) | 4 | No | 0 | 1 | 1 |
| push(F) | 4 | No | 0 | 1 | 1 |
| push(G) | 4 | No | 0 | 1 | 1 |
| push(H) | 4 | Yes | 4 | 1 | 5 |

**Total cost for 8 operations = 1+2+1+3+1+1+1+5 = 15**

**Amortized cost per operation = 15/8 ≈ 1.875 ≈ O(1)**

---

#### Why is it O(1) Amortized?

**The Math:**

For n push operations:
- Resizing happens at: 1, 2, 4, 8, 16, ..., n
- Copy costs: 1 + 2 + 4 + 8 + ... + n/2
- This is geometric series = **2n - 1**

**Total cost:**
- Regular inserts: n
- Copy costs: 2n - 1
- Total = n + 2n - 1 = **3n - 1**

**Amortized cost per operation:**
- (3n - 1) / n ≈ **3 = O(1)** ✅

**Key Insight:** Expensive operations are rare enough that when averaged, cost is constant!

---

#### Visual Understanding

```
Think of it like saving money:

Every push operation:
- "Pay" 3 coins (amortized cost)
- Use 1 coin for insert
- Save 2 coins for future resize

When resize needed:
- Use saved coins to pay for copying
- Always enough coins saved!

This way, each operation effectively costs 3 coins = O(1)!
```

---

### Part 3: More Amortized Examples (20 mins)

#### Example 1: Stack with Two Operations

```javascript
class Stack {
    constructor() {
        this.items = [];
    }
    
    push(x) {
        this.items.push(x);  // O(1) amortized
    }
    
    pop() {
        return this.items.pop();  // O(1) worst case
    }
    
    multipop(k) {
        // Pop k elements or until empty
        while(k > 0 && this.items.length > 0) {
            this.pop();
            k--;
        }
    }
}
```

**Analysis:**
- `push`: O(1)
- `pop`: O(1)
- `multipop(k)`: O(k) worst case

**Amortized Analysis:**
- Can't pop more elements than pushed
- If we do n operations total
- Maximum pops = n (all push then all pop)
- **Amortized cost per operation = O(1)**

---

#### Example 2: Binary Counter

Incrementing a binary counter:

```
0000 -> 0001  (flip 1 bit)
0001 -> 0010  (flip 2 bits)
0010 -> 0011  (flip 1 bit)
0011 -> 0100  (flip 3 bits)
0100 -> 0101  (flip 1 bit)
...
```

**Observation:**
- Bit 0 flips every operation
- Bit 1 flips every 2 operations
- Bit 2 flips every 4 operations
- Bit k flips every 2^k operations

**For n increments:**
- Total flips = n/1 + n/2 + n/4 + n/8 + ...
- This sums to **2n**

**Amortized cost = 2n / n = O(1)** per increment!

---

### Part 4: When to Use Amortized Analysis? (10 mins)

#### Use Cases

✅ **Dynamic Arrays** - Resizing  
✅ **Hash Tables** - Rehashing  
✅ **Splay Trees** - Balancing  
✅ **Disjoint Sets** - Path compression  
✅ **Queue with Two Stacks** - Transfer operations

#### Important Points

1. **Amortized ≠ Average Case**
   - Amortized: Worst case averaged
   - Average: Probability-based

2. **Individual Operation Can Be Expensive**
   - But averaged over sequence, it's cheap

3. **Used for Data Structures**
   - Where occasional expensive ops are needed
   - But most ops are cheap

4. **Real-World Impact**
   - JavaScript arrays use dynamic resizing
   - That's why `.push()` is "practically" O(1)!

---

## Practice Problems - Hour 2

### Problem 1: Find Space Complexity

```javascript
function mystery1(n) {
    let arr = new Array(n);
    for(let i = 0; i < n; i++) {
        arr[i] = i * 2;
    }
    return arr;
}
```

**Answer:** Auxiliary Space = O(n)

---

### Problem 2: Find Space Complexity

```javascript
function mystery2(n) {
    if(n <= 1) return n;
    return mystery2(n-1) + mystery2(n-2);
}
```

**Answer:** Space = O(n) - recursion depth (call stack)

---

### Problem 3: Compare Two Approaches

```javascript
// Approach A
function findMaxA(arr) {
    let sorted = [...arr].sort((a,b) => b-a);
    return sorted[0];
}

// Approach B
function findMaxB(arr) {
    let max = arr[0];
    for(let i = 1; i < arr.length; i++) {
        if(arr[i] > max) max = arr[i];
    }
    return max;
}
```

**Answer:**
- Approach A: O(n) space (creates copy)
- Approach B: O(1) space (in-place) ✅ Better!

---

### Problem 4: Auxiliary vs Total Space

```javascript
function process(arr) {
    let sum = 0;
    let count = 0;
    
    for(let i = 0; i < arr.length; i++) {
        sum += arr[i];
        count++;
    }
    
    return sum / count;
}
```

**Answer:**
- Input Space: O(n)
- Auxiliary Space: O(1)
- Total Space: O(n)

---

### Problem 5: True or False?

**Statement:** "An O(n) worst-case operation can have O(1) amortized cost."

**Answer:** TRUE ✅

**Example:** Dynamic array resizing
- Single resize: O(n)
- Amortized over many operations: O(1)

---

## Day 2 Summary - Key Takeaways

### Space Complexity

✅ **Space Complexity** = Memory used by algorithm

✅ **What uses space:**
- Variables
- Arrays/Objects
- Recursion call stack
- Return values

✅ **Common Space Complexities:**
- O(1) - Constant (few variables)
- O(log n) - Logarithmic (binary recursion)
- O(n) - Linear (array or n-depth recursion)
- O(n²) - Quadratic (2D matrix)

---

### Auxiliary vs Total Space

✅ **Total Space** = Input + Auxiliary  
✅ **Auxiliary Space** = Extra space (excluding input)  
✅ **We usually report Auxiliary Space**

✅ **In-Place Algorithm** = O(1) auxiliary space
- Modifies input directly
- Uses only few extra variables

---

### Amortized Analysis

✅ **Amortized Cost** = Average cost over sequence of operations

✅ **Not same as Average Case:**
- Amortized: Worst case averaged
- Average Case: Probability-based

✅ **Key Example:** Dynamic Array
- Single resize: O(n)
- Amortized push: O(1)

✅ **Why it matters:**
- Real data structures use this
- JavaScript arrays, hash tables, etc.

---

## Complete Day 1 + Day 2 Revision

### Time Complexity (Day 1)
- O(1), O(log n), O(n), O(n log n), O(n²)
- Best, Worst, Average cases
- Big O, Omega, Theta

### Space Complexity (Day 2)
- Auxiliary vs Total space
- In-place algorithms
- Recursion space = call stack depth

### Amortized Analysis (Day 2)
- Average cost over operations
- Dynamic array example
- Why push() is O(1) amortized

---

## What's Next?

**Day 3 onwards:** Arrays!

You now understand:
- ✅ How to measure TIME
- ✅ How to measure SPACE
- ✅ How to analyze algorithms

**You're ready for data structures!** 🚀

---

## Final Practice: Analyze This Code

```javascript
function complexFunction(n) {
    // Part 1
    let result = [];
    for(let i = 0; i < n; i++) {
        result.push(i);
    }
    
    // Part 2
    for(let i = 0; i < n; i++) {
        for(let j = 0; j < n; j++) {
            console.log(i, j);
        }
    }
    
    // Part 3
    function helper(x) {
        if(x <= 0) return;
        helper(x - 1);
    }
    helper(n);
    
    return result;
}
```

**Find:**
1. Time Complexity?
2. Space Complexity?
3. Auxiliary Space?

**Answers:**
1. Time: O(n²) - dominated by nested loop
2. Space: O(n) - result array + recursion stack
3. Auxiliary: O(n) - result array (n) + call stack (n)

---

**Congratulations! 🎉 Day 2 Complete!**

Ab tum Time aur Space dono analyze kar sakte ho! 💪