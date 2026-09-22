# 57. Searching Algorithms

## Linear search
Works on unsorted data; O(n) worst case and O(1) extra space.
~~~c
int linear_search(const int *a,size_t n,int x){
    for(size_t i=0;i<n;i++) if(a[i]==x) return (int)i;
    return -1;
}
~~~

## Binary search
Requires sorted data. O(log n) worst-case.
~~~c
int binary_search(const int *a,size_t n,int x){
    size_t lo=0,hi=n;
    while(lo<hi){
        size_t mid=lo+(hi-lo)/2;
        if(a[mid]<x) lo=mid+1;
        else hi=mid;
    }
    return (lo<n && a[lo]==x)?(int)lo:-1;
}
~~~

## Other major techniques
Sentinel search reduces a boundary check in some implementations but remains O(n). Interpolation search can approach O(log log n) on suitably distributed sorted numeric data but is O(n) worst case. Jump search is O(sqrt n) on sorted arrays. Exponential search finds a range then applies binary search and is O(log n) after range discovery. Hash-table lookup is expected O(1), but worst-case O(n).

## Practice
Implement first/last occurrence, lower_bound/upper_bound, rotated-array search, and two-sum using hashing.