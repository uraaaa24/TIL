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
- `.find()`を使わない方が良い場合
	- 配列内で見つかった要素の**インデックス**が必要な場合は、[`findIndex()`](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex) を使用する
	- **値のインデックス**を検索する必要がある場合は、[`indexOf()`](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf) を使用する([`findIndex()`](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex) と似ていますが、それぞれの要素の等価性はテスト関数ではなく値でチェックします)
	- 配列内に値が**存在する**かどうかを調べる必要がある場合は、 [`includes()`](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/includes) 
	- 指定したテスト関数を満たす要素があるかどうかを調べる必要がある場合は、 [`some()`](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/some)

```js
const array1 = [5, 12, 8, 130, 44];

const found = array1.find((element) => element > 10);

console.log(found);
// Expected output: 12
```

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