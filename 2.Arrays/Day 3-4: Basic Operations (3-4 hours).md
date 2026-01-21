# Day 3-4: Array Basic Operations - Complete Guide

**Duration: 3-4 hours**  
**Goal: Master fundamental array operations in JavaScript**

---

## What is an Array?

**Array** = Collection of elements stored at contiguous memory locations

**Think of it like:** A row of boxes, each box has:
- **Index** (position number starting from 0)
- **Value** (the item stored)

```
Index:  0    1    2    3    4
Array: [10] [20] [30] [40] [50]
```

**Key Points:**
- Arrays are **zero-indexed** (first element is at index 0)
- Fixed size in some languages, but **dynamic in JavaScript**
- Random access: Can access any element directly using index

---

## Part 1: Traversal (30 mins)

### What is Traversal?

**Traversal** = Visiting each element of array one by one

**Real Life Example:** Checking attendance - call each student's name one by one

---

### Method 1: For Loop (Most Common)

```javascript
function traverseArray(arr) {
    for (let i = 0; i < arr.length; i++) {
        console.log(`Index ${i}: ${arr[i]}`);
    }
}

// Example
const numbers = [10, 20, 30, 40, 50];
traverseArray(numbers);

// Output:
// Index 0: 10
// Index 1: 20
// Index 2: 30
// Index 3: 40
// Index 4: 50
```

**Time Complexity:** O(n) - visits each element once  
**Space Complexity:** O(1) - only uses variable `i`

---

### Method 2: For...of Loop (Modern JavaScript)

```javascript
function traverseWithForOf(arr) {
    for (let element of arr) {
        console.log(element);
    }
}

// Example
const fruits = ['apple', 'banana', 'orange'];
traverseWithForOf(fruits);

// Output:
// apple
// banana
// orange
```

**When to use:** When you don't need index, just the values

---

### Method 3: forEach Method

```javascript
function traverseWithForEach(arr) {
    arr.forEach((element, index) => {
        console.log(`Index ${index}: ${element}`);
    });
}

// Example
const colors = ['red', 'green', 'blue'];
traverseWithForEach(colors);

// Output:
// Index 0: red
// Index 1: green
// Index 2: blue
```

**When to use:** Functional programming style, cleaner code

---

### Method 4: While Loop

```javascript
function traverseWithWhile(arr) {
    let i = 0;
    while (i < arr.length) {
        console.log(arr[i]);
        i++;
    }
}

// Example
const nums = [1, 2, 3, 4, 5];
traverseWithWhile(nums);
```

---

### Practice Problem 1: Sum of Array Elements

**Problem:** Calculate sum of all elements in array

```javascript
function sumArray(arr) {
    let sum = 0;
    
    for (let i = 0; i < arr.length; i++) {
        sum += arr[i];
    }
    
    return sum;
}

// Test
console.log(sumArray([1, 2, 3, 4, 5]));  // Output: 15
console.log(sumArray([10, 20, 30]));      // Output: 60
```

**Time:** O(n)  
**Space:** O(1)

---

### Practice Problem 2: Find Maximum Element

**Problem:** Find the largest element in array

```javascript
function findMax(arr) {
    if (arr.length === 0) return null;
    
    let max = arr[0];  // Assume first element is max
    
    for (let i = 1; i < arr.length; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    
    return max;
}

// Test
console.log(findMax([3, 7, 2, 9, 1]));   // Output: 9
console.log(findMax([10, 5, 20, 15]));   // Output: 20
```

**Time:** O(n)  
**Space:** O(1)

---

### Practice Problem 3: Print Even Numbers

**Problem:** Print only even numbers from array

```javascript
function printEvenNumbers(arr) {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] % 2 === 0) {  // Check if divisible by 2
            console.log(arr[i]);
        }
    }
}

// Test
printEvenNumbers([1, 2, 3, 4, 5, 6, 7, 8]);
// Output:
// 2
// 4
// 6
// 8
```

---

## Part 2: Insertion (45 mins)

### What is Insertion?

**Insertion** = Adding a new element to the array

**3 Types:**
1. At beginning
2. At end
3. At specific position

---

### Type 1: Insert at Beginning

**Problem:** Add element at index 0

**Approach:** Shift all elements to the right, then insert

```javascript
function insertAtBeginning(arr, element) {
    // Method 1: Using unshift (Built-in)
    arr.unshift(element);
    return arr;
}

// Test
let arr1 = [2, 3, 4, 5];
insertAtBeginning(arr1, 1);
console.log(arr1);  // Output: [1, 2, 3, 4, 5]
```

**Time Complexity:** O(n) - all elements shift  
**Space Complexity:** O(1)

---

**Manual Implementation (Understanding how it works):**

```javascript
function insertAtBeginningManual(arr, element) {
    // Create new array with extra space
    let newArr = new Array(arr.length + 1);
    
    // Insert new element at first position
    newArr[0] = element;
    
    // Copy all old elements shifted by 1
    for (let i = 0; i < arr.length; i++) {
        newArr[i + 1] = arr[i];
    }
    
    return newArr;
}

// Test
let arr2 = [2, 3, 4, 5];
let result = insertAtBeginningManual(arr2, 1);
console.log(result);  // Output: [1, 2, 3, 4, 5]
```

**Visual Example:**
```
Original: [2, 3, 4, 5]
Insert 1 at beginning:

Step 1: Create space [_, _, _, _, _]
Step 2: Insert 1    [1, _, _, _, _]
Step 3: Copy rest   [1, 2, 3, 4, 5]
```

---

### Type 2: Insert at End

**Problem:** Add element at last position

**Approach:** Simply add at end

```javascript
function insertAtEnd(arr, element) {
    // Method 1: Using push (Built-in)
    arr.push(element);
    return arr;
}

// Test
let arr3 = [1, 2, 3, 4];
insertAtEnd(arr3, 5);
console.log(arr3);  // Output: [1, 2, 3, 4, 5]
```

**Time Complexity:** O(1) - no shifting needed  
**Space Complexity:** O(1)

---

**Manual Implementation:**

```javascript
function insertAtEndManual(arr, element) {
    // Simply assign at length index
    arr[arr.length] = element;
    return arr;
}

// Test
let arr4 = [1, 2, 3, 4];
insertAtEndManual(arr4, 5);
console.log(arr4);  // Output: [1, 2, 3, 4, 5]
```

**Visual Example:**
```
Original: [1, 2, 3, 4]
Insert 5 at end:

[1, 2, 3, 4, 5]  ← Just add at the end!
```

---

### Type 3: Insert at Specific Position

**Problem:** Add element at any given index

**Approach:** Shift elements from that position to right, then insert

