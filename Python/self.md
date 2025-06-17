# selfとは？
- インスタンス（= 具体的に生成されたオブジェクト）そのものを表す引数
- インスタンスメソッドの **第 1 引数**（慣例で `self` と書いているが、`foo` と書いても動く）

```python
class Person:
    def __init__(self, name):
        self.name = name      # ← self は生成中のインスタンス自身
    def greet(self):
        return f"こんにちは、{self.name}"

taro = Person("太郎")
print(taro.greet())   # Person.greet(taro) と等価
```

# `self.stocker`
- **辞書アクセスの糖衣**: 実体は `self.__dict__['stocker']` を `.` 記法で参照しているだけ
- **誕生は代入時**: `self.stocker = ...` と書いた瞬間に属性が動的に追加される（事前宣言は不要）
- **シャドーイング**: 同名のクラス属性があっても、インスタンスで再代入するとインスタンス側が優先される

```python
class Warehouse:
    def __init__(self, initial=None):
        self.stocker = initial or []   # ← 属性の誕生

    def add(self, item):
        self.stocker.append(item)      # ← self.__dict__['stocker'] にアクセス
```

## シャドーイングとは？
- **内側の名前空間が外側と同名シンボルを持つと、内側が優先され外側が見えなくなる** 現象
- クラス vs インスタンスのほか、関数スコープなどでも同じ規則が働く

```python
x = 10

def show():
    x = 20          # 関数スコープで x を再定義 → グローバル x を隠す
    print(x)        # 20

show()
print(x)            # 10
```