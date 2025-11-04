# Gaussian Elimination Algorithm for Determinant Calculation

## Table of Contents
- [Algorithm Description](#algorithm-description)
- [Example for 2x2 Matrix](#example-for-2x2-matrix)
- [Implementation Features](#implementation-features)
- [Complexity](#complexity)

## Algorithm Description
The Gaussian elimination method works by transforming the matrix into an upper triangular form and then multiplying the main diagonal elements.

### Step 0: Data Input
- The program expects the matrix size (n) and n×n matrix elements row by line

### Step 1: Preparation
- **Look at the first element of the first row** - this is our first pivot element
- **If it equals 0** - find a row below where the first element is not zero, and swap the rows
- **Remember** that each row swap changes the determinant's sign

### Step 2: Forward Elimination (for each column j)
- **Take the pivot element** - `matrix[j][j]`
- **For all rows i below the pivot** (i = j+1, j+2, ..., n):
  - **Calculate multiplier**: `multiplier = -matrix[i][j] / matrix[j][j]`
  - **Transform row i**: for each column k from j to n:
    - `matrix[i][k] += multiplier * matrix[j][k]`
  - This way, we zero out all elements below the pivot

## Example for 2x2 Matrix

Initial matrix:
```
[2, 1]
[1, 3]
```


### Step 1:
- **Pivot element** = 2 (not zero, no swap needed)

### Step 2:
- **Multiplier for row 1**: `multiplier = -1/2`
- **Transform row 2**:
  - `matrix[1][0] = 1 + (-1/2)*2 = 0`
  - `matrix[1][1] = 3 + (-1/2)*1 = 2.5`

Result:
```
[2, 1 ]
[0, 2.5]
```


### Step 3:
- **Determinant** = 2 × 2.5 = 5

## Implementation Features
- **Uses `double`** for calculation precision
- **Epsilon comparison** instead of exact equality with zero
- **Early exit** when zero determinant is detected

## Complexity
Forward elimination (transformation to triangular form): has time complexity O(n³).