```javascript
function insertAtPosition(arr, element, position) {
    // Check if position is valid
    if (position < 0 || position > arr.length) {
        console.log("Invalid position");
        return arr;
    }
    
    // Method 1: Using splice
    arr.splice(position, 0, element);
    return arr;
}

// Test
let arr5 = [1, 2, 4, 5];
insertAtPosition(arr5, 3, 2);  // Insert 3 at index 2
console.log(arr5);  // Output: [1, 2, 3, 4, 5]
```

**Time Complexity:** O(n) - may need to shift elements  
**Space Complexity:** O(1)

---

**Manual Implementation:**

```javascript
function insertAtPositionManual(arr, element, position) {
    // Create new array with extra space
    let newArr = new Array(arr.length + 1);
    
    // Copy elements before position
    for (let i = 0; i < position; i++) {
        newArr[i] = arr[i];
    }
    
    // Insert new element
    newArr[position] = element;
    
    // Copy remaining elements
    for (let i = position; i < arr.length; i++) {
        newArr[i + 1] = arr[i];
    }
    
    return newArr;
}

// Test
let arr6 = [1, 2, 4, 5];
let result2 = insertAtPositionManual(arr6, 3, 2);
console.log(result2);  // Output: [1, 2, 3, 4, 5]
```

**Visual Example:**
```
Original: [1, 2, 4, 5]
Insert 3 at index 2:

Index:     0  1  2  3  4
Step 1:   [1, 2, _, _, _]  Copy before position
Step 2:   [1, 2, 3, _, _]  Insert element
Step 3:   [1, 2, 3, 4, 5]  Copy rest (shifted)
```

---

### Practice Problem 4: Insert Multiple Elements

**Problem:** Insert multiple elements at once at the end

```javascript
function insertMultiple(arr, elements) {
    for (let element of elements) {
        arr.push(element);
    }
    return arr;
}

// Test
let arr7 = [1, 2, 3];
insertMultiple(arr7, [4, 5, 6]);
console.log(arr7);  // Output: [1, 2, 3, 4, 5, 6]

// Better way: Using spread operator
let arr8 = [1, 2, 3];
arr8.push(...[4, 5, 6]);
console.log(arr8);  // Output: [1, 2, 3, 4, 5, 6]
```

---

## Part 3: Deletion (45 mins)

### What is Deletion?

**Deletion** = Removing an element from the array

**3 Types:**
1. From beginning
2. From end
3. From specific position

---

### Type 1: Delete from Beginning

**Problem:** Remove first element

**Approach:** Shift all elements to the left

```javascript
function deleteFromBeginning(arr) {
    // Method 1: Using shift (Built-in)
    let removed = arr.shift();
    console.log("Removed:", removed);
    return arr;
}

// Test
let arr9 = [1, 2, 3, 4, 5];
deleteFromBeginning(arr9);
console.log(arr9);  // Output: [2, 3, 4, 5]
```

**Time Complexity:** O(n) - all elements shift left  
**Space Complexity:** O(1)

---

**Manual Implementation:**

```javascript
function deleteFromBeginningManual(arr) {
    if (arr.length === 0) return arr;
    
    // Shift all elements one position left
    for (let i = 0; i < arr.length - 1; i++) {
        arr[i] = arr[i + 1];
    }
    
    // Remove last element (duplicate now)
    arr.length = arr.length - 1;
    
    return arr;
}

// Test
let arr10 = [1, 2, 3, 4, 5];
deleteFromBeginningManual(arr10);
console.log(arr10);  // Output: [2, 3, 4, 5]
```

**Visual Example:**
```
Original: [1, 2, 3, 4, 5]
Delete from beginning:

Step 1: [2, 2, 3, 4, 5]  Shift element at index 1 to 0
Step 2: [2, 3, 3, 4, 5]  Shift element at index 2 to 1
Step 3: [2, 3, 4, 4, 5]  Shift element at index 3 to 2
Step 4: [2, 3, 4, 5, 5]  Shift element at index 4 to 3
Step 5: [2, 3, 4, 5]     Remove last duplicate
```

---

### Type 2: Delete from End

**Problem:** Remove last element

**Approach:** Simply remove last element

```javascript
function deleteFromEnd(arr) {
    // Method 1: Using pop (Built-in)
    let removed = arr.pop();
    console.log("Removed:", removed);
    return arr;
}

// Test
let arr11 = [1, 2, 3, 4, 5];
deleteFromEnd(arr11);
console.log(arr11);  // Output: [1, 2, 3, 4]
```

**Time Complexity:** O(1) - no shifting needed  
**Space Complexity:** O(1)

---

**Manual Implementation:**

```javascript
function deleteFromEndManual(arr) {
    if (arr.length === 0) return arr;
    
    // Just reduce the length
    arr.length = arr.length - 1;
    
    return arr;
}

// Test
let arr12 = [1, 2, 3, 4, 5];
deleteFromEndManual(arr12);
console.log(arr12);  // Output: [1, 2, 3, 4]
```

**Visual Example:**
```
Original: [1, 2, 3, 4, 5]
Delete from end:

[1, 2, 3, 4]  ← Just remove last!
```

---

### Type 3: Delete from Specific Position

**Problem:** Remove element at given index

**Approach:** Shift all elements after that position to left

```javascript
function deleteFromPosition(arr, position) {
    // Check if position is valid
    if (position < 0 || position >= arr.length) {
        console.log("Invalid position");
        return arr;
    }
    
    // Method 1: Using splice
    let removed = arr.splice(position, 1);
    console.log("Removed:", removed[0]);
    return arr;
}

// Test
let arr13 = [1, 2, 3, 4, 5];
deleteFromPosition(arr13, 2);  // Delete element at index 2
console.log(arr13);  // Output: [1, 2, 4, 5]
```

**Time Complexity:** O(n) - may need to shift elements  
**Space Complexity:** O(1)

---

**Manual Implementation:**

```javascript
function deleteFromPositionManual(arr, position) {
    if (position < 0 || position >= arr.length) {
        return arr;
    }
    
    // Shift all elements after position to left
    for (let i = position; i < arr.length - 1; i++) {
        arr[i] = arr[i + 1];
    }
    
    // Reduce length
    arr.length = arr.length - 1;
    
    return arr;
}

// Test
let arr14 = [1, 2, 3, 4, 5];
deleteFromPositionManual(arr14, 2);
console.log(arr14);  // Output: [1, 2, 4, 5]
```

**Visual Example:**
```
Original: [1, 2, 3, 4, 5]
Delete element at index 2 (which is 3):

Index:     0  1  2  3  4
Step 1:   [1, 2, 4, 4, 5]  Shift element at index 3 to 2
Step 2:   [1, 2, 4, 5, 5]  Shift element at index 4 to 3
Step 3:   [1, 2, 4, 5]     Remove last duplicate
```

