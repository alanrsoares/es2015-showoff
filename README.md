# ES2015 Showoff

A series of es2015+ examples on IMMUTABLE data manipulation

### Arrays

### Concatenate Arrays

```javascript
const concat = (...xss) => xss.reduce((xs, ys) => [...xs, ...ys], [])
```
```javascript
concat([1, 2, 3], [4, 5, 6], [7, 8], [9]) //=> [1, 2, 4, 5, 6, 7, 8, 9]
```

### [IMMUTABLE] Splice

```javascript
const splice = (xs, start, count, ...adds) =>
  [...xs.slice(start, count), ...adds, ...xs.slice(start + count)]
```
```javascript
const fishes = ['angel', 'clown', 'mandarin', 'surgeon']
splice(fishes, 2, 0, 'drum', 'bass') //=> ['angel', 'clown', 'drum', 'bass', 'mandarin', 'surgeon']
fishes //=> ['angel', 'clown', 'mandarin', 'surgeon']
```

### Unique values in an array

```javascript
const unique = xs => [...new Set(xs)]
```
```javascript
unique([1, 2, 2, 5, 1, 2, 4, 32]) //=> [1, 2, 5, 4, 32]
```

### Take prop from a list of objects

```javascript
const pluck = key => xs => xs.map(x => x[key])
```
```javascript
const takeIds = pluck('id')
const takeIds2 = xs => xs.map(({ id }) => id) // non-generic, using object destructuring
takeIds([{ id: 12 }, { id: 2 }, { id: 42 }]) //=> [12, 2, 42]
```

### N-Length 'blank' array

```javascript
const array = n => [...Array(Math.max(0, n))]
```
```javascript
array(3) //=> [undefined, undefined, undefined]
```

### Numeric a-to-b range array

```javascript
const range = (a = 0, b = 0) =>
  (j => array(Math.abs(a - b)).map(((x, i) => j + i)))(Math.min(a, b))
```
```javascript
range(3) //=> [0, 1, 2]
range(2, 6) //=> [2, 3, 4, 5]
```

### [IMMUTABLE] Sort of a numeric array

```javascript
const sort = xs => [...xs].sort((a, b) => a - b)
```
```javascript
const a = [3, 1, 2]
sort(a) //=> [1, 2, 3]
a //=> [3, 1, 2]
```

### Sum of a numeric array

```javascript
const sum = xs => xs.reduce((a, b) => a + b, 0)
```
```javascript
sum([1, 2, 3]) //=> 6
```

### Average/Mean of a numeric array

```javascript
const avg = xs => sum(xs) / xs.length
```
```javascript
avg([1, 2, 3]) //=> 2
```

### Median of a numeric array

```javascript
const median = xs =>
  (l => xs.length % 2
    ? sort(xs)[Math.floor(l)]
    : sum(sort(xs).slice(l - 1, l + 1)) / 2)(xs.length / 2)
```
```javascript
median([1, 2, 3]) //=> 2
median([1, 2, 3, 4, 5, 6]) //=> 3.5
```
