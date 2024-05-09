A sorting algorithm is an [[Algorithms|algorithm]] which is used to sort the elements of a [[Abstract Datatypes#List|list]]. Sorting algorithms have the following properties:
- **Stability** which determines if elements of equal value are switched during the sorting process.
- **Incremental** if when you add an item to a sorted list it can be placed without committing unnecessary actions.

Sorting can be divided into two categories of algorithm. These are comparison, and non-comparison algorithms. Comparison algorithms require the algorithm to individually compare elements of any type, while non-comparison algorithms usually rely on integers being parsed as the array type. The lower bound for comparison based algorithms is $n \log n$. While the

# Counting Inversions
Counting Inversions are a similar related problem to sorting that are defined as the number of steps away from an array being sorted. An inversion is defined as a pair of array indices $(i,j)$ such that array indices follow $i<j$, and $A[i]>A[j]$. This means each of these pairs are out of order elements within the array. These inversion are then counted as to find how far an array is from being sorted. With a sorted array having a count of $0$, while a reversed array having $n$. This can be used as a similarity test.

The solution to counting inversions can be done through a brute-force approach that manually searches through each element in $O(n^2)$, or a modification of merge sort that results in a complexity of $O(n\log n)$. The merge sort implementation of this algorithm works by splitting the lists as to count inverses, and sort the array. This allows the merge process to find if there are any inversions by checking if the left subarray is the smallest element, if it isn't then there are inversions.

# Bubble Sort
Bubble sort is a naïve sorting algorithm that compares each value pair sorting until all elements are sorted.
```pseudo
	\begin{algorithm}
	\caption{BubbleSort(A)}
	\begin{algorithmic}
		\FOR{$i \gets 0$ \TO $A.size$}
			\FOR{$j \gets 0$ \TO $A.size-1$}
				\IF{$A[i] < A[j]$}
					\STATE \CALL{swap}{A[i],A[j]}
				\ENDIF
			\ENDFOR
		\ENDFOR
	\end{algorithmic}
	\end{algorithm} 
```
This code can be further optimized to find values that have been already swapped as to avoid the second for loop.

# Insertion Sort
Insertion sorts the list by incrementally sorting the list until the list is fully sorted. It does this by splitting the list into two where there exists a sorted segment, and unsorted segment. Each iteration correctly sorts one unsorted element into the sorted segment. It follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{InsertionSort(A)}
	\begin{algorithmic}
		\FOR{$i \gets 1$ \TO $A.length$}
			\STATE $j \gets i-1$
			\WHILE{$j>0$ \AND $A[j] > A[i]$}
				\STATE $A[j+1] \gets A[j]$
				\STATE $j \gets j-1$
			\ENDWHILE
			\STATE $A[j+1] \gets A[i]$
		\ENDFOR
	\end{algorithmic}
	\end{algorithm} 
```
This follows the **loop invariant** that at the start of each iteration of the for loop the subarray $A[1..i-1]$ is sorted. The time complexity of insertion sort follows $O(n^2)$ since it individually sorts each element into the left subarray. Insertion sort has an average time complexity of $\Theta (n^2)$. Despite the slow speed it is in-place, and stable.

# Selection Sort
Selection Sort is a basic sorting algorithm that follows the general idea of there being two halves of the list, the sorted half and the unsorted half. The sorted half starts empty whereupon each iteration of the loop the smallest element is found from the unsorted half and put into the sorted half. It follows the pseudocode of:
```pseudo
	\begin{algorithm}
	\caption{SelectionSort(A)}
	\begin{algorithmic}
		\FOR{$i \gets 1$ \TO $A.length$}
			\STATE $min \gets i$
			\FOR{$j \gets i+1$ \TO $A.length$}
				\IF{$A[min] > A[j]$}
					\STATE $min \gets j$
				\ENDIF
			\ENDFOR
			\STATE \CALL{swap}{A[i],A[min]}
		\ENDFOR
	\end{algorithmic}
	\end{algorithm} 
```
Selection sort has a time complexity of $O(n^2)$, as a minimum operation is being ran on each place within the array. The invariant of selection sort states that sub array $A[1..i-1]$ is sorted, and for all $x$ in array $A[1..i-1]$, and $y$ in array $A[i..n]$, $x \leq y$. The algorithm isn't stable, but is in-place.

# Quick Sort
Quick sort is an in-place, [[Algorithmic Paradigms#Divide and Conquer|divide and conquer]] sorting algorithm which isn't stable. It is one of the most popular algorithms for sorting as it can be faster than merge sort. Quick sort works by selecting a **pivot** element from the list and partitioning the other elements into two sub-arrays. These sub-arrays are then sorted through the use of recursion. The pivot is commonly the median value of the array, however can also just be random.
```pseudo
	\begin{algorithm}
	\caption{QuickSort(A[lo..hi])}
	\begin{algorithmic}
		\IF{$hi > lo$}
			\STATE $pivot \gets A[lo]$
			\STATE $mid \gets$ \CALL{Partition}{(A,pivot)}
			\STATE \CALL{QuickSort}{A[lo..mid-1]}
			\STATE \CALL{QuickSort}{A[mid+1..hi]}
		\ENDIF
	\end{algorithmic}
	\end{algorithm} 
```

Quick sort has a worst case complexity of $O(n^2)$, however has an average of $\Theta (n \log n)$. This makes it faster than other sorts if the pivot selected is good, as the worst case complexity is caused by the minimum or maximum being selected as the pivot. Due to this the quicksort algorithm heavily relies upon its ability to [[Partitioning Algorithms|partition]] the data as this determines its stability and whether its in-place. With Hoare, and Dutch Flag being in-place but at the cost of stability, while naïve has stability. In the best case partition the pivot is the median of the array and as a result only $\log n$ recursions are done. In the worse case the partition is the smallest or largest element which results in $n$ recursions, giving the algorithm its worst-case time complexity. The argument to prove the average height of $\log n$ follows the **coinflip argument**, which states that as the middle $50\%$ of pivots are considered good every second pivot should be good. As this is the case the algorithm tends towards a lower logarithmic function.

Quicksort can be further optimised by instead of recursively sorting the left and right half of the arrays they can sort the smallest half and then the largest. This results in the smallest half having a height of $\log n$ while the largest is sorted by [[Functional Programming|tail recursive calls]].

Choice of a pivot can further be used to improve quicksort. Randomised pivot selection in practice choses the best result, however a balanced quicksort can also be achieved through using [[Order & Selection Algorithms#Median of Medians|median of medians]] to choose the pivot.

# Merge Sort
Merge sort is a comparison based sorting algorithm which is stable. It is a [[Algorithmic Paradigms#Divide and Conquer|divide and conquer]] algorithm which commonly uses [[Recursion|recursion]]. Merge sort functions through a division of all elements into single sub-problems which are built up sorting at every step. This is usually done by sorting all pairs, and then merging these pairs into sets of 4, and continuing this process until the list is fully sorted. Merge sort has a worst case and average time complexity of $O(n \log n)$, which can be multiplied by the comparison equations complexity. Merge sort is good for languages where comparison is expensive. It follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{MergeSort(A,p,r)}
	\begin{algorithmic}
		\IF{$p<r$}
			\STATE $q \gets |(p+r)/2|$
			\STATE \CALL{MergeSort}{A,p,q}
			\STATE \CALL{MergeSort}{A,q+1,r}
			\STATE \CALL{Merge}{A,p,q,r}
		\ENDIF
	\end{algorithmic}
	\end{algorithm} 
```

This calls an auxiliary function merge which uses the code:
```pseudo
	\begin{algorithm}
	\caption{Merge(A,p,q,r)}
	\begin{algorithmic}
		\STATE $n_1 \gets q-p+1$
		\STATE $n_2 \gets r-q$
		\STATE \COMMENT{Create Left \& Right Halfs}
		\STATE Let $L[1..n_1+1]$ and $R[1..n_2+1]$
		\FOR{$i\gets 1$ \to $n_1$}
			\STATE $L[i] \gets A[p+1-1]$
		\ENDFOR
		\FOR{$i\gets 1$ \to $n_2$}
			\STATE $R[i] \gets A[q+j]$
		\ENDFOR
		\STATE $L[n_1+1] \gets R[n_2+1] \gets \infty$
		\STATE $i \gets j \gets 1$
		\STATE\COMMENT{Sort Left \& Right Halfs}
		\FOR{$k \gets p$ \TO $r$} 
			\IF{$L[i] \leq R[j]$}
				\STATE $A[k] \gets L[i]$
				\STATE $i \gets i+1$
			\ELSE
				\STATE $A[k] \gets R[i]$
				\STATE $j \gets j+1$
			\ENDIF
		\ENDFOR
	\end{algorithmic}
	\end{algorithm} 
```
Merge sort is a stable sort. It's **loop invariant** states that at the start of each iteration the sub array $A[p..k-1]$ contains the $k-p$ smallest elements of $L[1..n_1+1]$ and $R[1..n_2+1]$ in sorted order. Furthermore, $L[i]$ and $R[j]$ are the smallest elements of their array that have not been copied back into `A[]`.

Merge sort can be improved through the use of a bottom up approach that iteratively merges the results. This still requires $O(n)$ auxiliary memory however removes the recursive stack calls.

# Heap Sort
Heap Sort is a sorting algorithm which uses a [[Heap Structures|heap]] as to sort its elements. This functions simply by creating a maxheap from an array whereafter the max or minimum is extracted for each element. The algorithm runs in $O(n\log n)$ time, however in practice runs slower than most other sorting algorithms. Additionally heap sort is also unstable, but is in-place. It follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{HeapSort(A)}
	\begin{algorithmic}
		\STATE \CALL{MaxHeapify}{A}
		\FOR{$i\gets n$ \TO $1$}
			\STATE $A[i] \gets$ \CALL{ExtractMax}{A}
		\ENDFOR
	\end{algorithmic}
	\end{algorithm} 
```

# Counting Sort
Counting Sort is a non-comparison algorithm that is unstable. It works by creating a counting array which size is equal to `max-min` of the array. This counting array counts the amount of appearances of a certain number. Which it then puts into the output array by iterating from the start of the counting array. This has a complexity of $O(n+u)$ where `u` is the size of the counting array. Alternatively the time complexity can be considered in respect to bits where the sorting of $w$-bit integers can be considered to have a time complexity of $O(n+2^w)$. Where the algorithm is linear if $w=\log n + O(1)$. Counting-sort can be expressed with:
```pseudo
	\begin{algorithm}
	\caption{CountingSort(A)}
	\begin{algorithmic}
		\STATE $k \gets$ \CALL{Max}{A}
		\STATE $C, Result \gets \emptyset$
		\FOR{$i \gets 0$ \TO $k$}
			\STATE $C[i] \gets 0$
			\STATE $Result[i] \gets 0$
		\ENDFOR
		\FOR{$i \gets 0$ \TO $A.length$}
			\STATE $C[A[i]] \gets C[A[i]]+1$
		\ENDFOR
		\FOR{$i \gets 1$ \TO $k$}
			\STATE $C[i] \gets C[i] + C[i-1]$
		\ENDFOR
		\FOR{$j \gets A.length$ \TO $1$}
			\STATE $Result[C[A[i]]] \gets A[j]$
			\STATE $C[A[i]] \gets C[A[i]]-1$
		\ENDFOR
	\end{algorithmic}
	\end{algorithm} 
```

To make the algorithm stable a new position array must be initialized. This array constructs its position from the rule `position[i]=position[i-1]+count[i-1]`. During the construction of the output the `outputArr[position[key]]=(key,val)`, after which `position[key]` is incremented

# Radix Sort
Radix sort is a non-comparison algorithm that uses a stable sorting algorithm as to sort numbers of $k$ digits. In the case of **least significant digit** this functions through sorting right to left the digits in each column. Due to the requirement for stability counting sort is commonly used due to its low time complexity. Since it commonly uses counting-sort the algorithm isn't usually considered in-place. The algorithm follows the pseudocode:
```pseudo
	\begin{algorithm}
	\caption{RadixSort(A,d)}
	\begin{algorithmic}
		\FOR{$i \gets 1$ \TO $d$}
			\STATE \CALL{Sort}{$a_i$}
		\ENDFOR
	\end{algorithmic}
	\end{algorithm} 
```

The algorithm has a time complexity of $O(k\cdot (n+b))$, where $k$ is the digits, and $b$ is the base system. Since the base and amount of bits is closely related the time complexity of radix can be more precisely written as $O(\frac{w}{\log b}(n+b))$, where $w$ is the amount of bits wide a number is. Due to this fact the base of radix needs to be chosen more carefully. To ensure this, the base needs to be balanced by making by making $b=O(n)$, or b=n. This results in the time complexity becoming $O(\frac{w}{\log n} \cdot n)$.
