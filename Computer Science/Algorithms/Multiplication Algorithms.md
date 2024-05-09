2Multiplication algorithms have the goal of dividing the process of dividing multiple multilength integer inputs into a few small one integer operations. These operations are usually found on the base instruction set of computers. Compared to [[Division Algorithms|division algorithms]] multiplication is a much faster process.

# Elementary Algorithm
The most basic algorithm has a time complexity of $O(n^2)$ and follows the process of multiplying each integer in the first number by the second, and then adding the power of ten for the corresponding place. This follows an algorithm of:
```pseudo
	\begin{algorithm}
	\caption{BasicMultiplication($num_1,num_2$)}
	\begin{algorithmic}
	\STATE $total \gets 0$
	\FOR{$i\gets 0$ \TO $num_1.length$}
		\STATE $temp \gets 10^i$
		\FOR{$j\gets 0$ \TO $num_2.length$}
			\STATE $temp \gets num_1[i] \cdot num_2[j] \cdot 10^j$
		\ENDFOR
		\STATE $total \gets total + temp$
	\ENDFOR
	\end{algorithmic}
	\end{algorithm} 
```

# Karatsuba's Algorithm
Karatsuba's algorithm is a fast multiplication algorithm that increases the speed of multiplication to a time complexity of $O(n^{\log 3})$ by using a [[Algorithmic Paradigms#Divide and Conquer|divide and conquer]] strategy . Karatsuba's algorithm works by dividing each number into two and calling a recursive function to calculate the multiplication of the two left, and right halves of the sum. This has a base of traditional multiplication that enables the result to be found.
```pseudo
	\begin{algorithm}
	\caption{Karatsuba($num_1,num_2$)}
	\begin{algorithmic}
		\IF{$num_1 < 10$ \OR $num_2 < 10$}
			\RETURN $num_1 \cdot num_2$
		\ENDIF
		\STATE $high_1, low_1 \gets$ \CALL{splitHalf}{num1}
		\STATE $high_2, low_2 \gets $ \CALL{splitHalf}{num2}
		\STATE $z_0 \gets$ \CALL{karatsuba}{low1,low2}
		\STATE $z_1 \gets$ \CALL{karatsuba}{low1+high1,low2+high2}
		\STATE $z_2 \gets$ \CALL{karatsuba}{high1,high2}
		\RETURN $(z_2 \cdot 10^{m_2\cdot 2})+((z_1-z_2-z_0)\cdot 10^{m_2})+z_0$
	\end{algorithmic}
	\end{algorithm} 
```

