# Frequency Counter Pattern - Anagram Detection

## Function Overview
The purpose of this function is to determine if both inputs are considered anagrams of each other. Inputs will always be lowercase strings that only contain characters a-z.


## Data Inputs
* 'test' , 'tset -- should return true
* 'anagram' , 'nagaram' -- should return true
* 'rat' , 'car' -- should return false
* 'qwerty' , 'qeywrt' -- should return false


## Function Implementations

### Time Complexity - O(n)

```js
function isValidAnagram(input1, input2) {
  if (input1.length !== input2.length) {
    return false
  }

  const characterLookup = {}

  for (let char in input1) {
    const value = input1[char]
    characterLookup[value] = ((characterLookup[value] || 0) + 1)
  }

  for (let char in input2) {
    const character = input2[char]
    if (!characterLookup[character]) {
      return false
    }

    characterLookup[character] -= 1
  }

  return true
}
```