# Bitwise flags (ビットフラグ)
- 一つの整数の"各ビット"を**ON / OFFスイッチ**とみなし、複数の真偽値（フラグ）を一まとめにして扱う方法
- 例：`GPUBufferUsage.COPY_SRC`(0x0004) と `MAP_WRITE`(0x0002) を  `usage = 0x0004 \| 0x0002` のように OR で合成し、  `if (usage & GPUBufferUsage.MAP_WRITE) { … }` で AND 判定する

# 仕組み
- 2 の累乗で「かぶらない」値を割り振る

```txt
10進  16進   2進 (下位 6bit 抜粋)
1     0x01   000001   // FLAG_A
2     0x02   000010   // FLAG_B
4     0x04   000100   // FLAG_C
8     0x08   001000   // 以降も 16, 32, 64...
```

- 各ビットは **互いに重ならない** ので、OR(`|`) で合成しても値がユニーク
- AND(`&`) で特定のビットが立っているか高速に判定できる

# 典型的な操作方法

```ts
// 1. 定義
const enum FileAccess {
  Read    = 1 << 0,  // 1
  Write   = 1 << 1,  // 2
  Execute = 1 << 2,  // 4
}

// 2. 合成
const perms = FileAccess.Read | FileAccess.Execute; // => 0b101 (5)

// 3. 判定
const canWrite = Boolean(perms & FileAccess.Write); // false

// 4. 追加/削除/反転
let flags = 0;
flags |= FileAccess.Write;        // 追加 (set)
flags &= ~FileAccess.Write;       // 削除 (clear)
flags ^= FileAccess.Execute;      // 反転 (toggle)

```

# 参考リンク
- https://developer.mozilla.org/ja/docs/Glossary/Bitwise_flags