---

### Practice Problem 5: Remove All Occurrences

**Problem:** Remove all occurrences of a value from array

```javascript
function removeAllOccurrences(arr, value) {
    // Filter out all occurrences
    return arr.filter(element => element !== value);
}

// Test
let arr15 = [1, 2, 3, 2, 4, 2, 5];
let result3 = removeAllOccurrences(arr15, 2);
console.log(result3);  // Output: [1, 3, 4, 5]
```

**Alternative (In-place):**

```javascript
function removeAllOccurrencesInPlace(arr, value) {
    let writeIndex = 0;
    
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] !== value) {
            arr[writeIndex] = arr[i];
            writeIndex++;
        }
    }
    
    // Trim array to new size
    arr.length = writeIndex;
    return arr;
}

// Test
let arr16 = [1, 2, 3, 2, 4, 2, 5];
removeAllOccurrencesInPlace(arr16, 2);
console.log(arr16);  // Output: [1, 3, 4, 5]
```

**Time:** O(n)  
**Space:** O(1) for in-place version

---

## Part 4: Searching (45 mins)

### What is Searching?

**Searching** = Finding if an element exists in array and its position

**2 Main Types:**
1. Linear Search (Unsorted array)
2. Binary Search (Sorted array)

---

### Type 1: Linear Search

**Concept:** Check each element one by one until found

**Use When:** Array is unsorted OR small array

```javascript
function linearSearch(arr, target) {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] === target) {
            return i;  // Return index where found
        }
    }
    return -1;  // Not found
}

// Test
let arr17 = [10, 25, 30, 15, 40];
console.log(linearSearch(arr17, 30));  // Output: 2
console.log(linearSearch(arr17, 50));  // Output: -1
```

**Time Complexity:**
- Best Case: O(1) - element at first position
- Worst Case: O(n) - element at last or not found
- Average Case: O(n)

**Space Complexity:** O(1)

---

**Visual Example:**
```
Array: [10, 25, 30, 15, 40]
Search for 30:

Step 1: Check arr[0] = 10 ≠ 30 ❌
Step 2: Check arr[1] = 25 ≠ 30 ❌
Step 3: Check arr[2] = 30 = 30 ✅ Found at index 2!
```

---

### Practice Problem 6: Find All Occurrences

**Problem:** Find all positions where element exists

```javascript
function findAllOccurrences(arr, target) {
    let positions = [];
    
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] === target) {
            positions.push(i);
        }
    }
    
    return positions;
}

// Test
let arr18 = [10, 25, 30, 25, 40, 25];
console.log(findAllOccurrences(arr18, 25));  // Output: [1, 3, 5]
console.log(findAllOccurrences(arr18, 50));  // Output: []
```

---

### Type 2: Binary Search

**Concept:** Divide array in half repeatedly (Only works on SORTED array)

**Use When:** Array is sorted AND large array

**How it works:**
1. Find middle element
2. If target = middle, found!
3. If target < middle, search left half
4. If target > middle, search right half
5. Repeat until found or no elements left

```javascript
function binarySearch(arr, target) {
    let left = 0;
    let right = arr.length - 1;
    
    while (left <= right) {
        // Find middle index
        let mid = Math.floor((left + right) / 2);
        
        // Check if target is at mid
        if (arr[mid] === target) {
            return mid;
        }
        
        // If target is smaller, search left half
        if (arr[mid] > target) {
            right = mid - 1;
        }
        // If target is larger, search right half
        else {
            left = mid + 1;
        }
    }
    
    return -1;  // Not found
}

// Test (Array MUST be sorted!)
let arr19 = [10, 20, 30, 40, 50, 60, 70];
console.log(binarySearch(arr19, 40));  // Output: 3
console.log(binarySearch(arr19, 25));  // Output: -1
```

**Time Complexity:**
- Best Case: O(1) - element at middle
- Worst Case: O(log n) - keep halving
- Average Case: O(log n)

**Space Complexity:** O(1)

---

**Visual Example:**
```
Array: [10, 20, 30, 40, 50, 60, 70]
Search for 40:

Step 1: left=0, right=6, mid=3
        [10, 20, 30, 40, 50, 60, 70]
                     ↑
        arr[3] = 40 = target ✅ Found!

Search for 20:

Step 1: left=0, right=6, mid=3
        [10, 20, 30, 40, 50, 60, 70]
                     ↑
        arr[3] = 40 > 20, search left half

Step 2: left=0, right=2, mid=1
        [10, 20, 30]
             ↑
        arr[1] = 20 = target ✅ Found!
```

---

**Recursive Binary Search:**

```javascript
function binarySearchRecursive(arr, target, left = 0, right = arr.length - 1) {
    // Base case: element not found
    if (left > right) {
        return -1;
    }
    
    let mid = Math.floor((left + right) / 2);
    
    // Element found
    if (arr[mid] === target) {
        return mid;
    }
    
    // Search left half
    if (arr[mid] > target) {
        return binarySearchRecursive(arr, target, left, mid - 1);
    }
    // Search right half
    else {
        return binarySearchRecursive(arr, target, mid + 1, right);
    }
}

// Test
let arr20 = [10, 20, 30, 40, 50, 60, 70];
console.log(binarySearchRecursive(arr20, 50));  // Output: 4
```

---

### Practice Problem 7: Search in Rotated Sorted Array

**Problem:** Array is sorted but rotated at some pivot

```javascript
// Example: [40, 50, 60, 70, 10, 20, 30] (rotated at index 4)

function searchRotated(arr, target) {
    let left = 0;
    let right = arr.length - 1;
    
    while (left <= right) {
        let mid = Math.floor((left + right) / 2);
        
        if (arr[mid] === target) {
            return mid;
        }
        
        // Check which half is sorted
        if (arr[left] <= arr[mid]) {
            // Left half is sorted
            if (target >= arr[left] && target < arr[mid]) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        } else {
            // Right half is sorted
            if (target > arr[mid] && target <= arr[right]) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
    }
    
    return -1;
}

// Test
let arr21 = [40, 50, 60, 70, 10, 20, 30];
console.log(searchRotated(arr21, 20));  // Output: 5
```

---

## Part 5: Updating (30 mins)

### What is Updating?

**Updating** = Changing value of existing element(s)

---

### Type 1: Update Single Element

**Problem:** Change value at specific index

```javascript
function updateElement(arr, index, newValue) {
    // Check if index is valid
    if (index < 0 || index >= arr.length) {
        console.log("Invalid index");
        return arr;
    }
    
    // Update the value
    arr[index] = newValue;
    return arr;
}

// Test
let arr22 = [10, 20, 30, 40, 50];
updateElement(arr22, 2, 999);
console.log(arr22);  // Output: [10, 20, 999, 40, 50]
```

