# Matrix Notation for statistics

Matrix and vector notation comes form the branch of mathematics called Linear algebra.
Matrices and vectors are used in essentially all statistical disciplines, and a key to understanding theoretical and empirical properties of our statistical models. We'll define a vector, matrix, and how they interact in the context of statistics.

Our end goal will be to understand how linear regression can be represented using vectors as matrices, understanding this equation

$$
Y \sim \mathcal{N}(X\beta,\sigma^{2})
$$

First, we'll define vectors and understand how they can represent data and points in n-dimensional space. 
Next we'll define Matrices and different ways of conceptualizing them.
After defining vectors and matrices separatley, we'll lear about they can interact: vector times vector, vector time matrix, and matrix times matrix. Finally, we'll frame linear regression in terms of matrices and vectors.





## Vector
A vector is an $n$-dimensional collection of real numbers.
Vectors are represented as a stack of these $n$ numbers, surrounded by brackets.
For example, 

\begin{align*}
y = \left[ 
\begin{array}{c}
y_{1}\\
y_{2}\\
y_{3}\\
\vdots\\
y_{n}\\
\end{array} \right]
\end{align*}
is a vector with $n$ elements.

A specific example of a vector with values is 
\begin{align*}
h = \left[ 
\begin{array}{c}
34\\
22.2\\
83/2\\
\end{array} \right]
\end{align*}
$h$ is a vector of length $3$. The first element is 34, second 22.2, and third 83/2.

Vectors generalize the number line.
A $n$-dimensional vector represents a single point in a $n$-dimensional space of real numbers. 
Real numbers can be thought of as $1$-dimensional vectors.
For example the expression $r=45.456$ could be represented as
\begin{align*}
r = \left[ 
\begin{array}{c}
45.456
\end{array} \right],
\end{align*}
a 1-dimensional vector with a single value 45.456.

Vectors can help us gain intuition about how statistical model are fit. 
For example, scatterplots can be thought of as a collection of 2-dimensional vectors


```R
x <- rnorm(100,0,1)
y <- rnorm(100,0,0.2)
plot(x,y)
```


![png](matrixNotation_files/matrixNotation_4_0.png)


Each point on the scatter plot above can be represented as a "tuple" $(x,y)$ or viewed as a single 2-dimensional vector.

## Matrix

A matrix is a collection of vectors, and have two dimensions written with square brackets, for example 
\begin{align*}
M = \left[ 
\begin{array}{cc}
34 & 55\\
22.2 & 0.9\\
83/2 & 76.3\\
\end{array} \right]
\end{align*}
We'll use capital letters to denote matrices, like this

\begin{align*}
X = \left[ 
\begin{array}{cc}
4 & 55\\
1/3 & 1.9\\
0.88 & 99.3\\
\end{array} \right]
\end{align*}






 Matrices can represent different concepts in statistics. They can $P$ variables collected from a set of $N$ observations. For example, height, weight, BMI, and CKMB enzyme levels for patients atrisk for a myocardial infarction (heart attack).
 
In this example, each row would represent a patient, and the columns would represent height (inches), weight (kg), and CKMB levels (IU/L). Our matrix can be constructed like

\begin{align*}
D = \left[ 
\begin{array}{cccc}
60 & 77 & 8\\
54 & 50 & 18\\
63 & 90 & 4\\
\end{array} \right]
\end{align*}

## vector times vector (the inner product)

Consider two vectors $a$ and $b$. Each is length $4$, representing a single point in a 4-dimensional Real space.
\begin{align*}
a = \left[ \begin{array}{c}
1\\
2\\
3\\
4\\
\end{array} \right]
;
b = \left[ \begin{array}{c}
5\\
6\\
7\\
8\\
\end{array} \right]
\end{align*}

Then we define the **inner product** of these two vectors as 
\begin{align*}
   a'b &= \sum_{i=1}^{4} a_{i} \times b_{i} \\
       &= 1 \times 5 + 2 \times 6 + 3 \times 7 + 4 \times 8\\
       &= 70
\end{align*}
where the $'$ symbol stand for transpose.

The transpose "flips" the rows and columns of a vector or matrix. If 
\begin{align*}
a = \left[ \begin{array}{c}
1\\
2\\
3\\
4\\
\end{array} \right]
\end{align*}
a vector with $4$ rows and $1$ column then $a'$ is a vector with $1$ row and $4$ columns
\begin{align*}
a = \left[ \begin{array}{cccc}
1 & 2 & 3 & 4
\end{array} \right]
\end{align*}






## matrix times matrix

Consider two matrices $A$ and $B$. $A$ has $2$ rows and $3$ columns. $B$ has $3$ rows and $5$ columns.
\begin{align*}
A = \left[ 
\begin{array}{ccc}
1 & 2 & 3\\
4 & 5 & 6\\
\end{array} \right]
\end{align*}

\begin{align*}
B = \left[ 
\begin{array}{ccccc}
7 & 8 & 9 & 10 & 11\\
12 & 13 & 14 & 15 & 16\\
17 & 18 & 19 & 20 & 21\\
\end{array} \right]
\end{align*}

