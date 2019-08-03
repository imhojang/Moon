---
layout: post
title:  "Sorting Algorithms Part I & II"
date:   2019-07-15
excerpt: " "
tag:
- javascript
- sorting
- algorithms
comments: true
feature: https://images.unsplash.com/photo-1552550049-db097c9480d1?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1234&q=80
category: [ Algorithms ]
---

## Sorting Application 

Where sorting algorithms help us

- Sorting a list of people
- Find the median
- Find duplicates in some data
- Binary Search in a database

------

## Why do we study sorting algorithms?

Isn't the system sort good enough?

**Maybe**

- Need guaranteed performance?
- Large records?
- Small records?
- Stable? => 

A basic sorting algorithm may be our choice.

To understand basic issues of sorting.

------

## Bubble Sort 

In a bubble sort, the elements of the list gradually bubbles to their proper location in the list.

- perform a sequence of passes through the list
- on each pass: proceed from left to right, swapping adjacent elements if they are out of order.
- larger elements bubbles up to the end of the list.
- At the end of the kth pass, the k right most elements are in their final positions.

#### Big O

- Worst Case: O(n제곱) when does it have worst case performance?
- Best Case: O(n) when does it have best case performance?

#### Disadvantages

**Performance (especially with large dataset)**

we study bubble sort for academic purpose, since it is the easiest to understand.

#### Advantages

1. ***Memory**:** Bubble sort is **"in place"** algorithm (does not require extra space when sorting)
2. **Easy to write**: Ideal for beginners
3. **Good for testing whether a list is sorted or not:**  
   Other sorting algorithms often cycle through their whole sorting sequence, but we can do O(n) with ubble sort in the best case scenario.

------

## Insertion Sort

Going from left to right, **inserts** each element into its proper location with respect to the elements to its left.

#### Big O

- Worst Case: O(n제곱) when does it have worst case performance?
- Best Case: O(n) when does it have best case performance?

#### Disadvantages

**Performance (especially with large dataset)**

we study insertion sort for academic purpose, since it is the easiest to understand.

#### Advantages

1. ***Memory**:** Bubble sort is **"in place"** algorithm (does not require extra space when sorting)
2. **Easy to write**: Ideal for beginners
3. **Good for testing whether a list is sorted or not:**  
   Other sorting algorithms often cycle through their whole sorting sequence, but we can do O(n) with ubble sort in the best case scenario.

------

## Sorting Algorithms - Part II

## What does "stable" mean?

A stable sort preserves the relative order of records.

상대적인 위치가 최종 결과에 유지된다면 stable 
아니라면 unstable.

------

## Selection Sort

- Consider the positions in the array from left to right
- For each position, find the element that belongs there and put it in place by swapping it with the element that's currently there.

#### Big O

- Worst Case: O(n제곱) when does it have worst case performance?
- Best Case: O(n제곱) when does it have best case performance?

#### Disadvantages

**Performance (especially with large dataset)**

we study insertion sort for academic purpose, since it is the easiest to understand.

#### Advantages

1. ***Memory**:** Bubble sort is **"in place"** algorithm (does not require extra space when sorting)
2. **Easy to write**: Ideal for beginners
3. **Good for testing whether a list is sorted or not:**  
   Other sorting algorithms often cycle through their whole sorting sequence, but we can do O(n) with ubble sort in the best case scenario.

------

## Merge Sort

It is based on the process of **merging two sorted** arrays into a single sorted array.

#### Big O

- Worst Case: O(log n) when does it have worst case performance?
- Best Case: O(log n) when does it have best case performance?

#### Disadvantages

**O (n)** 공간 필요도.

#### Advantages

1. Best case, Worst case: All O(n log n)

- log n 이라고 해서 항상 n 제곱보다 나은건 아니다. 

#### Divide and conquer (방법론)

1. Divide: split the array in half, forming two subarrays.
2. Conquer: Apply merge sort recursively to the subarrays, stopping when a sub array has a single element.
3. Combine: merge the sorted subarrays.

Examples: 

- Binary Search
- Quick Sort
- Merge Sort

------

Stable한 것은 insertion sort를 제외한 모든것

In place in 것은 merge sort를 제외한 모든것

------

## TO DO

- Quick sort
- Divide and conquer
- Dynamic programming