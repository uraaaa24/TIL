# `@classmethod` と `@staticmethod`
## `@classmethod`
- デコレータ `@classmethod` でラップされた関数は **クラスを暗黙の第 1 引数** `cls` **として受け取る**
- クラスオブジェクト `MyClass.m()` からもインスタンス `MyClass().m()` からも呼び出せる（どちらでも _クラス_ が渡る）
- **サブクラス** から呼び出すと `cls` には _そのサブクラス自身_ が渡る。  
    たとえば `PremiumUser.from_email()` の内部で `return cls(name)` と書いておけば、`cls` は `PremiumUser` なので **PremiumUser 型のインスタンス** が生成される――これが “多態性を維持できる” という意味。
- 典型的な用途
    - 代替コンストラクタ (`from_dict`, `from_env`, `from_json` …)
    - クラス全体に関わる設定値の読み書き (`set_config`, `with_options` …)
    - サブクラスごとに異なるインスタンスを生成するファクトリ

```python
class User:
    default_role = "guest"

    def __init__(self, name, role=None):
        self.name = name
        self.role = role or self.default_role

    @classmethod
    def from_email(cls, email: str) -> "User":
        name = email.split("@")[0]
        return cls(name)   # cls は呼び出し元クラスになる

# --- サブクラスで呼び出す例 ---------------------------
class PremiumUser(User):
    default_role = "premium"

bob = PremiumUser.from_email("bob@vip.com")
print(type(bob), bob.role)  # <class '__main__.PremiumUser'> premium
```

## `@staticmethod`
- `@staticmethod` でラップされた関数は **暗黙の引数を一切受け取らない**
- クラス／インスタンスの両方から同じように呼び出せるが、`self` や `cls` にアクセスしない
- クラスやインスタンスの状態に依存しないユーティリティ関数を **名前空間としてクラスにまとめたいとき** に便利
- 他言語の “static メソッド” にほぼ相当（Python の `@classmethod` とは別物なので注意）

```python
class Math:
    @staticmethod
    def is_prime(n: int) -> bool:
        if n < 2:
            return False
        for p in range(2, int(n**0.5) + 1):
            if n % p == 0:
                return False
        return True
```