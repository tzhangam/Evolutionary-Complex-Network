#Useful things in numpy
---

First and foremost, the ***ndarray*** is the core and soul of numpy.

---
*  ***Simple Creation***

  ```python
  #The following are for creation of 1-D arrays
  a=np.array([1,2,3])
  a=np.arange(1000)	#0~999
  a=np.arange(1,5) #1,2,3,4
  a=np.arange(1,5,2) #[1,3]. Interval length=2.
  a=np.linspace(1,5,10) #Start, End, number of points. Start and end are included.
  a=np.array([1,2,3],dtype=float64) #Manually specifying the datatype in the nd array.
  ```

*	Multi-dimensional arrays, ***shape***, matrices

  ```python
  #Creating 2-D array
  a=np.array([[1,2],[3,4,]]) # A 2x2 matrix
  a.ndim # Here should be 2. The dimension of a.
  ```

  ```python
  #The concept of SHAPE
  a=np.array([[1,2],[3,4],[5,6]])
  a.shape #Here is (3,2), a tuple object, as a is a 3x2 matrix.
  a.reshape(2,3) #Using the elements in a, change the a into a 2x3 matrix, ordering the elements in the C code order by default.

  #C style order: Iterate in a single row from left to right, then move down row by row.
  #Fortran style order: Iterate in a single column from top to bottom, then move right column by column.

  b=a.ravel() # b gets the flatten 1-D result of a, notice reshape with actually affect the shape of a, while ravel will not.
  ```

  ```python
  #Popular initialization of multi-dimension arrrays

  a=np.zeros((3,3)) # Initialize a 3x3 matrix with all 0's in entries. Notice the shape argument is of type tuple.

  a=np.ones((4,2)) #Initialize a 4x2 matrix with all 1's.

  ```

*	Termwise operation on ndarrays

  ```python
  a.min()
  a.max()
  a.std()
  a.sum()
  C=A+B # A,B,C are ndarrays. Termwise addition of A and B into C
  C=A.dot(B) # This is indeed matrix multiplication, given A, B, C are matrices.
  C=np.sqrt(A) #Some more sophisticated function are not class method of ndarray.


  c=a>4 # c has the same shape as a, and is the indicator matrix of a telling which entries of a are greater than 4.

  a[c] # This is a 1-D array, containing all entries in a that is greater than 4.

  a[c]=-1	# Assign -1 to all entries in a which is formerly greater than 4.

  ```

*	***Concatenating nd arrays, splitting nd arrays***

  ```python
  #Stacking is concatenation
  c=np.vstack((a,b)) # Put a over b thus generating c.
  d=np.hstack((a,b)) # Similar
  #Notice the argument should be tuples.

  #Splitting is splitting
  c=np.hsplit(a,3)	# Split a into 3 horizontal parts, store the 3 parts as a ndarray with 3 primary "Entries" into c.

  c=np.vsplit(a,2)	#Similar.
  ```

*	Advanced Indexing and Iteration

  ```python
  #Indexing
  a[0:2] # From 0th element to 1st element, the 2nd element is not included
  a[1,2] # Access the entry at 1st row( start from 0th row ), 2nd column ( start from 0th column)
  a[0:2,2] # The partial matrix containing 0th~1st row, and 2nd column
  a[:, 1:3] # Get all rows, column 1 to 2.
  ```

  ```python
  #Advance iteration using nditer

  # C order and Fortran order
  for x in np.nditer(a, order='C'):
      
  for x in np.nditer(a, order='F'):

  # Enable writing mode, iterate by reference
  for x in np.nditer(a, op_flags=['readwrite']):
      x[...]=function()
      
      #[...]: This symbol is a convention to follow when using writing mode#
  ```

*	Final remark

  Dimension compatibility:	Dim 1 is compatible with Dim 2 iff

  ​					1) Dim 1 == Dim 2

  ​					or

  ​					2) Dim 1 ==1 or Dim 2==1