**Time Complexity:** O(1) - direct access  
**Space Complexity:** O(1)

---

### Type 2: Update Multiple Elements

**Problem:** Update all elements that match a condition

```javascript
function updateMultiple(arr, oldValue, newValue) {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] === oldValue) {
            arr[i] = newValue;
        }
    }
    return arr;
}

// Test
let arr23 = [10, 20, 30, 20, 40, 20];
updateMultiple(arr23, 20, 999);
console.log(arr23);  // Output: [10, 999, 30, 999, 40, 999]
```

**Time Complexity:** O(n) - check each element  
**Space Complexity:** O(1)

---

### Practice Problem 8: Increment All Elements

**Problem:** Add a value to all elements

```javascript
function incrementAll(arr, increment) {
    for (let i = 0; i < arr.length; i++) {
        arr[i] += increment;
    }
    return arr;
}

// Test
let arr24 = [1, 2, 3, 4, 5];
incrementAll(arr24, 10);
console.log(arr24);  // Output: [11, 12, 13, 14, 15]

// Using map (creates new array)
let arr25 = [1, 2, 3, 4, 5];
let result4 = arr25.map(x => x + 10);
console.log(result4);  // Output: [11, 12, 13, 14, 15]
```

---

### Practice Problem 9: Double Even Numbers

**Problem:** Multiply all even numbers by 2

```javascript
function doubleEvenNumbers(arr) {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] % 2 === 0) {  // If even
            arr[i] *= 2;
        }
    }
    return arr;
}

// Test
let arr26 = [1, 2, 3, 4, 5, 6];
doubleEvenNumbers(arr26);
console.log(arr26);  // Output: [1, 4, 3, 8, 5, 12]
```

---

## Final Practice Problems (30-45 mins)

### Problem 10: Reverse Array

**Problem:** Reverse the array in-place

```javascript
function reverseArray(arr) {
    let left = 0;
    let right = arr.length - 1;
    
    while (left < right) {
        // Swap elements
        let temp = arr[left];
        arr[left] = arr[right];
        arr[right] = temp;
        
        left++;
        right--;
    }
    
    return arr;
}

// Test
let arr27 = [1, 2, 3, 4, 5];
reverseArray(arr27);
console.log(arr27);  // Output: [5, 4, 3, 2, 1]
```

**Time:** O(n)  
**Space:** O(1)

---

### Problem 11: Move Zeros to End

**Problem:** Move all 0s to end, maintain order of other elements

```javascript
function moveZerosToEnd(arr) {
    let writeIndex = 0;
    
    // Move all non-zero elements to front
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] !== 0) {
            arr[writeIndex] = arr[i];
            writeIndex++;
        }
    }
    
    // Fill remaining positions with 0
    while (writeIndex < arr.length) {
        arr[writeIndex] = 0;
        writeIndex++;
    }
    
    return arr;
}

// Test
let arr28 = [0, 1, 0, 3, 12, 0, 5];
moveZerosToEnd(arr28);
console.log(arr28);  // Output: [1, 3, 12, 5, 0, 0, 0]
```

**Time:** O(n)  
**Space:** O(1)

---

### Problem 12: Remove Duplicates from Sorted Array

**Problem:** Remove duplicates in-place, return new length

```javascript
function removeDuplicates(arr) {
    if (arr.length === 0) return 0;
    
    let writeIndex = 0;
    
    for (let i = 1; i < arr.length; i++) {
        if (arr[i] !== arr[writeIndex]) {
            writeIndex++;
            arr[writeIndex] = arr[i];
        }
    }
    
    return writeIndex + 1;  // New length
}

// Test
let arr29 = [1, 1, 2, 2, 3, 4, 4, 5];
let newLength = removeDuplicates(arr29);
console.log(newLength);  // Output: 5
console.log(arr29.slice(0, newLength));  // Output:
# Day 3-4: Array Basic Operations - Complete Guide

**Duration: 3-4 hours**  
**Goal: Master fundamental array operations in JavaScript**

---

## What is an Array?

**Array** = Collection of elements stored at contiguous memory locations

**Think of it like:** A row of boxes, each box has:
- **Index** (position number starting from 0)
- **Value** (the item stored)

```
Index:  0    1    2    3    4
Array: [10] [20] [30] [40] [50]
```

**Key Points:**
- Arrays are **zero-indexed** (first element is at index 0)
- Fixed size in some languages, but **dynamic in JavaScript**
- Random access: Can access any element directly using index

---

## Part 1: Traversal (30 mins)

### What is Traversal?

**Traversal** = Visiting each element of array one by one

**Real Life Example:** Checking attendance - call each student's name one by one

---

### Method 1: For Loop (Most Common)

```javascript
function traverseArray(arr) {
    for (let i = 0; i < arr.length; i++) {
        console.log(`Index ${i}: ${arr[i]}`);
    }
}

// Example
const numbers = [10, 20, 30, 40, 50];
traverseArray(numbers);

// Output:
// Index 0: 10
// Index 1: 20
// Index 2: 30
// Index 3: 40
// Index 4: 50
```

**Time Complexity:** O(n) - visits each element once  
**Space Complexity:** O(1) - only uses variable `i`

---

### Method 2: For...of Loop (Modern JavaScript)

```javascript
function traverseWithForOf(arr) {
    for (let element of arr) {
        console.log(element);
    }
}

// Example
const fruits = ['apple', 'banana', 'orange'];
traverseWithForOf(fruits);

// Output:
// apple
// banana
// orange
```

**When to use:** When you don't need index, just the values

---

### Method 3: forEach Method

```javascript
function traverseWithForEach(arr) {
    arr.forEach((element, index) => {
        console.log(`Index ${index}: ${element}`);
    });
}

// Example
const colors = ['red', 'green', 'blue'];
traverseWithForEach(colors);

// Output:
// Index 0: red
// Index 1: green
// Index 2: blue
```

**When to use:** Functional programming style, cleaner code

---

### Method 4: While Loop

```javascript
function traverseWithWhile(arr) {
    let i = 0;
    while (i < arr.length) {
        console.log(arr[i]);
        i++;
    }
}

// Example
const nums = [1, 2, 3, 4, 5];
traverseWithWhile(nums);
```

---

### Practice Problem 1: Sum of Array Elements

**Problem:** Calculate sum of all elements in array

```javascript
function sumArray(arr) {
    let sum = 0;
    
    for (let i = 0; i < arr.length; i++) {
        sum += arr[i];
    }
    
    return sum;
}

