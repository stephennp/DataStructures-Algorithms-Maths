# Motivation Problem

- Given a string , find the longest sub string that occurs at least times
- Brute Force method: For every sub string `X` of `S`, one can find all the occurrences of `X` in `S` by `KMP` .`KMP` takes O(N) time, so the total time for this brute force method will be O(N^3).
- A faster solution using hashing: We can binary search the length of the sub string. For a current length `X`  in the binary search, hash of every sub string of length `X`  can be found in `O(N)` time. While doing this, the hashes can be stored in a dictionary, and when all sub strings of length `X` are processed, the hash with maximum frequency is to be checked if it has frequency greater than equal to `M`. This takes `O(N(log(N())))^2`  time, where a log term comes due to maintaining the dictionary(map in C++).

# A solution using Suffix Array

- A Suffix Array is a sorted array of suffixes of a string. Only the indices of suffixes are stored in the string instead of whole strings. For example: Suffix Array of `banana` would look like this:

```
string: banana

0 -> banana
1 -> anana
2 -> nana
3 -> ana
4 -> na
5 -> a

- then sort suffixes with alphabetically:

5 -> a
3 -> ana
1 -> anana
0 -> banana
4 -> na
2 -> nana

```
# Steps of implementation
- search the `nan` if it existed in the prefix of suffixes
- start index left:0 and right: 5
- use binary search divided the array into 2 parts, use mid = (left+right)/2 = 2
- if mid > left alphabet -> move to right part
- else move to left part accordingly

# Build suffix array

```c++
// Naive algorithm for building suffix array of a given text
#include <iostream>
#include <cstring>
#include <algorithm>
using namespace std;
  
// Structure to store information of a suffix
struct suffix
{
    int index;
    char *suff;
};
  
// A comparison function used by sort() to compare two suffixes
int cmp(struct suffix a, struct suffix b)
{
    return strcmp(a.suff, b.suff) < 0? 1 : 0;
}
  
// This is the main function that takes a string 'txt' of size n as an
// argument, builds and return the suffix array for the given string
int *buildSuffixArray(char *txt, int n)
{
    // A structure to store suffixes and their indexes
    struct suffix suffixes[n];
  
    // Store suffixes and their indexes in an array of structures.
    // The structure is needed to sort the suffixes alphabatically
    // and maintain their old indexes while sorting
    for (int i = 0; i < n; i++)
    {
        suffixes[i].index = i;
        suffixes[i].suff = (txt+i);
    }
  
    // Sort the suffixes using the comparison function
    // defined above.
    sort(suffixes, suffixes+n, cmp);
  
    // Store indexes of all sorted suffixes in the suffix array
    int *suffixArr = new int[n];
    for (int i = 0; i < n; i++)
        suffixArr[i] = suffixes[i].index;
  
    // Return the suffix array
    return  suffixArr;
}
  
// A utility function to print an array of given size
void printArr(int arr[], int n)
{
    for(int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;
}
  
// Driver program to test above functions
int main()
{
    char txt[] = "banana";
    int n = strlen(txt);
    int *suffixArr = buildSuffixArray(txt,  n);
    cout << "Following is suffix array for " << txt << endl;
    printArr(suffixArr, n);
    return 0;
}


```

# Search

```c++
// A suffix array based search function to search a given pattern
// 'pat' in given text 'txt' using suffix array suffArr[]
void search(char *pat, char *txt, int *suffArr, int n)
{
    int m = strlen(pat);  // get length of pattern, needed for strncmp()
  
    // Do simple binary search for the pat in txt using the
    // built suffix array
    int l = 0, r = n-1;  // Initilize left and right indexes
    while (l <= r)
    {
        // See if 'pat' is prefix of middle suffix in suffix array
        int mid = l + (r - l)/2;
        int res = strncmp(pat, txt+suffArr[mid], m);
  
        // If match found at the middle, print it and return
        if (res == 0)
        {
            cout << "Pattern found at index " << suffArr[mid];
            return;
        }
  
        // Move to left half if pattern is alphabtically less than
        // the mid suffix
        if (res < 0) r = mid - 1;
  
        // Otherwise move to right half
        else l = mid + 1;
    }
  
    // We reach here if return statement in loop is not executed
    cout << "Pattern not found";
}
int main()
{
    char txt[] = "banana";  // text
    char pat[] = "nan";   // pattern to be searched in text
  
    // Build suffix array
    int n = strlen(txt);
    int *suffArr = buildSuffixArray(txt, n);
  
    // search pat in txt using the built suffix array
    search(pat, txt, suffArr, n);
  
    return 0;
}
```