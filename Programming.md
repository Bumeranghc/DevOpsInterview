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

## Hebrew sort

Write a program with function that gets a paragraph written in English, and returns the paragraph’s words sorted alphabetically.
But, instead of the alphabet being in English order, the alphabet is in the Hebrew order:
`A, B, G, D, H, V, Z, J, T, Y, K ,L, M, N, S, I, P, X, Q, R, W, U, C, E, F, O`

Punctuation should be removed from the input.

For Example, for the following input:
`Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua`
The function should return or print the following:
`adipiscing aliqua amet do dolor dolore tempor labore Lorem magna sit sed incididunt ipsum ut consectetur et elit eiusmod`

```c++
/*******************************************************************************
 * The function that gets a paragraph written in English, and returns the
 * paragraph's words sorted alphabetically.
 *
 * The alphabet for sort is in the Hebrew order:
 * A, B, G, D, H, V, Z, J, T, Y, K,L, M, N, S, I, P, X, Q, R, W, U, C, E, F, O
 *
 * The punctuation is removed from the input.
 *
 * Usage:
 *
 * This is console C++ application.
 * 1. Compile and run the app
 * 2. Type or insert a paragraph.
 * 3. Press <Enter> to finish input and you will get a Hebrew-style sorted words
 * from the paragraph.
*******************************************************************************/

#include <iostream>
#include <list> //will use list as container for words from paragraph
#include <map> //will use associative arrays to implement Hebrew-style order for sort
#include <string> //will operate with strings in paragraph

using namespace std;

//definition of the Hebrew-style order
map <char, int> order = {{'A', 0},
                         {'B', 1},
                         {'G', 2},
                         {'D', 3},
                         {'H', 4},
                         {'V', 5},
                         {'Z', 6},
                         {'J', 7},
                         {'T', 8},
                         {'Y', 9},
                         {'K', 10},
                         {'L', 11},
                         {'M', 12},
                         {'N', 13},
                         {'S', 14},
                         {'I', 15},
                         {'P', 16},
                         {'X', 17},
                         {'Q', 18},
                         {'R', 19},
                         {'W', 20},
                         {'U', 21},
                         {'C', 22},
                         {'E', 23},
                         {'F', 24},
                         {'O', 25}};

// implementation of not case sensitive comparator
bool comparator (const std::string& first, const std::string& second)
{
    unsigned int i=0;
    while ( (i<first.length()) && (i<second.length()) )
    {
        if (order[toupper(first[i])] < order[toupper(second[i])]) return true;
        else if (order[toupper(first[i])] > order[toupper(second[i])]) return false;
        ++i;
    }
    return ( first.length() < second.length() );
}

//implementation of sort using list as container and built-in sort with our comparator
string hebrewsort(string input)
{
    list<string>::iterator it;
    list<string> paragraph;
    int current = 0, next = 0;
    //remove all the punctuation and split the input to list elements
    do
    {
        if (order.count(toupper(input[next])) == 0)
        {
            if (current < next) paragraph.push_back (input.substr( current, next - current ));
            current=next + 1;
        }
        next++;
    }
    while (next <= input.length());
    paragraph.sort(comparator);
    string result = "";
    for (it=paragraph.begin(); it!=paragraph.end(); ++it)
        result += *it + " ";
    return result;
}

//the main function
int main ()
{
    string text;
    cout << "Enter the text: " << endl;
    getline(cin, text);
    cout << "Hebrew-style sort:" << endl << hebrewsort(text);
}
```

