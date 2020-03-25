# Frequency Counter Pattern - Square Values in Array

## Function Overview
The purpose of this function is to determine if all elements, in the first array, exist in the second array. The second array values must be the squared value of the element values from the first array. The order of the element values in each array does not matter.


## Data Inputs
* [1,2,3] , [1,4,9] -- should return true
* [2,4] , [4,6] -- should return false (16 not present)
* [3,5] , [9] -- should return false (25 not present)
* [1,2,1] , [4,4,1] -- should return false (1 only exists once)


## Function Implementations

### Time Complexity - O(n^2)
```js 
function hasSquareValue(array1, array2) {
  if (array1.length !== array2.length) {
    return false
  }

  for (i = 0; i < array1.length; i++) {
    const index = array2.indexOf(array1[i] ** 2)
    if (index == -1) {
      return false
    }
    array2.splice(index, 1)
  }

  return true
}
```

### Time Complexity - O(n)
```js
function hasSquareValue(array1, array2) {
  if (array1.length !== array2.length) {
    return false
  }

  const arrayCounter1 = {}
  const arrayCounter2 = {}

  for (let value of array1) {
    arrayCounter1[value] = ((arrayCounter1[value] || 0) + 1)
  }

  for (let value of array2) {
    arrayCounter2[value] = ((arrayCounter2[value] || 0) + 1)
  }

  for (let key in arrayCounter1) {
    const squareValue = (key ** 2)
    if (!(squareValue in arrayCounter2) || arrayCounter2[squareValue] !== arrayCounter1[key]) {
      return false
    }
  }

  return true
}
```