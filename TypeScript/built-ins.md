## `.filter()`
- 指定された配列の中から指定された関数で実装されているテストに合格した要素だけを抽出した[シャローコピー](https://developer.mozilla.org/ja/docs/Glossary/Shallow_copy)を作成（コピーメソッド）
- テストに合格した要素がない場合は、空の配列が返される

```js
const words = ["spray", "elite", "exuberant", "destruction", "present"];

const result = words.filter((word) => word.length > 6);

console.log(result);
// Expected output: Array ["exuberant", "destruction", "present"]
```

## `.find()`
- 提供されたテスト関数を満たす配列内の最初の要素を返す
- テスト関数を満たす値がない場合は、 `undefined` を返す

## `.flatMap()`
- `map()` で各要素を変換し、その直後に `flat(1)` で 1 段階だけ配列を平たくする
- 「**何かを変換 → ときどき配列を返す → 1 段 flatten**」という処理に最適
```js
const arr1 = [1, 2, 1];

const result = arr1.flatMap((num) => (num === 2 ? [2, 2] : 1));

console.log(result);
// Expected output: Array [1, 2, 2, 1]
```

```js
const arr1 = ["it's Sunny in", "", "California"];

arr1.map((x) => x.split(" "));
// [["it's","Sunny","in"],[""],["California"]]

arr1.flatMap((x) => x.split(" "));
// ["it's","Sunny","in", "", "California"]
```

## `reduce()`