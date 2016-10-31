Dynamic Programming
A alg design technique, it is suitable for Optimization Problem.

DP = a form of "careful" brute force.
DP = subproblems + reuse.


* Fibonaci numbers
* Shortest paths

Fibonaci:
F1 = F2 = 1
Fn = F(n-1) + F(n-2)


Naive Recursive Algorithm:
fib(n):
	if n<=2: f = 1
	else: f = fib(n-1) + fib(n-2)
	return f

exponential time, runtime is bad.
T(n) = T(n-1) + T(n-2) + O(1)
T(n) >= 2T(n-2)
T(n) >= O(2^(n/2))

General Method to improve the naive recursive method.

####Memoized DP Algorithm
The idea is simple, when we compute a Fibonaci number, we put it into a dictionary.

memo ={}, then we check if we solved the problem for nth number, if so, return that answer from the dictionary, otherwise, computer it.

```
fib(n):
	if n in memo: return memo[n];
	if n<=2: f=1
	else: f = fib(n-1) + fib(n-2)
		memo[n] = f
		return f
```

The part of code 
```
	if n<=2: f=1
	else: f = fib(n-1) + fib(n-2)
```
is identical of that from the Naive recursive.

The reason that the memorized DP algorithm is more efficient is that:

```
				  Fn
			   /     \
		  F(n-1)    F(n-2)
		  /    \      /   \
	F(n-2) F(n-3) F(n-3) F(n-4)
	 .      .      .       .
	 .      .      .       .
	 .      .      .       .
```
A lot of calculation are being repeated using the naive recursive.


fib(k) only recurses the first time it's called, for all k.


Memorized calls cost constant time O(1).
# Non memorized calls is n.
fib(1),fib(2),fib(3),fib(4)...
# non recursive work per call = O(1).
=>time = O(n) 
which is the product of # nonmemorized calls and work per call O(1).


DP = recursion + memorization
- memoize (remember) & reuse solutions
to subproblems that help solve the problem.

1. what are the sub problems?

time = # subproblems * time per subproblem

in the case of fibonaci number:
=> time = n * O(1)


####Bottom-up DP Algorithm
```
fib = {}
for k in range(1,n+1):
	if k<=2: f =1
	else: f = fib[k-1] + fib[k-2]
	fib[k] = f;
return fib[n];
```

- does exactly the same thing as the memoized version, in the exactly same order
- topological sort of subproblem dependency DAG （directed acyclic graph):
	f[k-1] and f[k-2] are always solved before f[k].
- can often save space.

