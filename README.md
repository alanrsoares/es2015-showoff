# ES2015 Showoff

A series of es2015+ examples on IMMUTABLE data manipulation

### Arrays

### Unique values in an array

```javascript
const unique = xs => [...new Set(xs)]
```

### [IMMUTABLE] Sort of a numeric array

```javascript
const sort = xs => xs.slice.sort()
```

### Sum of a numeric array

```javascript
const sum = xs => xs.reduce((a, b) => a + b, 0)
```

### Average/Mean of a numeric array

```javascript
const avg = xs => sum(xs) / xs.length
```

### Median of a numeric array

```javascript
const median = xs =>
  xs.length % 2
    ? sort(xs)[Math.floor(xs.length / 2)]
    : sum(sort(xs).slice((xs.length / 2) - 1, (xs.length / 2) + 1)) / 2
```
