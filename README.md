# CS--Javascript-Algorithms
CS--Javascript-Algorithms


#### Factorial 
```
function recur(num){
  if(num < 1){
    return 1
  }
  return num * recur(num-1)
}

console.log(recur(5)); // 120
```

#### Fibonacci
```
function fibbo(num){
  if(num <= 1){
    return num
  }
  return fibbo(num -1) + fibbo(num-2)
}

console.log(fibbo(10))

```

#### Bubble Sort
The least desirable sorting option since it has a time complexity of 0(n^2).  Still, it's asked about in interviews. What is a bubble sort and how does it work?  Imagine we have an array of numbers. The top value is the number, the bottom value is its place in the array.  The goal is to sort them from lowest to highest.    

```
      2, 7, 4, 1, 5, 3
      0  1  2  3  4  5
      
      We first scan the array comparing the numbers 2 and 7.  If 7 were smaller than 2, we would switch their places.  In this case we don't.  Next, we compare the number 7 to the number 4.  The number 4 is smaller than 7, so they switch places.
      
      2, 4, 7, 1, 5, 3
      0  1  2  3  4  5
      
      Now we compare number 7 to the number 1.  The number 1 switches with 7
      
      2, 4, 1, 7, 5, 3
      0  1  2  3  4  5
      
      Next, compare number 7 with 5, and we swap again
      
      2, 4, 1, 5, 7, 3
      0  1  2  3  4  5
      
      And once more we compare 7 with 3, and the swap happens again
      
      2, 4, 1, 5, 3, 7
      0  1  2  3  4  5
      
      Now this is the result of the first pass.  In order to get the numbers in order from lowest to highest, we have to do the process as many times as it takes.  This is why bubble sort is not a very good solution for sorting.
      
```

```

So how does this solution work? In this case, 'i' represents the length of the array.
Using the numbers up top, it would be a lenth of 6.  We decrement 'i' by one as we
move down the array to make sure we've hit all the numbers.  

const bubbleSort = (arr) => {
  let temp
  for(let i = arr.length; i > 0; i--){
    for(let j = 0; j < i; j++){
      if(arr[j] > arr[j + 1]){
        temp    = arr[j]
        arr[j]  = arr[j + 1]
        arr[j + 1] = temp;
      }
    }
  }
  return arr
}

const arr = [3,4,2,7,9,0]
  
console.log(bubbleSort(arr))
```

#### Insertion Sort

Insertion sort is a simple sorting algorithm that builds the final sorted array (or list) one item at a time. It is much less efficient on large lists than more advanced algorithms such as quicksort, heapsort, or merge sort. ... Efficient for (quite) small data sets, much like other quadratic sorting algorithms.

```
const insert = (nums) => {
  for(let i = 1; i < nums.length; i++){
    for(let j = 0; j < i; j++){
      if(nums[i] < nums[j]){
        
        const spliced = nums.splice(i, 1);
        nums.splice(j, 0, spliced[0])
        
      }
    }
  }
  return nums
}

console.log(insert([7,4,5,1,2,9]))
```

#### Merge Sort

In computer science, merge sort is an efficient, general-purpose, comparison-based sorting algorithm. Most implementations produce a stable sort, which means that the order of equal elements is the same in the input and output. Merge sort is a divide and conquer algorithm.

```
const mergeSort = nums => {
  const sortedArray = [...nums];
  if(sortedArray.length < 2){
    return nums;
  }
  
  const length = sortedArray.length;
  const middle = Math.floor(length/2);
  const left = sortedArray.slice(0, middle);
  const right = sortedArray.slice(middle);
  
  return merge(mergeSort(left), mergeSort(right));
};

  const merge = (left, right) => {
    const results = []
    while(left.length && right.length){
      if(left[0] <= right[0]){
        results.push(left.shift())
      } else {
        results.push(right.shift())
      }
    }
    return results.concat(left, right)
  }
  
console.log(mergeSort([3, 1, 5, 4, 31, 12, 45, 65,26]))
```
#### Linked List

```
function insertNodeAtTail(head, data) {
    //check if the head is null. 
    if(head === null){
        //if head is null, then data is the new node. 
        head = new SinglyLinkedListNode(data)
    } else {
        let currentNode = head
        while(currentNode){
            if(currentNode.next === null){
                //reached the tail
                //currentNode is the tail
                // create a new node instance and add it
                currentNode.next = new SinglyLinkedListNode(data)
                break
            } else {
                // go to the next node
                currentNode = currentNode.next
            }
        }
    }
    //return the head
    return head
}
```


```
/*
head
  head node       node
-----|----   -> ----|----  -> null
 info link     info   link

*/


function LinkedList(){
  // start out with nothing in the list
  var length = 0;
  var head = null;
  
  var Node = function(element){
    // this is where we bring in new elements
    // the next one is set to null
    this.element = element;
    this.next = null;
  }
  
  this.size = function(){
    return length;
  }
  
  this.head = function(){
    return head
  }
  
  this.add = function(element){
    var node = new Node(element)
    if(head === null){
      head = node;
    }else{
      var currentNode = head;
      
      // skipping down the list looking for next nodes
      while(currentNode.next){
        currentNode = currentNode.next;
      }
       // when we get to the end, we add the node
      currentNode.next = node
    }
    length++
  }
  
  
  this.remove = function(element){
    var currentNode = head;
    var previousNode;
    if(currentNode.element == element){
      head = currentNode.next;
    }else{
      while(currentNode.element !== element){
        previous = currentNode;
        currentNode = currentNode.next;
      }
      previousNode.next = currentNode.next
    }
    length --;
  }
 
}
```