// Test
console.log(sumArray([1, 2, 3, 4, 5]));  // Output: 15
console.log(sumArray([10, 20, 30]));      // Output: 60
```

**Time:** O(n)  
**Space:** O(1)

---

### Practice Problem 2: Find Maximum Element

**Problem:** Find the largest element in array

```javascript
function findMax(arr) {
    if (arr.length === 0) return null;
    
    let max = arr[0];  // Assume first element is max
    
    for (let i = 1; i < arr.length; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    
    return max;
}

// Test
console.log(findMax([3, 7, 2, 9, 1]));   // Output: 9
console.log(findMax([10, 5, 20, 15]));   // Output: 20
```

**Time:** O(n)  
**Space:** O(1)

---

### Practice Problem 3: Print Even Numbers

**Problem:** Print only even numbers from array

```javascript
function printEvenNumbers(arr) {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] % 2 === 0) {  // Check if divisible by 2
            console.log(arr[i]);
        }
    }
}

// Test
printEvenNumbers([1, 2, 3, 4, 5, 6, 7, 8]);
// Output:
// 2
// 4
// 6
// 8
```

---

## Part 2: Insertion (45 mins)

### What is Insertion?

**Insertion** = Adding a new element to the array

**3 Types:**
1. At beginning
2. At end
3. At specific position

---

### Type 1: Insert at Beginning

**Problem:** Add element at index 0

**Approach:** Shift all elements to the right, then insert

```javascript
function insertAtBeginning(arr, element) {
    // Method 1: Using unshift (Built-in)
    arr.unshift(element);
    return arr;
}

// Test
let arr1 = [2, 3, 4, 5];
insertAtBeginning(arr1, 1);
console.log(arr1);  // Output: [1, 2, 3, 4, 5]
```

**Time Complexity:** O(n) - all elements shift  
**Space Complexity:** O(1)

---

**Manual Implementation (Understanding how it works):**

```javascript
function insertAtBeginningManual(arr, element) {
    // Create new array with extra space
    let newArr = new Array(arr.length + 1);
    
    // Insert new element at first position
    newArr[0] = element;
    
    // Copy all old elements shifted by 1
    for (let i = 0; i < arr.length; i++) {
        newArr[i + 1] = arr[i];
    }
    
    return newArr;
}

// Test
let arr2 = [2, 3, 4, 5];
let result = insertAtBeginningManual(arr2, 1);
console.log(result);  // Output: [1, 2, 3, 4, 5]
```

**Visual Example:**
```
Original: [2, 3, 4, 5]
Insert 1 at beginning:

Step 1: Create space [_, _, _, _, _]
Step 2: Insert 1    [1, _, _, _, _]
Step 3: Copy rest   [1, 2, 3, 4, 5]
```

---

### Type 2: Insert at End

**Problem:** Add element at last position

**Approach:** Simply add at end

```javascript
function insertAtEnd(arr, element) {
    // Method 1: Using push (Built-in)
    arr.push(element);
    return arr;
}

// Test
let arr3 = [1, 2, 3, 4];
insertAtEnd(arr3, 5);
console.log(arr3);  // Output: [1, 2, 3, 4, 5]
```

**Time Complexity:** O(1) - no shifting needed  
**Space Complexity:** O(1)

---

**Manual Implementation:**

```javascript
function insertAtEndManual(arr, element) {
    // Simply assign at length index
    arr[arr.length] = element;
    return arr;
}

// Test
let arr4 = [1, 2, 3, 4];
insertAtEndManual(arr4, 5);
console.log(arr4);  // Output: [1, 2, 3, 4, 5]
```

**Visual Example:**
```
Original: [1, 2, 3, 4]
Insert 5 at end:

[1, 2, 3, 4, 5]  ← Just add at the end!
```

---

### Type 3: Insert at Specific Position

**Problem:** Add element at any given index

**Approach:** Shift elements from that position to right, then insert

```javascript
function insertAtPosition(arr, element, position) {
    // Check if position is valid
    if (position < 0 || position > arr.length) {
        console.log("Invalid position");
        return arr;
    }
    
    // Method 1: Using splice
    arr.splice(position, 0, element);
    return arr;
}

// Test
let arr5 = [1, 2, 4, 5];
insertAtPosition(arr5, 3, 2);  // Insert 3 at index 2
console.log(arr5);  // Output: [1, 2, 3, 4, 5]
```

**Time Complexity:** O(n) - may need to shift elements  
**Space Complexity:** O(1)

---

**Manual Implementation:**

```javascript
function insertAtPositionManual(arr, element, position) {
    // Create new array with extra space
    let newArr = new Array(arr.length + 1);
    
    // Copy elements before position
    for (let i = 0; i < position; i++) {
        newArr[i] = arr[i];
    }
    
    // Insert new element
    newArr[position] = element;
    
    // Copy remaining elements
    for (let i = position; i < arr.length; i++) {
        newArr[i + 1] = arr[i];
    }
    
    return newArr;
}

// Test
let arr6 = [1, 2, 4, 5];
let result2 = insertAtPositionManual(arr6, 3, 2);
console.log(result2);  // Output: [1, 2, 3, 4, 5]
```

**Visual Example:**
```
Original: [1, 2, 4, 5]
Insert 3 at index 2:

Index:     0  1  2  3  4
Step 1:   [1, 2, _, _, _]  Copy before position
Step 2:   [1, 2, 3, _, _]  Insert element
Step 3:   [1, 2, 3, 4, 5]  Copy rest (shifted)
```

---

### Practice Problem 4: Insert Multiple Elements

**Problem:** Insert multiple elements at once at the end

```javascript
function insertMultiple(arr, elements) {
    for (let element of elements) {
        arr.push(element);
    }
    return arr;
}

// Test
let arr7 = [1, 2, 3];
insertMultiple(arr7, [4, 5, 6]);
console.log(arr7);  // Output: [1, 2, 3, 4, 5, 6]

// Better way: Using spread operator
let arr8 = [1, 2, 3];
arr8.push(...[4, 5, 6]);
console.log(arr8);  // Output: [1, 2, 3, 4, 5, 6]
```

---

## Part 3: Deletion (45 mins)

### What is Deletion?

**Deletion** = Removing an element from the array

**3 Types:**
1. From beginning
2. From end
3. From specific position

---

### Type 1: Delete from Beginning

**Problem:** Remove first element

**Approach:** Shift all elements to the left

```javascript
function deleteFromBeginning(arr) {
    // Method 1: Using shift (Built-in)
    let removed = arr.shift();
    console.log("Removed:", removed);
    return arr;
}

