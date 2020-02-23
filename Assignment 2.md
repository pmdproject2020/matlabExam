
# Assignment 2 progs :

---

> Q1.	Write a menu driven program to sort a list using the following methods:
Menu for Sorting Methods
>1.	Bubble Sort Method
>2.	Insertion Sort Method
>3.	Quit

>Your Choice :1/2/3 ->

## Answer : 
---

>structure of the prog

---
1. menu function
2. swap function
3. main function

    1.switch case 
        
        * choice 1 : bubble_sort function
        * choice 2 : insertion_sort funtion
        * choice 3 : quit
---



## swap function
```octave
function [x,y]=swap(a,b)
  x=b;
  y=a;
endfunction
```

## Bubble sort
```octave
function arr=bubble_sort(a,n)
   sc=0;
  for i=1:n
    for j=1:n-1
      if (a(j) > a(j+1))
        sc=sc+1;
        disp(["\nswapped =>  " , num2str(sc) ,"\n"])
        [ a(j) , a(j+1) ] = swap( a(j), a(j+1) );
        a  #to print the array
      endif
    endfor #inner
  endfor #outter
  arr=a;
 endfunction 
```

# Insertion Sort
---

```octave

function arr=insertion_sort(a,n)
   #sc=0;
  for i=1:n
    j=i;
    while(j>1 && a(j) < a(j-1))
      #disp("swapped")
      [ a(j) , a(j-1) ] = swap( a(j) , a(j-1) );
      a
      j--;
    endwhile  
  endfor #outter
  arr=a;
endfunction

```

# Insertion Sort
---
>logic

```
arr[] = 64 25 12 22 11

// Find the minimum element in arr[0...4]
// and place it at beginning
11 25 12 22 64

// Find the minimum element in arr[1...4]
// and place it at beginning of arr[1...4]
11 12 25 22 64

// Find the minimum element in arr[2...4]
// and place it at beginning of arr[2...4]
11 12 22 25 64

// Find the minimum element in arr[3...4]
// and place it at beginning of arr[3...4]
11 12 22 25 64 
```
---

>Function 
---
```octave

function sorted_arr=selection_sort(a,n)
  for i=1:n
    min_indx=i;
    for j=i+1:n
      if(a(j)<a(min_indx))
        min_indx=j;
      endif
    end #inner for
    [a(i) , a(min_indx)] = swap(a(i) , a(min_indx))
  end #outer for
  sorted_arr=a;
endfunction

```
---

## Binary search

```octave
function indx = binSrc ( ar , ele)
  l=1;
  r=numel(ar); #no of element
  indx=-9;
  while(l < r)
      mid=floor((l+r)/2)
      if(ar(mid)==ele)
        indx=mid
        break
      elseif(ar(mid) > ele)
        r=mid;
      else
        l=mid+1;
      end
  endwhile
endfunction
```

# function to get user input
### and store them into an Array
---
```octave
function [arr,noe]=getInp
  noe= input("\nHow many elements do u wanna store : ");
  disp("\n")
  for i=1:noe
    disp([num2str(i)," : "]);
    A(i)=input('val : ');
  end
  arr=A;
end
```
---
## Another way to do the same
```octave
 arr = input("Enter array : ")  
```
```
 arr = input("Enter array : ")
Enter array : [1 2 3 4 5 6 6 6 424 ]
arr =

     1     2     3     4     5     6     6     6   424

```
---
> XD , this is one liner
---

# Menu function 

### it returns the choice
---

```octave
function choice=menu
    display([
        "\n\t1. Bubble Sort  ",
        "\n\t2. Insertion Sort  ",
        "\n\t3. Quit  "
    ])
    choice=input("\n\tYour Choice : ");
 end

```
---

## Main function 
---
```octave
function main_fun(choice)
    
    switch (choice)
    case 1
        display("\nin case 1")
        [a,n]=getInp()
        v=bubble_sort(a,n);
        disp(["\nfinal array : \n",num2str(v),"\n"]);
    case 2
        display("\nin case 2")
        [a,n]=getInp()
        v=insertion_sort(a,n);
        disp(["\nfinal array : \n",num2str(v),"\n"]);
    case 3
        exit
    end
endfunction
```

# Recursive Functions

- sum of n (1-200) numbers
- product of n numbers
- N-th Fibonacci no
- Tower of Hanoi

# sum of n numbers
---

```octave
function s = sumN(n)
    if(n<0)
      s=0;
      return
    end
    s=n+sumN(n-1);
endfunction```
---
# Product of N num
```octave
function p = prodN_v1(n)
    if( n==0)
      p=0;
      return
    elseif (n==1)
      p=1;
      return
    end
   p=n*prodN_v1(n-1);
endfunction
```
---
> Example ->

```octave
sumN(10)
ans = 55
prodN_v1(6)
ans =  720
```

# N-th Fibonacci Num
---
- **Code**
```octave
function term= fib (n)
  if(n<=0)
    term = 0;
    return
  end
  if (n==1 || n==2)
    term=1;
    return
  end
  term = fib(n-1) + fib(n-2); 
endfunction 
```
---
> example
```
 fib( 6 )
 ans = 8
```

# Tower of Hanoi
---
```
Take an example for 2 disks :
Let rod 1 = 'A', rod 2 = 'B', rod 3 = 'C'.

Step 1 : Shift first disk from 'A' to 'B'.
Step 2 : Shift second disk from 'A' to 'C'.
Step 3 : Shift first disk from 'B' to 'C'.

The pattern here is :
Shift 'n-1' disks from 'A' to 'B'.
Shift last disk from 'A' to 'C'.
Shift 'n-1' disks from 'B' to 'C'.
```
---
![img](https://media.geeksforgeeks.org/wp-content/uploads/tower-of-hanoi.png)

---
> Example
---
```
Input : 2
Output : Disk 1 moved from A to B
         Disk 2 moved from A to C
         Disk 1 moved from B to C

Input : 3
Output : Disk 1 moved from A to C
         Disk 2 moved from A to B
         Disk 1 moved from C to B
         Disk 3 moved from A to C
         Disk 1 moved from B to A
         Disk 2 moved from B to C
         Disk 1 moved from A to C
```
---

**Code**
---
---
```octave
clc
clear all
function T_of_H(n,A,B,C)

  if n > 0
    T_of_H(n-1,A,C,B)
    fprintf("\nMove disk %d from %s to %s \n",n,A,C)
    T_of_H(n-1,B,C,A)
  end
end

T_of_H(3,"A","B","C")
```


```octave

```
