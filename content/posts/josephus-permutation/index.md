+++
title = "Josephus Permutation"
date = "2023-11-15T15:52:47+08:00"
authorTwitter = "" #do not include @
author = "Tyler"
cover = ""
tags = ["C", "codewars", "coding"]
categories = ["comp sci"]
description = "On how to solve josephus permutation in C"
showFullContent = false
readingTime = true
draft = false
+++

Once upon a time, josephus permutation was an act orchestrated by josephus to *mass suicide* because they refuse to surrender to their enemy. In modern day, **josephus permutation** is a theoretical computer science problem related to the process of eliminating an element. This is my attempt at solving [this problem]("https://www.codewars.com/kata/5550d638a99ddb113e0000a2/train/c") on Codewars.

---

## Example

With an `array = [1,2,3,4,5,6,7]`, and `k=3`, the function should behave like this:
```
[1,2,3,4,5,6,7] - initial sequence
[1,2,4,5,6,7] => 3 is counted out and goes into the result [3]
[1,2,4,5,7] => 6 is counted out and goes into the result [3,6]
[1,4,5,7] => 2 is counted out and goes into the result [3,6,2]
[1,4,5] => 7 is counted out and goes into the result [3,6,2,7]
[1,4] => 5 is counted out and goes into the result [3,6,2,7,5]
[4] => 1 is counted out and goes into the result [3,6,2,7,5,1]
[] => 4 is counted out and goes into the result [3,6,2,7,5,1,4]
```

---

## Brainless Approach

Without understanding the underlying algorithm, it might seem as though it's a no-brainer. Just put the element into another array! With that idea, we'll inevitably write the atrocity like this: (yes, i did that in the first place.)

```c
void josephus_permutation(size_t n, int permuted[n], const int array[n], size_t k) {
	// For keeping track of which element to take out
	int index = 0;
	// Take out the element and store it in the permuted array
	for(int i = 1; i <= n; i++) {
		if(index <= n) {
			index += k;
		}
		else {
			index -= n;
			index += k;
		}

    }
}
```
