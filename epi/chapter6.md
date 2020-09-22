# 6.5 Test Palindromicity
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

console.log(isPalindrome('racecar')); // true
console.log(isPalindrome('brewery')); // false
console.log(isPalindrome('reviver')); // true
console.log(isPalindromePunctuation('A man, a plan, a canal – Panama')); // false
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

console.log(isPalindromePunctuation('Deer Madam, Reed')); // true
console.log(isPalindromePunctuation('Napalm')); // false
console.log(isPalindromePunctuation('A man, a plan, a canal – Panama')); // true
```