Then we define the $(i,j)$ element of the product of matrix $A$ and $B$ as 
\begin{align}
    A B (i,j) = \sum_{r=1}^{3} a(i,r) b(r,j)
\end{align}

Another way to look at this matrix multiplication product is by using an inner product.
Redefine the matrix A in terms of two "row" vectors and B in terms of 5 "column" vectors.

\begin{align*}
A &= \left[ 
\begin{array}{ccc}
1 & 2 & 3\\
4 & 5 & 6\\
\end{array} \right]\\
%
&= \left[ 
\begin{array}{c}
a_{1}\\
a_{2}
\end{array} \right]
\end{align*}
where
\begin{align*}
a_{1} &= \left[ 
\begin{array}{c}
1\\
2\\
3
\end{array} \right]\\
%
a_{2}&= \left[ 
\begin{array}{c}
4\\
5\\
6
\end{array} \right]
\end{align*}

and 

\begin{align*}
B = \left[ 
\begin{array}{ccccc}
b_{1} & b_{2} & b_{3} & b_{4} & b_{5}
\end{array} \right]
\end{align*}

where 
\begin{align*}
b_{1} &= \left[ 
\begin{array}{c}
7\\
12\\
17
\end{array} \right]
\end{align*}
and so on. Then we can redefine the $(i,j)$ element of $A$ times $B$ as an inner product
\begin{align}
    A B (i,j) &= \sum_{r=1}^{3} a(i,r) b(r,j)\\
              &= a_{i}'b_{j}
\end{align}




## matrix times vector

Consider a vector $\beta$ and matrix $X$. The product is a vector, where the ($i^{\text{th}}$) element equals

\begin{align}
    X \beta (i) = \sum_{j} X(i,j) \beta_{j}
\end{align}
or the inner product 
\begin{align}
    X \beta (i) =  x'_{i} \beta
\end{align}

where $x_{i}$ is the $i^{\text{th}}$ row vector of the matrix $X$



## Matrix notation for Simple Linear regression

The above terminology and methods manipulating vectors and matrices can allow us to express linear regression as an operation on matrices and vectors.

### model form (system of equations)

Simple linear regression relates a variable $x$ to a variable $y$ by a simple formula
\begin{align}
y &= \beta_{0} + \beta_{1} x + \epsilon\\
\epsilon & \sim N(0,\sigma^{2})
\end{align}
A simple linear regression equation states any value $y$ can be probabilistically predicted or explained by knowing the corresponding value $x$, $\beta_{0}$, $\beta_{1}$, and the variance $\sigma^{2}$ .
Given a list of $n$ values for $x$, a value for $\beta_{0}$ and a value for $\beta_{1}$, we can rewrite the above equation in matrix notation.
$$
y = X\beta + \epsilon
$$
where $y$ is a vector of length $n$, 
$$ y = 
\left[ 
\begin{array}{c}
y_{1}\\
y_{2}\\
\vdots\\
y_{n}
\end{array} \right]
$$

$\beta$ is a vector containing $\beta_{0}$ and $\beta_{1}$,

$$ \beta = 
\left[ 
\begin{array}{c}
\beta_{0}\\
\beta_{1}\\
\end{array} \right],
$$
and 
$$ X = 
\left[ 
\begin{array}{cc}
1 & x_{1}\\
1 & x_{2}\\
1 & x_{3}\\
\vdots & \vdots\\
1 & x_{n}
\end{array} \right]
$$
is a matrix; the first colummn all ones and the second column the values of $x$.
Epsilon is a vector of length $n$
$$ \epsilon = 
\left[ 
\begin{array}{c}
\epsilon_{1}\\
\epsilon_{2}\\
\vdots\\
\epsilon_{n}
\end{array} \right]
$$

every value following a Normal distribution with variance $\sigma^{2}$.

Written this way, we can define a structure or functional form for all values of $y$ and $x$ at once.
The functional form does not look that different from our original $y=\beta_{0} + \beta_{1}x + \epsilon$, and is even more compact.




 


### probability form

The equation 
\begin{align}
y &= X\beta + \epsilon\\
\epsilon & \sim N(0,\sigma^{2})
\end{align}
explains the probabilstic, and linear relationship, between $x$ and $y$. But I believe we can do better.
Tha above equation can confuse the non-statistically inclined. 
Oftne, they may focus on the linear relationship, forgetting the probabilistic component because of how it is writtne.
The $\epsilon$ appears like an after thought.

To more clearly communicate the fact that the relationship between $y$ and $x$ is probabilistic, we can write
$$
y \sim N(X\beta,\sigma^{2}), 
$$
read y is Normally distributed with mean $X\beta$ and variance $\sigma^2$.
This expression, called the probabilstic form, more clearly communicates that the relationship between $y$ and $x$ is not deterministic, and allowed to fluctuate around a mean that depends on $x$ and on $\beta$.





```R

```