// Test
let arr9 = [1, 2, 3, 4, 5];
deleteFromBeginning(arr9);
console.log(arr9);  // Output: [2, 3, 4, 5]
```

**Time Complexity:** O(n) - all elements shift left  
**Space Complexity:** O(1)

---

**Manual Implementation:**

```javascript
function deleteFromBeginningManual(arr) {
    if (arr.length === 0) return arr;
    
    // Shift all elements one position left
    for (let i = 0; i < arr.length - 1; i++) {
        arr[i] = arr[i + 1];
    }
    
    // Remove last element (duplicate now)
    arr.length = arr.length - 1;
    
    return arr;
}

// Test
let arr10 = [1, 2, 3, 4, 5];
deleteFromBeginningManual(arr10);
console.log(arr10);  // Output: [2, 3, 4, 5]
```

**Visual Example:**
```
Original: [1, 2, 3, 4, 5]
Delete from beginning:

Step 1: [2, 2, 3, 4, 5]  Shift element at index 1 to 0
Step 2: [2, 3, 3, 4, 5]  Shift element at index 2 to 1
Step 3: [2, 3, 4, 4, 5]  Shift element at index 3 to 2
Step 4: [2, 3, 4, 5, 5]  Shift element at index 4 to 3
Step 5: [2, 3, 4, 5]     Remove last duplicate
```

---

### Type 2: Delete from End

**Problem:** Remove last element

**Approach:** Simply remove last element

```javascript
function deleteFromEnd(arr) {
    // Method 1: Using pop (Built-in)
    let removed = arr.pop();
    console.log("Removed:", removed);
    return arr;
}

// Test
let arr11 = [1, 2, 3, 4, 5];
deleteFromEnd(arr11);
console.log(arr11);  // Output: [1, 2, 3, 4]
```

**Time Complexity:** O(1) - no shifting needed  
**Space Complexity:** O(1)

---

**Manual Implementation:**

```javascript
function deleteFromEndManual(arr) {
    if (arr.length === 0) return arr;
    
    // Just reduce the length
    arr.length = arr.length - 1;
    
    return arr;
}

// Test
let arr12 = [1, 2, 3, 4, 5];
deleteFromEndManual(arr12);
console.log(arr12);  // Output: [1, 2, 3, 4]
```

**Visual Example:**
```
Original: [1, 2, 3, 4, 5]
Delete from end:

[1, 2, 3, 4]  ← Just remove last!
```

---

### Type 3: Delete from Specific Position

**Problem:** Remove element at given index

**Approach:** Shift all elements after that position to left

```javascript
function deleteFromPosition(arr, position) {
    // Check if position is valid
    if (position < 0 || position >= arr.length) {
        console.log("Invalid position");
        return arr;
    }
    
    // Method 1: Using splice
    let removed = arr.splice(position, 1);
    console.log("Removed:", removed[0]);
    return arr;
}

// Test
let arr13 = [1, 2, 3, 4, 5];
deleteFromPosition(arr13, 2);  // Delete element at index 2
console.log(arr13);  // Output: [1, 2, 4, 5]
```

**Time Complexity:** O(n) - may need to shift elements  
**Space Complexity:** O(1)

---

**Manual Implementation:**

```javascript
function deleteFromPositionManual(arr, position) {
    if (position < 0 || position >= arr.length) {
        return arr;
    }
    
    // Shift all elements after position to left
    for (let i = position; i < arr.length - 1; i++) {
        arr[i] = arr[i + 1];
    }
    
    // Reduce length
    arr.length = arr.length - 1;
    
    return arr;
}

// Test
let arr14 = [1, 2, 3, 4, 5];
deleteFromPositionManual(arr14, 2);
console.log(arr14);  // Output: [1, 2, 4, 5]
```

**Visual Example:**
```
Original: [1, 2, 3, 4, 5]
Delete element at index 2 (which is 3):

Index:     0  1  2  3  4
Step 1:   [1, 2, 4, 4, 5]  Shift element at index 3 to 2
Step 2:   [1, 2, 4, 5, 5]  Shift element at index 4 to 3
Step 3:   [1, 2, 4, 5]     Remove last duplicate
```

---

### Practice Problem 5: Remove All Occurrences

**Problem:** Remove all occurrences of a value from array

```javascript
function removeAllOccurrences(arr, value) {
    // Filter out all occurrences
    return arr.filter(element => element !== value);
}

// Test
let arr15 = [1, 2, 3, 2, 4, 2, 5];
let result3 = removeAllOccurrences(arr15, 2);
console.log(result3);  // Output: [1, 3, 4, 5]
```

**Alternative (In-place):**

```javascript
function removeAllOccurrencesInPlace(arr, value) {
    let writeIndex = 0;
    
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] !== value) {
            arr[writeIndex] = arr[i];
            writeIndex++;
        }
    }
    
    // Trim array to new size
    arr.length = writeIndex;
    return arr;
}

// Test
let arr16 = [1, 2, 3, 2, 4, 2, 5];
removeAllOccurrencesInPlace(arr16, 2);
console.log(arr16);  // Output: [1, 3, 4, 5]
```

**Time:** O(n)  
**Space:** O(1) for in-place version

---

## Part 4: Searching (45 mins)

### What is Searching?

**Searching** = Finding if an element exists in array and its position

**2 Main Types:**
1. Linear Search (Unsorted array)
2. Binary Search (Sorted array)

---

### Type 1: Linear Search

**Concept:** Check each element one by one until found

**Use When:** Array is unsorted OR small array

```javascript
function linearSearch(arr, target) {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] === target) {
            return i;  // Return index where found
        }
    }
    return -1;  // Not found
}

// Test
let arr17 = [10, 25, 30, 15, 40];
console.log(linearSearch(arr17, 30));  // Output: 2
console.log(linearSearch(arr17, 50));  // Output: -1
```

**Time Complexity:**
- Best Case: O(1) - element at first position
- Worst Case: O(n) - element at last or not found
- Average Case: O(n)

**Space Complexity:** O(1)

---

**Visual Example:**
```
Array: [10, 25, 30, 15, 40]
Search for 30:

Step 1: Check arr[0] = 10 ≠ 30 ❌
Step 2: Check arr[1] = 25 ≠ 30 ❌
Step 3: Check arr[2] = 30 = 30 ✅ Found at index 2!
```

---

### Practice Problem 6: Find All Occurrences

**Problem:** Find all positions where element exists

```javascript
function findAllOccurrences(arr, target) {
    let positions = [];
    
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] === target) {
            positions.push(i);
        }
    }
    
    return positions;
}

