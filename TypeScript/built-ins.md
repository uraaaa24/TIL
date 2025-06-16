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
	- 配列内で見つかった要素の**インデックス**が必要な場合は、[`findIndex()`](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex) 
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


---
## `.indexOf()`と`.findIndex()`の違い
- **`indexOf`**: “**この値そのもの** がどこにある？”
- **`findIndex`**: “**こういう条件** を満たす要素はどこ？”

```js
// 1. オブジェクト配列で「id:42」を探す
const users = [{id: 10}, {id: 42}, {id: 99}];
const idx = users.findIndex(u => u.id === 42); // 1
// indexOf では “同じ参照のオブジェクト” がない限り見つからない

// 2. 文字列配列で `'apple'` を探す
const fruits = ['banana', 'apple', 'orange'];
fruits.indexOf('apple');      // 1 ← シンプルで速い
fruits.findIndex(f => f==='apple'); // 同じ結果だが冗長

// 3. `NaN` を含む配列
[NaN, 1, 2].indexOf(NaN);             // -1  ← 見つからない
[NaN, 1, 2].findIndex(Number.isNaN);  // 0   ← 発見
```