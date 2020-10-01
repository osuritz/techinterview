# Arrays

## 5.2 Increment an Arbitrary-Precision Integer
```typescript
function incrementAribitraryNumber(A: number[]): number[] {
  let carry = true;
  for (let i= A.length-1; i >= 0 && carry; i--) {
    if (A[i] === 9) {
      A[i] = 0;
      carry = true;
      continue;
    }

    A[i] = A[i] + 1;
    carry = false;
  }

  // All digits were set to '0' but need to carry the one to a new digit.
  // This can be done by just appending one more '0' at the end of the array (so need to move all elts)
  // and then setting the first digit to a '1'.
  if (carry) {
    A.push(0);
    A[0] = 1;
  }

  return A;
}

expect(incrementAribitraryNumber([1,2,9])).toEqual([1,3,0]);
expect(incrementAribitraryNumber([9,9,9])).toEqual([1,0,0,0]);
```