// Test
let arr18 = [10, 25, 30, 25, 40, 25];
console.log(findAllOccurrences(arr18, 25));  // Output: [1, 3, 5]
console.log(findAllOccurrences(arr18, 50));  // Output: []
```

---

### Type 2: Binary Search

**Concept:** Divide array in half repeatedly (Only works on SORTED array)

**Use When:** Array is sorted AND large array

**How it works:**
1. Find middle element
2. If target = middle, found!
3. If target < middle, search left half
4. If target > middle, search right half
5. Repeat until found or no elements left

```javascript
function binarySearch(arr, target) {
    let left = 0;
    let right = arr.length - 1;
    
    while (left <= right) {
        // Find middle index
        let mid = Math.floor((left + right) / 2);
        
        // Check if target is at mid
        if (arr[mid] === target) {
            return mid;
        }
        
        // If target is smaller, search left half
        if (arr[mid] > target) {
            right = mid - 1;
        }
        // If target is larger, search right half
        else {
            left = mid + 1;
        }
    }
    
    return -1;  // Not found
}

// Test (Array MUST be sorted!)
let arr19 = [10, 20, 30, 40, 50, 60, 70];
console.log(binarySearch(arr19, 40));  // Output: 3
console.log(binarySearch(arr19, 25));  // Output: -1
```

**Time Complexity:**
- Best Case: O(1) - element at middle
- Worst Case: O(log n) - keep halving
- Average Case: O(log n)

**Space Complexity:** O(1)

---

**Visual Example:**
```
Array: [10, 20, 30, 40, 50, 60, 70]
Search for 40:

Step 1: left=0, right=6, mid=3
        [10, 20, 30, 40, 50, 60, 70]
                     ↑
        arr[3] = 40 = target ✅ Found!

Search for 20:

Step 1: left=0, right=6, mid=3
        [10, 20, 30, 40, 50, 60, 70]
                     ↑
        arr[3] = 40 > 20, search left half

Step 2: left=0, right=2, mid=1
        [10, 20, 30]
             ↑
        arr[1] = 20 = target ✅ Found!
```

---

**Recursive Binary Search:**

```javascript
function binarySearchRecursive(arr, target, left = 0, right = arr.length - 1) {
    // Base case: element not found
    if (left > right) {
        return -1;
    }
    
    let mid = Math.floor((left + right) / 2);
    
    // Element found
    if (arr[mid] === target) {
        return mid;
    }
    
    // Search left half
    if (arr[mid] > target) {
        return binarySearchRecursive(arr, target, left, mid - 1);
    }
    // Search right half
    else {
        return binarySearchRecursive(arr, target, mid + 1, right);
    }
}

// Test
let arr20 = [10, 20, 30, 40, 50, 60, 70];
console.log(binarySearchRecursive(arr20, 50));  // Output: 4
```

---

### Practice Problem 7: Search in Rotated Sorted Array

**Problem:** Array is sorted but rotated at some pivot

```javascript
// Example: [40, 50, 60, 70, 10, 20, 30] (rotated at index 4)

function searchRotated(arr, target) {
    let left = 0;
    let right = arr.length - 1;
    
    while (left <= right) {
        let mid = Math.floor((left + right) / 2);
        
        if (arr[mid] === target) {
            return mid;
        }
        
        // Check which half is sorted
        if (arr[left] <= arr[mid]) {
            // Left half is sorted
            if (target >= arr[left] && target < arr[mid]) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        } else {
            // Right half is sorted
            if (target > arr[mid] && target <= arr[right]) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
    }
    
    return -1;
}

// Test
let arr21 = [40, 50, 60, 70, 10, 20, 30];
console.log(searchRotated(arr21, 20));  // Output: 5
```

---

## Part 5: Updating (30 mins)

### What is Updating?

**Updating** = Changing value of existing element(s)

---

### Type 1: Update Single Element

**Problem:** Change value at specific index

```javascript
function updateElement(arr, index, newValue) {
    // Check if index is valid
    if (index < 0 || index >= arr.length) {
        console.log("Invalid index");
        return arr;
    }
    
    // Update the value
    arr[index] = newValue;
    return arr;
}

// Test
let arr22 = [10, 20, 30, 40, 50];
updateElement(arr22, 2, 999);
console.log(arr22);  // Output: [10, 20, 999, 40, 50]
```

**Time Complexity:** O(1) - direct access  
**Space Complexity:** O(1)

---

### Type 2: Update Multiple Elements

**Problem:** Update all elements that match a condition

```javascript
function updateMultiple(arr, oldValue, newValue) {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] === oldValue) {
            arr[i] = newValue;
        }
    }
    return arr;
}

// Test
let arr23 = [10, 20, 30, 20, 40, 20];
updateMultiple(arr23, 20, 999);
console.log(arr23);  // Output: [10, 999, 30, 999, 40, 999]
```

**Time Complexity:** O(n) - check each element  
**Space Complexity:** O(1)

---

### Practice Problem 8: Increment All Elements

**Problem:** Add a value to all elements

```javascript
function incrementAll(arr, increment) {
    for (let i = 0; i < arr.length; i++) {
        arr[i] += increment;
    }
    return arr;
}

// Test
let arr24 = [1, 2, 3, 4, 5];
incrementAll(arr24, 10);
console.log(arr24);  // Output: [11, 12, 13, 14, 15]

// Using map (creates new array)
let arr25 = [1, 2, 3, 4, 5];
let result4 = arr25.map(x => x + 10);
console.log(result4);  // Output: [11, 12, 13, 14, 15]
```

---

### Practice Problem 9: Double Even Numbers

**Problem:** Multiply all even numbers by 2

```javascript
function doubleEvenNumbers(arr) {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] % 2 === 0) {  // If even
            arr[i] *= 2;
        }
    }
    return arr;
}

// Test
let arr26 = [1, 2, 3, 4, 5, 6];
doubleEvenNumbers(arr26);
console.log(arr26);  // Output: [1, 4, 3, 8, 5, 12]
```

---

## Final Practice Problems (30-45 mins)

### Problem 10: Reverse Array

**Problem:** Reverse the array in-place

```javascript
function reverseArray(arr) {
    let left = 0;
    let right = arr.length - 1;
    
    while (left < right) {
        // Swap elements
        let temp = arr[left];
        arr[left] = arr[right];
        arr[right] = temp;
        
        left++;
        right--;
    }
    
    return arr;
}

// Test
let arr27 = [1, 2, 3, 4, 5];
reverseArray(arr27);
console.log(arr27);  // Output: [5, 4, 3, 2, 1]
```

**Time:** O(n)  
**Space:** O(1)

---

### Problem 11: Move Zeros to End

**Problem:** Move all 0s to end, maintain order of other elements

```javascript
function moveZerosToEnd(arr) {
    let writeIndex = 0;
    
    // Move all non-zero elements to front
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] !== 0) {
            arr[writeIndex] = arr[i];
            writeIndex++;
        }
    }
    
    // Fill remaining positions with 0
    while (writeIndex < arr.length) {
        arr[writeIndex] = 0;
        writeIndex++;
    }
    
    return arr;
}

