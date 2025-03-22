# Mathematics

## Scaling a number from a range to another

```typescript
// The range we want our value to be scaled in.
const dstRange = {
  min: 0,
  max: 1,
};

// The range our value stands in.
const srcRange = {
  min: -272,
  max: 1024,
};

let value: number = 451;
```

### Imperative

```typescript
const scale = (
  x: number,
  srcMin: number,
  srcMax: number,
  dstMin: number,
  dstMax: number
) => {
  return ((x - srcMin) * (dstMax - dstMin)) / (srcMax - srcMin) + dstMin;
};

const scaledValue = scale(
  value,
  srcRange.min,
  srcRange.max,
  dstRange.min,
  dstRange.max
);
```

### Functional

```typescript
const scale =
  (dstMin: number, dstMax: number) =>
  (value: number, srcMin: number, srcMax: number) => {
    return ((x - srcMin) * (dstMax - dstMin)) / (srcMax - srcMin) + dstMin;
  };

// A function to scale from 0. to 1.
const scaleToNorm = scale(0, 1);

// Scale it!
const scaledValue = scaleToNorm(value, srcRange.min, srcRange.max);
```
