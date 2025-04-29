# EX 2C BACKTRACKING- SUBSET SUM PROBLEM
## DATE: 11.03.2025
## AIM:
To demonstrate that the sum of the subset of a given set is equal to the given sum.

## Algorithm 

1. Define `SubsetSum(a, i, sum, target, n)` to recursively check if a subset with the given sum exists.  
2. If index `i` equals `n`, return whether the current `sum` is equal to `target`.  
3. If the current `sum` exceeds the `target`, return `False` (prune the branch).  
4. If the current `sum` equals the `target`, return `True` (valid subset found).  
5. Recursively call `SubsetSum` by either **excluding** the current element or **including** it and adding `a[i]` to `sum`.  
6. Read input `size` to determine the number of elements in the list `a`.  
7. Use a loop to input `size` integers into list `a`.  
8. Read the target sum value from the user.  
9. Call `SubsetSum(a, 0, 0, target, n)` to initiate the recursive search.  
10. If the result is `True`, print the input array and `"True, subset found"`.  
11. Otherwise, print the input array and `"False, subset not found"`.  

## Program:
```
/*
Program to implement Subset sum problem.
Developed by: AKSHAYAA M
Register Number: 212222230009 
*/
```
```python
def SubsetSum(a,i,sum,target,n):
    if i == n:
        return sum==target
    if sum>target:
        return False
    if sum==target:
        return True
        
    return SubsetSum(a,i+1,sum,target,n) or SubsetSum(a,i+1,sum+a[i],target,n)
    
a=[]
size=int(input())
for i in range(size):
    x=int(input())
    a.append(x)

target=int(input())
n=len(a)
if(SubsetSum(a,0,0,target,n)==True):
    for i in range(size):
        print(a[i])
    print("True,subset found")
else:
    for i in range(size):
        print(a[i])
    print("False,subset not found")
```

## Output:

![image](https://github.com/user-attachments/assets/4ae00ae1-7963-4175-aac3-a8bb04ecd8b0)


## Result:
The Subset Sum program executed successfully, and the result was determined based on whether a subset matching the target sum was found or not.
