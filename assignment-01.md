

# CMPS 2200 Assignment 1

**Name:** Roberto Diniz Junqueira


In this assignment, you will learn more about asymptotic notation, parallelism, functional languages, and algorithmic cost models. As in the recitation, some of your answer will go here and some will go in `main.py`. You are welcome to edit this `assignment-01.md` file directly, or print and fill in by hand. If you do the latter, please scan to a file `assignment-01.pdf` and push to your github repository. 
  
  

1. (2 pts ea) **Asymptotic notation** (12 pts)

  - 1a. Is $2^{n+1} \in O(2^n)$? Why or why not? 
.  
.  Yes, 2^(n+1) is in O(2^n)
.  This is because:
.  2^(n+1) equals 2 * 2^n, meaning it's just 2 times 2^n, and in Big-O notation, constant multipliers like 2 don't matter, so it's O(2^n)
. 

  - 1b. Is $2^{2^n} \in O(2^n)$? Why or why not?     
.  
.  No, 2^(2^n) is not in O(2^n)
.  This is because:
.  2^(2^n) grows much faster than 2^n, and for large values of n, 2^(2^n) becomes significantly bigger than 2^n, so it's not O(2^n)
.  

  - 1c. Is $n^{1.01} \in O(\mathrm{log}^2 n)$?    
.  
.  No, n^(1.01) is not in O(log(n)^2)
.  This is because:
.  Polynomial functions like n^(1.01) grow faster than logarithmic functions, so as a result, n^(1.01) will always outpace log(n)^2 for large n
.  

  - 1d. Is $n^{1.01} \in \Omega(\mathrm{log}^2 n)$?  
.  
.  Yes, n^(1.01) is in Omega(log(n)^2)
.  This is because:
.  Polynomial functions grow faster than logarithmic ones, so n^(1.01) is always at least as big as log(n)^2 times some constant
.  

  - 1e. Is $\sqrt{n} \in O((\mathrm{log} n)^3)$?  
.  
.  No, sqrt(n) is not in O((log(n))^3)
.  This is because:
.  sqrt(n) grows faster than any log function raised to a power, and eventually sqrt(n) surpasses (log(n))^3, and fails the big-O condition
.  

  - 1f. Is $\sqrt{n} \in \Omega((\mathrm{log} n)^3)$?  
.  
.  Yes, sqrt(n) is in Omega((log(n))^3)
.  This is because:
.  sqrt(n) grows faster than (log(n))^3, so sqrt(n) will always eventually be bigger than some constant multiple of (log(n))^3
.  

2. **SPARC to Python** (12 pts)

Consider the following SPARC code of the Fibonacci sequence, which is the series of numbers where each number is the sum of the two preceding numbers. For example, 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610 ... 
$$
\begin{array}{l}
\mathit{foo}~x =   \\
~~~~\texttt{if}{}~~x \le 1~~\texttt{then}{}\\
~~~~~~~~x\\   
~~~~\texttt{else}\\
~~~~~~~~\texttt{let}{}~~(ra, rb) = (\mathit{foo}~(x-1))~~,~~(\mathit{foo}~(x-2))~~\texttt{in}{}\\  
~~~~~~~~~~~~ra + rb\\  
~~~~~~~~\texttt{end}{}.\\
\end{array}
$$ 

  - 2a. (6 pts) Translate this to Python code -- fill in the `def foo` method in `main.py`  

  - 2b. (6 pts) What does this function do, in your own words?  

.  
.  foo(x) recursively calculates the x-th fibonacci number by returning x, if x is 0 or 1, or if not, by returning the sum of the two previous fibonacci numbers, foo(x-1) and foo(x-2)
.  
.  
.  
.  
.  
.  
  

3. **Parallelism and recursion** (26 pts)

Consider the following function:  

```python
def longest_run(myarray, key)
   """
    Input:
      `myarray`: a list of ints
      `key`: an int
    Return:
      the longest continuous sequence of `key` in `myarray`
   """
```
E.g., `longest_run([2,12,12,8,12,12,12,0,12,1], 12) == 3`  
 
  - 3a. (7 pts) First, implement an iterative, sequential version of `longest_run` in `main.py`.  

  - 3b. (4 pts) What is the Work and Span of this implementation?  

.  
.  The solution has Work O(n) and Span is also O(n), since it checks each element exactly once and each check depends on completing the previous one
.  
.  
.  
.  
.  
.  
.  


  - 3c. (7 pts) Next, implement a `longest_run_recursive`, a recursive, divide and conquer implementation. This is analogous to our implementation of `sum_list_recursive`. To do so, you will need to think about how to combine partial solutions from each recursive call. Make use of the provided class `Result`.   

  - 3d. (4 pts) What is the Work and Span of this sequential algorithm?  
.  
.  The recursive solution has Work O(n) because every element is checked once, and Span O(log n) because the array is divided in half each time
.  
.  
.  
.  
.  
.  
.  
.  
.  


  - 3e. (4 pts) Assume that we parallelize in a similar way we did with `sum_list_recursive`. That is, each recursive call spawns a new thread. What is the Work and Span of this algorithm?  

.  
.  With parallel recursion, Work remains O(n), and Span becomes O(log n), as each half is checked simultaneously
.  
.  
.  
.  
.  
.  

