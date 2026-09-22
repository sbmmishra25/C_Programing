# 58. Sorting Algorithms

## Comparison overview
Bubble: O(n²), stable, in-place.
Selection: O(n²), generally not stable, in-place.
Insertion: O(n²) worst, O(n) best on nearly sorted data, stable.
Merge: O(n log n), stable, O(n) auxiliary array.
Quick: O(n log n) average, O(n²) worst with poor pivots, typically in-place apart from recursion stack.
Heap: O(n log n), in-place, not stable.
Shell: gap-based; performance depends on sequence.
Counting: O(n+k) for bounded integer keys, not comparison-based.
Radix: O(d(n+k)) for suitable fixed-digit keys.
Bucket: expected near O(n+k) under distribution assumptions.

## Complete insertion sort
~~~c
void insertion_sort(int *a,size_t n){
    for(size_t i=1;i<n;i++){
        int key=a[i];
        size_t j=i;
        while(j>0 && a[j-1]>key){a[j]=a[j-1];--j;}
        a[j]=key;
    }
}
~~~

## Merge-sort skeleton
~~~c
/* recursively split, sort halves, then merge into temporary storage */
~~~

## Quick-sort caution
A comparator for qsort should not return a-b because integer subtraction can overflow. Use:
~~~c
int cmp_int(const void *pa,const void *pb){
    int a=*(const int*)pa,b=*(const int*)pb;
    return (a>b)-(a<b);
}
~~~

## Choosing an algorithm
Consider stability, memory, data distribution, key range, worst-case guarantees, and whether input is already nearly sorted.

## Practice
Implement all comparison sorts above, then benchmark them on random, sorted, reverse-sorted, and duplicate-heavy arrays.