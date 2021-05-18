---
layout: post
current: post
cover:  assets/images/api-gatway.png
navigation: True
title: Rotating Array
date: 2021-05-06 00:00:00
tags: [Data Structures]
class: post-template
subclass: 'post'
author: heyvp7
---

There is a classica cryptography algorith named [Caesar Cipher](https://en.wikipedia.org/wiki/Caesar_cipher). In this algorithm we will be having all the 26 characters (in array arr) and we rotate the array some number of times (say 2 times and is stored in n).

So once we rotate the array two times, we will be having new array like below.

A -> C
B -> D
C -> E
D -> F
...

X -> Z
Y -> A
Z -> B

To achieve this programatically below program will be helpful. We have two algorithms for this. 

### Divide Reverse, Reverse, Reverse

**Divide**
In this algorithm we will be virtually splitting the array into two parts. First part will be from start position (0) to number of times we want to rotate. Second part is from next character of rotation times to end of array.

```java
    private  void rotateUsingReverse(int[] arr, int rotationTimes){
        // In one access two elements are swapped
        reverse(arr, 0, rotationTimes-1);
        reverse(arr, rotationTimes,arr.length-1);

        // here we will have another half number of access.
        reverse(arr, 0,arr.length-1);
    }


    // In one access two elements are swapped
    private void reverse(int[] arr, int startIndex, int endIndex){
        while (startIndex<endIndex){
            int tempNumber = arr[startIndex];
            arr[startIndex] = arr[endIndex];
            arr[endIndex] = tempNumber;
            ++startIndex;
            --endIndex;
        }
    }
 ```
 **Reverse, Reverse, Reverse**
 
 So We have virtually split the array into two segments. Now we take the first segment which ll have number of times the rotation to be made (say if the rotation is 5 times we will have 5 elements).
 
 We will be reversing this first small array,  by the following step.
 
 - First we will be keeping a temporary copy of initial index(0) in temp variable.
 - We will now copy the last element (value at endIndex or value at index 4 for 5 elements), to initial Index
 - Next we will copy the value at inital index to the endIndex
 - Next we will increment the startIndex by 1
 - Next we will decrease the endIndex by 1.

We will be continuing the above step till startIndex is less than endIndex.

Similarly we will do for the next segement of array.  Now we will be reversing the whole array.  Below example will help you understanding.

int[] arrayOfNumber = {1,2,3,4,5,6,7,8,9};
Lets rotate 3 times.

So We will be having 2 virital array
array1 => {1.2.3}
array2 => {4,5,6,7,8,9}

Now we will be reversing the virtual array1 -> {3,2,1}
Now we will be reversing the virtual array2 -> {9,8,7,6,5,4}

Now the arrayOfNumber will be like => {3,2,1,9,8,7,6,5,4}

Now again we will be rotation the whole arrayOfNumber => {4,5,6,7,8,9,1,2,3}


### Divide Reverse, Reverse, Reverse

```java

 private void rotateArray(int[] arr, int rotationTimes){

        int numberOfItemsInSegment =findTheGCD(arr.length,rotationTimes);
        System.out.println(numberOfItemsInSegment);

        for(int startIndex=0; startIndex<numberOfItemsInSegment;++startIndex){
            int tempElement = arr[startIndex];
            int indexToSwap = startIndex;

            while (true) {
                int nextIndexToswp = indexToSwap + rotationTimes;
                if(nextIndexToswp>= arr.length){
                    nextIndexToswp = nextIndexToswp-arr.length;
                }
                if(startIndex==nextIndexToswp){
                    break;
                }
                int swapElement = arr[nextIndexToswp];
                arr[indexToSwap] = swapElement;

                indexToSwap=nextIndexToswp;
            }
            arr[indexToSwap] = tempElement;
        }
       // return arr;
    }

    private int findTheGCD(final int firstNumber, final int secondNumber){

            if(secondNumber == 0){
            return firstNumber;
        }else{
            return findTheGCD(secondNumber,firstNumber%secondNumber);
        }
    }
```
 
