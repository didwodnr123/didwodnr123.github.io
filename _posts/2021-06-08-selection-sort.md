---
layout:     post
title:      "[알고리즘] 정렬: 선택 정렬"
subtitle:   " \"Selection Sort\""
author:     "Jaeuk"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - Algorithm
    - Sort
---

# Selection Sort

- Selection Sort

**선택 정렬**은 `in-place` 비교 정렬 알고리즘이다. O(n^2) 시간 복잡도를 갖고 있고, 대규모 리스트에서는 비효율적이다. 일반적으로 **삽입 정렬**보다 성능이 떨어진다. 선택 정렬 알고리즘은 단순하여 사용할 수 있는 메모리가 제한적인 경우에 효과적이다.

## Contents

1. 예시
2. 구현
3. 복잡도
4. 다른 정렬 알고리즘과 비교

## 예시 

<table class="wikitable">
<tbody><tr>
<th>Sorted sublist
</th>
<th>Unsorted sublist
</th>
<th>Least element in unsorted list
</th></tr>
<tr>
<td>()
</td>
<td style="text-align:right;">(11, 25, 12, 22, 64)
</td>
<td>11
</td></tr>
<tr>
<td>(11)
</td>
<td style="text-align:right;">(25, 12, 22, 64)
</td>
<td>12
</td></tr>
<tr>
<td>(11, 12)
</td>
<td style="text-align:right;">(25, 22, 64)
</td>
<td>22
</td></tr>
<tr>
<td>(11, 12, 22)
</td>
<td style="text-align:right;">(25, 64)
</td>
<td>25
</td></tr>
<tr>
<td>(11, 12, 22, 25)
</td>
<td style="text-align:right;">(64)
</td>
<td>64
</td></tr>
<tr>
<td>(11, 12, 22, 25, 64)
</td>
<td style="text-align:right;">()
</td>
<td>
</td></tr></tbody></table>

## 구현

```python
def selectionSort(x):
	length = len(x)
	for i in range(length-1):
	    indexMin = i
		for j in range(i+1, length):
			if x[indexMin] > x[j]:
				indexMin = j
		x[i], x[indexMin] = x[indexMin], x[i]
	return x
```

## 복잡도

| Name           | Avg    | Worst  | Stable |
| -------------- | ------ | ------ | ------ |
| Bubble  sort   | O(n^2) | O(n^2) | YES    |
| Selection sort | O(n^2) | O(n^2) | NO     |
| Insertion sort | O(n^2) | O(n^2) | YES    |



## 다른 정렬 알고리즘과 비교

- 버블 정렬(bubble sort) : 시간 복잡도 Θ ( *n* 2 )인 정렬 알고리즘 중에서 선택 정렬은 버블 정렬보다 항상 우수하다.
- 삽입 정렬(insertion sort) : 삽입 정렬은 k번째 반복 이후, 첫번째 k 요소가 정렬된 순서로 온다는 점에서 유사하다. 하지만 선택 정렬은 k+1 번째 요소를 찾기 위해 나머지 모든 요소들을 탐색하지만 삽입 정렬은 k+1 번째 요소를 배치하는 데 필요한 만큼의 요소만 탐색하기 때문에 훨씬 효율적으로 실행된다는 차이가 있다.