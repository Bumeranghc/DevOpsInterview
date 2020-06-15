# Programming

[Back to contents](README.md)

## Palindrome

Function isPalindrome that checks if a given string (case insensitive) is a palindrome.

```C++
bool isPalindrome (const std::string& str)
{
    bool bResult = true;
    for (unsigned int i = 0; i < str.length()/2; i++)
    {
        if (tolower(str[i]) != tolower(str[str.length()-i-1]))
        {
            bResult = false;
            break;
        }
    }
    return bResult;
}
```

## Maximum subarray sum

The maximum sum subarray problem consists in finding the maximum sum of a contiguous subsequence in an array or list of integers. For example, for `{-2, 1, -3, 4, -1, 2, 1, -5, 4}` it should be 6 as sum of this subsequence: `{4, -1, 2, 1}`.
Easy case is when the list is made up of only positive numbers and the maximum sum is the sum of the whole array. If the list is made up of only negative numbers, return 0 instead.

Empty list is considered to have zero greatest sum. Note that the empty list or array is also a valid sublist/subarray.

Finding the sum:

```c++
int maxSequence(const vector<int>& arr){
  int bestsum = 0, currentsum = 0;
  for (auto& x: arr) // for every element of array
  {
      currentsum + x > 0 ? currentsum += x : currentsum = 0; // Accumulate elements in current sum until that sum is grater than 0
      if (currentsum > bestsum) bestsum = currentsum; // Check if current sum is grater than best sum which is already found
  }
  return bestsum;
}
```

Finding the subarray:

```c++
vector<int> maxSequenceEnchanced(const vector<int>& arr){
  int bestsum = 0, beststart = 0, bestend = 0, currentsum = 0, currentstart = 0;
  for (int i = 0; i < arr.size(); i++)
  {
      currentsum > 0 ? currentsum += arr[i] : currentsum = arr[currentstart = i]; // Extend the existing sequence with the current element or start a new sequence at the current element
      if (currentsum > bestsum) // Check if current sum is grater than best sum which is already found
      {
          bestsum = currentsum;
          beststart = currentstart; // Store indexes of start and end elements
          bestend = i;
      }
  }
  return {arr.begin() + beststart, arr.begin() + bestend + 1};
}
```

