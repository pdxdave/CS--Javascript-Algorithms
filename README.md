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
function mergeSort (arr) {
    if (arr.length < 2) {
      return arr;
    }

    var mid = Math.floor(arr.length / 2);
    var subLeft = mergeSort(arr.slice(0, mid));
    var subRight = mergeSort(arr.slice(mid));

    return merge(subLeft, subRight);
}

function merge (node1, node2) {
    var result = [];
    while (node1.length > 0 && node2.length > 0)
        result.push(node1[0] < node2[0]? node1.shift() : node2.shift());
    return result.concat(node1.length? node1 : node2);
}


console.log(mergeSort([3,5,1,8,9,11,34,2,23]))
```
#### Linked List
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
