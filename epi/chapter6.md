# Strings

## 6.5 Test Palindromicity
```typescript
/** Basic, naive isPalindrome function: puncation would throw a wrench in it. */
function isPalindrome(s: String): boolean {
  for (let i=0, j=s.length-1; i <= j; i++, j--) {
    if (s[i] !== s[j]) {
      return false;
    }
  }

  return true;
}

expect(isPalindrome('racecar')).toBe(true);
expect(isPalindrome('brewery')).toBe(false);
expect(isPalindrome('reviver')).toBe(true);
expect(isPalindrome('A man, a plan, a canal – Panama')).toBe(false);
```

```typescript
/**
 * This function will ignore whitespace, puncation, and case differences so that known palindromes
 * such as "A man, a plan, a canal – Panama" succeed.
 */
function isPalindromePunctuation(s: String): boolean {
  const alphanumeric = /^\w$/i;
  let i = 0;
  let j = s.length -1;
  while (i <= j) {
    while (!s[i].match(alphanumeric)) { i++; }
    while (!s[j].match(alphanumeric)) { j--; }

    if (s[i++].toLocaleLowerCase() !== s[j--].toLocaleLowerCase()) {
      return false;
    }
  }

  return true;
}

expect(isPalindromePunctuation('Deer Madam, Reed')).toBe(true);
expect(isPalindromePunctuation('Napalm')).toBe(false);
expect(isPalindromePunctuation('A man, a plan, a canal – Panama')).toBe(true);
```

## 6.6 Reverse All the Words in a Sentence
```typescript
// Alice likes Bob --> Bob likes Alice
// ram is costly --> costly is ram
function reverseWords(input: string[]) {
  const n = input.length;

  // Start by reversing the entire array. That gives us the right order of "words" but
  // with the letters of ever word reversed.
  // E.g. "Alice likes Bob" --> "boB sekil ecilA"
  reverse(input, 0, input.length -1);

  // Go through each word and reverse the letters once more to get them in the correct order.
  // E.g. "boB sekil ecilA" --> "Bob likes Alice"
  let start = 0;
  let end = 0;
  while (start < n) {
    while ( start < n && input[start] === ' ') { start++; }
    end = start;
    while (end < n && input[end] !== ' ') { end++; }
    reverse(input, start, end-1);
    start = end;
  }
}

function reverse(input: string[], start: number, end: number) {
  while (start < end) {
    const temp = input[start];
    input[start++] = input[end];
    input[end--] = temp;
  }
}

// Just used for demo/testing.
function reverseWordsInString(s: string): string {
  const A = [...s];
  reverseWords(A);
  return A.join('');
}

expect(reverseWordsInString('Alice likes Bob')).toEqual('Bob likes Alice');
expect(reverseWordsInString('ram is costly')).toEqual('costly is ram');
```
