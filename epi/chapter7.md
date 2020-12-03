# Linked Lists

## 7.4 Test for Overlapping Lists (Cycle-free Lists)
```typescript
function overlappingNoCycleLists<T>(l0: ListNode<T>, l1: ListNode<T>): ListNode<T>|null {
  let l0Length = listLength(l0);
  let l1Length = listLength(l1);

  if (l0Length > l1Length) {
    l0 = advanceListByK(l0, l0Length - l1Length);
  } else {
    l1 = advanceListByK(l1, l1Length - l0Length);
  }

  let l0Internal: ListNode<T>|null = l0;
  let l1Internal: ListNode<T>|null = l1;
  while (l0 !== null && l1 !== null && l0 !== l1) {
    l0Internal = l0.next;
    l1Internal = l1.next;
  }

  return l0;
}
```

## Utilities Used
```typescript
class ListNode<T> {
  value: T;
  next: ListNode<T>|null = null;

  constructor(value: T, next: ListNode<T>|null = null) {
    this.value = value;
  }
}

function listLength<T>(l: ListNode<T>): number {
  let count = 1;
  let current = l;
  while (current.next != null) {
    ++count;
  }

  return count;
}

function advanceListByK<T>(l: ListNode<T>, itemsToSkip: number): ListNode<T> {
  let newHead = l;
  for (let i=1; i <= itemsToSkip; ++i) {
    if (newHead.next == null) {
      throw new RangeError('Index of out range: ' + itemsToSkip);
    }
    newHead = newHead.next;
  }

  return newHead;
}
```
