# 14 Augmenting Data Structures
## 14.1 Dynamic order statistics
**order-statistic tree:** a red-black tree with additional information x.size stored in each node.

**Size:** the number of (internal) nodes in the subtree rooted at x (including x itself), that is, the size of the subtree.
	x.size = x.left.size + x.right.size + 1.
  
**the rank of an element:** the position at which it would be printed in an in-order walk of the tree.

**Retrieving an element with a given rank**

	OS-SELECT(x,i):
	'''
		Function: returns a pointer to the node con-taining 
		the ith smallest key in the subtree rooted at x. 
	
		Algorithm: select in x.left or x.right recursively 
		according the x.left.size
	
		Runtime: O(lgn)
	'''
	
**Determining the rank of an element**

	OS-RANK(T,x):
	'''
		Function: returns the position of x in the linear 
		order determined by an in order tree walk of T .
		
		Algorithm: 
		
		Runtime:O(lgn)
	'''
	
**Maintaining subtree sizes**

	Insertion while maintain the size:
	'''
		Function:
		
		Algorithm: maintain size of node changed in rotations
		
		Runtime:O(lgn)
	'''


	Deletion while maintain the size:
	'''
		Function:
		
		Algorithm:To update the subtree sizes, we simply traverse 
		a simple path from node y (starting from its original 
		position within the tree) up to the root, decrementing 
		the size attribute of each node on the path. 
		
		Runtime:O(lgn)
	'''

## 14.2 How to augment a data structure
**four steps:**

>	1. Choose an underlying data structure.

>	2. Determine additional information to maintain in the underlying data 	structure.
	
>	3. Verify that we can maintain the additional information for the basic modifying operations on the underlying data structure.
	
>	4. Develop new operations
	
**Augmenting red-black trees**
>**Theorem 14.1 (Augmenting a red-black tree):**
	Let f be an attribute that augments a red-black tree T of n nodes, and suppose that the value of f for each node x depends on only the information in nodes x, x.left,
and x.right, possibly including x.left.f and x.right.. . Then, we can maintain the
values of f in all nodes of T during insertion and deletion without asymptotically
affecting the O(lgn) performance of these operations.

## 14.3 Interval trees
**closed interval:** an ordered pair of real numbers [t1, t2] 

**interval tree:** a red-black tree that maintains a dynamic set of elements, with each element x containing an interval x.int. 

**x.int:** [t1,t2]

**x.max:** the maximum value of any interval endpoint stored in the subtree 	rooted at x.     x.max = max(x.int.high; x.left.max; x.right.max)
	
**x.key:** the low endpoint

	INTERVAL-SEARCH(T, i):
	'''
		Function:returns a pointer to an element x in the interval tree T 
		such that x:int overlaps interval i, or a pointer to the sentinel 
		T.nil if no such element is in the set.
		
		Algorithm: search x.left or x.right according to whether x.left.max >= i.low
		
		Runtime: O(lgn)
	'''
	

