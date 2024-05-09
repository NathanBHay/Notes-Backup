Line drawing is the idea of drawing a line between two points in a discrete or rasterized environment (like a grid). This process creates difficulty 
# Naive Line Drawing
The most basic approach to line drawing is too simply follow traditional linear calculations for finding the line. This involves 

```pseudo
	\begin{algorithm}
	\caption{NaiveLineDraw($x0, y0, x1, y1$)}
	\begin{algorithmic}
		\State $m \gets (y1-y0) / (x1 - x0)$
		\State $c \gets y0 - m \cdot x0$
		\State $path \gets \emptyset$
		\For{$x \gets x0$ \To $x1$}
			\State $y \gets$ \Call{Round}{$m \cdot x + c$}
			\State $path.$\Call{push}{$(x, y)$}
		\EndFor
		\Return $path$
	\end{algorithmic}
	\end{algorithm}
```
This approach assumes that the line can be in any order, and that $x0<x1$. The main problem with this is that a division operation is required and as a result floating point numbers are used. This leads to the algorithm being slow if repeated many times. 

# Bresenham's Line Algorithm
Bresenham's line algorithm is an optimised algorithm that approximates the line that can be drawn between two points. Bresenham's main advantage is that only uses integer operations. This change allows for it to be a faster alternative algorithms. Bresenham's algorithm has been adapted to include variations used to rasterize different shapes such as circles, Bezier curves, and more.
```pseudo
	\begin{algorithm}
	\caption{Bresenham($x0, y0, x1, y1$)}
	\begin{algorithmic}
		\State $steep \gets$ \Call{abs}{$y1 - y0$} $>$ \Call{abs}{$x1-x0$}
		\State $dx \gets x1 - x0$
		\State $dy \gets$ \Call{abs}{$y1 - y0$}
		\State $error \gets dx / 2$
		\State $y \gets y0$
		\State $path \gets \emptyset$
		\For{$x\gets0$ \To $x1$}
			\If{$steep$}
				\State $line.$\Call{push}{(y,x)}
			\Else
				\State $line.$\Call{push}{(x,y)}
			\EndIf
			\State $error \gets error -dy$
			\If{$error < 0$}
				\State $y \gets y + 1$ 
				\State $error \gets error + dx$
				\EndIf
		\EndFor
		\Return $path$
	\end{algorithmic}
	\end{algorithm}
```
Bresenham's line functions through calculating an ongoing error value that changes for each value of the line. This error value is decreased every time a x-pixel inline with the previous is added. Once this error value reaches a threshold it steps up a certain amount of y-positions. This allows it to draw a line without requiring floating point arithmetic. 

# Chain Codes
Chain codes are an optimised way of representing rasterized lines. This approach encodes the line as a set of binary digits such that a 0 represents the next pixel being in line with the y-value of the previous while 1 represents an increase in height by one. Thus, a flat line would be represented as all 0s while a 45-degree line would be represented with all 1s. An expansion to this to include other octants could include a signed bit. 
