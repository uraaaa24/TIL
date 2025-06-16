## `.filter()`

## `.find()`

## `.flatMap()`
- `map()` で各要素を変換し、その直後に `flat(1)` で 1 段階だけ配列を平たくする
- 「**何かを変換 → ときどき配列を返す → 1 段 flatten**」という処理に最適
```js
const arr1 = [1, 2, 1];

const result = arr1.flatMap((num) => (num === 2 ? [2, 2] : 1));

console.log(result);
// Expected output: Array [1, 2, 2, 1]
```

## `reduce()`