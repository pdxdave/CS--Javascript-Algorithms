# CS--Javascript-Algorithms
CS--Javascript-Algorithms


#### Recursion 
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

``

#### Insertion Sort
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
