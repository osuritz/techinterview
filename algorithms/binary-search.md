# Algorithms >  Binary Search
A binary search **requires that the input be sorted**. The technique is very simple: we basically keep splitting the input in half and determine
if the value we're looking for is in the lower (left) or higher (right) half than the midway point.
Keep going until we've either found the item or run out of items to look at (in which case we return `-1`).

**Time complexity: O(log n).**
Log n basically happens when you can write off/drop/ignore half of your remaining possibilities at every iteration. So if your interviewer hints that the
fastest solution to a problem is O(log n), there's a good chance you can leverage some sort of binary search.

## When to Use
* When an array is sorted and we are looking for a specific element
  - Note there's a interview question that uses a variation of this where the sorted array is "rotated" or "shifted". In that case we need to first
  determine where the pivot point is. The unique property of that pivot is that it's the only element that is **less then** the element righ before it (`i-1`).


## Example
Example C# implementation
```csharp
public static int BinarySearch<T>(T[] array, T searchFor, Comparer<T> comparer)
{
  int high, low, mid;
  high = array.Length - 1;
  low = 0;
  if (array[0].Equals(searchFor))
    return 0;
  else if (array[high].Equals(searchFor))
    return high;
  else
  {
    while (low <= high)
    {
      mid = (high - low) / 2 + low;
      if (comparer.Compare(array[mid], searchFor) == 0)
        return mid;
      else if (comparer.Compare(array[mid], searchFor) > 0)
       high = mid - 1;
      else
        low = mid + 1;
    }
    return -1;
  }
}
```
