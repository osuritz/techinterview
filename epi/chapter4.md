# Primitive Types

## 4.1 Computing the Parity of a Word
```typescript
/**
 * Returns 1 if the number of "1" in the "word" is odd.
 * 
 * E.g. the parity of 1011 (decimal 11) is 1 but the parity of 10001000 (decimal 136) is 0.
 */
function parity(x: number): number {
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

## 4.8 Reverse Digits
```typescript
/**
 * E,g, 42 --> 24, -314 --> -413
 */
function reverseDigits(x: number): number {
  if (!Number.isInteger(x)) {
    throw 'Excepted an integer';
  }

  let n = x;
  let result = 0;
  while (n != 0) {
      result = (result * 10) + n % 10;
      n = Math.trunc(n / 10);  // Note: Math.floor only works as intended on positive integers
  }
  
  return result;
}

console.log(`Reverse of 42: ${reverseDigits(42)}`);
console.log(`Reverse of -314: ${reverseDigits(-314)}`);
```

## 4.9 Check If a Decimal Integer Is a Palindrome
```typescript
function isPalindromeNumber(x: number): boolean {
  if (!Number.isInteger(x)) {
    throw 'Excepted an integer';
  }

  if (x < 0) { return false; }
  if (x === 0) { return true; }

  let n = Math.trunc(Math.log10(x) +1);   // Number of digits in x, neat!
  let orderOfMagnitude = Math.pow(10, n-1);
  for (let i=0; i < Math.floor(n / 2); i++) {

    let rightMostDigit = x % 10;
    let leftMostDigit = Math.floor(x / orderOfMagnitude);
    if (leftMostDigit !== rightMostDigit) {
      return false;
    }

    x = x % orderOfMagnitude; // Remove left-most digit
    x = Math.floor(x / 10); // Remove right-most digit
    orderOfMagnitude = orderOfMagnitude / 100;  // Because we've removed two digits from x
  }

  return true;
}

expect(isPalindromeNumber(0)).toBe(true);
expect(isPalindromeNumber(1)).toBe(true);
expect(isPalindromeNumber(-1)).toBe(false);
expect(isPalindromeNumber(7)).toBe(true);
expect(isPalindromeNumber(11)).toBe(true);
expect(isPalindromeNumber(12)).toBe(false);
expect(isPalindromeNumber(100)).toBe(false);
expect(isPalindromeNumber(121)).toBe(true);
expect(isPalindromeNumber(123321)).toBe(true);
expect(isPalindromeNumber(214748647)).toBe(false);
```