// Test
let arr28 = [0, 1, 0, 3, 12, 0, 5];
moveZerosToEnd(arr28);
console.log(arr28);  // Output: [1, 3, 12, 5, 0, 0, 0]
```

**Time:** O(n)  
**Space:** O(1)

---

### Problem 12: Remove Duplicates from Sorted Array

**Problem:** Remove duplicates in-place, return new length

```javascript
function removeDuplicates(arr) {
    if (arr.length === 0) return 0;
    
    let writeIndex = 0;
    
    for (let i = 1; i < arr.length; i++) {
        if (arr[i] !== arr[writeIndex]) {
            writeIndex++;
            arr[writeIndex] = arr[i];
        }
    }
    
    return writeIndex + 1;  // New length
}

// Test
let arr29 = [1, 1, 2, 2, 3, 4, 4, 5];
let newLength = removeDuplicates(arr29);
console.log(newLength);  // Output: 5
console.log(arr29.slice(0, newLength));  // Output: [1, 2, 3, 4, 5]
```

**Time:** O(n)  
**Space:** O(1)

---

### Problem 13: Merge Two Sorted Arrays

**Problem:** Merge two sorted arrays into one sorted array

```javascript
function mergeSortedArrays(arr1, arr2) {
    let merged = [];
    let i = 0, j = 0;
    
    // Compare and merge
    while (i < arr1.length && j < arr2.length) {
        if (arr1[i] <= arr2[j]) {
            merged.push(arr1[i]);
            i++;
        } else {
            merged.push(arr2[j]);
            j++;
        }
    }
    
    // Add remaining elements from arr1
    while (i < arr1.length) {
        merged.push(arr1[i]);
        i++;
    }
    
    // Add remaining elements from arr2
    while (j < arr2.length) {
        merged.push(arr2[j]);
        j++;
    }
    
    return merged;
}

// Test
let arr30 = [1, 3, 5, 7];
let arr31 = [2, 4, 6, 8];
let merged = mergeSortedArrays(arr30, arr31);
console.log(merged);  // Output: [1, 2, 3, 4, 5, 6, 7, 8]
```

**Time:** O(n + m) where n, m are array lengths  
**Space:** O(n + m) for result array

---

### Problem 14: Find Second Largest Element

**Problem:** Find second largest element in array

```javascript
function findSecondLargest(arr) {
    if (arr.length < 2) return null;
    
    let largest = -Infinity;
    let secondLargest = -Infinity;
    
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] > largest) {
            secondLargest = largest;
            largest = arr[i];
        } else if (arr[i] > secondLargest && arr[i] !== largest) {
            secondLargest = arr[i];
        }
    }
    
    return secondLargest === -Infinity ? null : secondLargest;
}

// Test
console.log(findSecondLargest([10, 5, 20, 8, 15]));  // Output: 15
console.log(findSecondLargest([10, 10, 10]));        // Output: null
```

**Time:** O(n)  
**Space:** O(1)

---

### Problem 15: Rotate Array by K Positions

**Problem:** Rotate array to right by k positions

```javascript
function rotateArray(arr, k) {
    // Handle k > arr.length
    k = k % arr.length;
    
    // Helper function to reverse
    function reverse(start, end) {
        while (start < end) {
            let temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }
    
    // Step 1: Reverse entire array
    reverse(0, arr.length - 1);
    
    // Step 2: Reverse first k elements
    reverse(0, k - 1);
    
    // Step 3: Reverse remaining elements
    reverse(k, arr.length - 1);
    
    return arr;
}

// Test
let arr32 = [1, 2, 3, 4, 5, 6, 7];
rotateArray(arr32, 3);
console.log(arr32);  // Output: [5, 6, 7, 1, 2, 3, 4]
```

**Example visualization:**
```
Original:      [1, 2, 3, 4, 5, 6, 7]
Rotate by 3:

Step 1: Reverse all      [7, 6, 5, 4, 3, 2, 1]
Step 2: Reverse first 3  [5, 6, 7, 4, 3, 2, 1]
Step 3: Reverse rest     [5, 6, 7, 1, 2, 3, 4] ✅
```

**Time:** O(n)  
**Space:** O(1)

---

## Summary - Key Takeaways

### Operations Complexity Table

| Operation | Time Complexity | Space Complexity |
|-----------|----------------|------------------|
| **Traversal** | O(n) | O(1) |
| **Insert at Beginning** | O(n) | O(1) |
| **Insert at End** | O(1) | O(1) |
| **Insert at Position** | O(n) | O(1) |
| **Delete from Beginning** | O(n) | O(1) |
| **Delete from End** | O(1) | O(1) |
| **Delete from Position** | O(n) | O(1) |
| **Linear Search** | O(n) | O(1) |
| **Binary Search** | O(log n) | O(1) |
| **Update Single** | O(1) | O(1) |
| **Update Multiple** | O(n) | O(1) |

---

### Important Patterns Learned

✅ **Traversal Pattern:**
```javascript
for (let i = 0; i < arr.length; i++) {
    // Process arr[i]
}
```

✅ **Two Pointer Pattern:**
```javascript
let left = 0, right = arr.length - 1;
while (left < right) {
    // Swap or compare arr[left] and arr[right]
    left++;
    right--;
}
```

✅ **Binary Search Pattern:**
```javascript
let left = 0, right = arr.length - 1;
while (left <= right) {
    let mid = Math.floor((left + right) / 2);
    // Compare and adjust left/right
}
```

✅ **In-Place Modification Pattern:**
```javascript
let writeIndex = 0;
for (let i = 0; i < arr.length; i++) {
    if (condition) {
        arr[writeIndex++] = arr[i];
    }
}
```

---

## What to Practice Next

1. ✅ Complete all 15 practice problems
2. ✅ Solve on paper first, then code
3. ✅ Try without looking at solutions
4. ✅ Understand time/space complexity
5. ✅ Practice variations of each problem

---

## LeetCode Problems to Practice

**Easy:**
1. Two Sum (Uses searching)
2. Remove Duplicates from Sorted Array
3. Remove Element
4. Search Insert Position (Binary Search)
5. Plus One

**Medium:**
6. Rotate Array
7. Move Zeroes
8. Find First and Last Position (Binary Search)

---

## Tomorrow: Day 5

**Next Topic: Two Pointer Technique**
- Same Direction Pointers
- Opposite Direction Pointers
- Real-world problems

**You're doing great! Keep practicing! 🚀**