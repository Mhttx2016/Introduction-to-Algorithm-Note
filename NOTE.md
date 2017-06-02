# Introduction-to-Algorithm-Note
## 15.3 Elements of dynamic programming
two key ingredients that an optimization problem must have in order for dynamic programming to apply: optimal
substructure and overlapping subproblems.
### Optimal substructure

>**optimal substructure:** a problem exhibits optimal substructure if an optimal solution to the problem contains within it optimal solutions to subproblems, we must take care to ensure that the range of subproblems we consider includes those used in an optimal solution.

>**space of subproblems:**  as simple as possible and then expand it as necessary.

>**Optimal substructure varies across problem domains in two ways:**
>>1. how many subproblems an optimal solution to the original problem uses, and
>>2.  how many choices we have in determining which subproblem(s) to use in an optimal solution.

>**running time of a dynamic-programming:** depends on the product of two factors: the number of subproblems overall and how many choices we look at for each subproblem.

>**bottom-up fashion:** first find optimal solutions to subproblems and, having solved the subproblems, we find an optimal olution to the problem. Finding an optimal solution to the problem entails making a choice among subproblems as to which we
will use in solving the problem.  **The cost** of the problem solution is usually the subproblem costs plus a cost that is directly attributable to the choice itself.

>**difference between greedy algorithms and dynamic programming:** instead of first finding optimal solutions to subproblems and then making an informed choice, greedy algorithms first make a “greedy” choice—the choice that looks best at the time—and then solve a resulting subproblem, without bothering to solve all possible related smaller subproblems.

### Subtleties

>**Unweighted shortest path** vs **Unweighted longest path**

The unweighted shortest-path problem exhibits optimal substructure by introducing an intermediate vertex,while for longest simple paths, not only does the problem lack optimal substructure, but we cannot necessarily assemble a “legal” solution
to the problem from solutions to subproblems.? Although a solution to a problem for both longest and shortest paths uses
two subproblems, the subproblems in finding the longest simple path are not **independent**

>**independent:** We mean that the solution to one subproblem does not affect the solution to another subproblem of the same problem.

### Overlapping subproblems
>**overlapping subproblems:** When a recursive algorithm revisits the same problem repeatedly.
Dynamic-programming algorithms typically take advantage of overlapping subproblems by **solving each subproblem once** and then **storing the solution in a table** where it can be looked up when needed, using constant time perlookup.

>**runtime analysis:** Whenever a recursion tree for the natural recursive solution to a problem contains
the same subproblem repeatedly, and the total number of distinct subproblems is small, dynamic programming can improve efficiency, sometimes dramatically, usuall from exponential to quadradic.

### Reconstructing an optimal solution

As a practical matter, we often store which choice we made in each subproblem in
a table so that we do not have to reconstruct this information from the costs that we
stored.

>**Memoization:** A memoized recursive algorithm maintains an entry in a table for the solution to each subproblem.

	MEMOIZED-MATRIX-CHAIN(p):
		LOOKUP-CHAIN(m,p,i,j):
	'''
		Function: A memoized recursive algorithm maintains an entry 
		in a table for the solution to each subproblem.
		
		Algorithm: Each table entry initially contains a special value to 
		indicate that the entry has yet to be filled in. When the subproblem
		is first encountered as the recursive algorithm unfolds, 
		its solution is computed and then stored in the table.Each subsequent
		time that we encounter this subproblem, we simply look up the 
		value stored in the table and return it.
		
		Runtime:O(n^3)
	'''
	
## 15.4 Longest common subsequence

