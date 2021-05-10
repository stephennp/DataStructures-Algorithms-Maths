# Intro:

- Bucket sort is a comparison sort algorithm that operates on elements by dividing them into different buckets and then sorting these buckets individually. Each bucket is sorted individually using a separate sorting algorithm or by applying the bucket sort algorithm recursively. Bucket sort is mainly useful when the input is uniformly distributed over a range.

- Assume one has the following problem in front of them:

- One has been given a large array of floating point integers lying uniformly between the lower and upper bound. This array now needs to be sorted. A simple way to solve this problem would be to use another sorting algorithm such as Merge sort, Heap Sort or Quick Sort. However, these algorithms guarantee a best case time complexity of . However, using bucket sort, the above task can be completed in time. Let's have a closer look at it.

- Consider one needs to create an array of lists, i.e of buckets. Elements now need to be inserted into these buckets on the basis of their properties. Each of these buckets can then be sorted individually using Insertion Sort. Consider the pseudo code to do so:

```csharp
void bucketSort(float[] a,int n)
{
    for(each floating integer 'x' in n)
    {
        insert x into bucket[n*x];
    }
    for(each bucket)
    {
        sort(bucket);
    }
}
```

# Time Complexity:

- If one assumes that insertion in a bucket takes time, then steps 1 and 2 of the above algorithm clearly take time.
