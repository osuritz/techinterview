# Primitive Types

## Computing the Parity of a Word
```typescript
/**
 * Returns 1 if the number of "1" in the "word" is odd.
 * 
 * E.g. the parity of 1011 (decimal 11) is 1 but the parity of 10001000 (decimal 136) is 0.
 */
function parity(x: number) {
  if (!Number.isInteger(x)) {
    throw 'Excepted an integer';
  }

  let result = 0;
  while (x != 0) {
    result ^= x & 1;
    x = x >>> 1;
  }

  return result;
}

console.log(`Parity of 3 (0x11): ${parity(11)}`);
console.log(`Parity of 136 (0x10001000): ${parity(136)}`);
```
