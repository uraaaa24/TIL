```py
import hashlib

# 分割してハッシュ
m = hashlib.sha256()
m.update(b"Nobody inspects")
m.update(b" the spammish repetition")
m.digest()    # => b'\x03\x1e\xdd...'
m.hexdigest() # => '031edd7d4165...'

# 1 行で済ませるなら
hashlib.sha256(
    b"Nobody inspects the spammish repetition"
).hexdigest()

```

# 暗号化とハッシュ化の違い

|      | 暗号化 (Encryption)   | ハッシュ化 (Hash)                     |
| ---- | ------------------ | -------------------------------- |
| 戻せる? | 復号キーがあれば戻せる        | **不可逆**                          |
| 目的   | 機密性の確保             | 一致確認・改ざん検知                       |
| 出力長  | 入力に比例 (可変)         | アルゴリズム毎に固定 (例: SHA-256 は 256bit) |
| 代表例  | AES, RSA, ChaCha20 | SHA-2, SHA-3, BLAKE3             |

## ハッシュ化
- 同一データから変換されたハッシュ値は、常に同一の値になる
- パスワード一致確認や、データの改ざん検知に使われる
- SHA-2(SHA-256)がよく使われている

## 暗号化
- データを第三者に盗み見られても簡単には読めない状態にしておくこと
- 暗号化にも復号化にも同じキーを使う共通鍵暗号方式や、暗号化と復号化で異なるキーを使う公開鍵暗号方式がある
- 共通鍵暗号方式と公開鍵暗号方式を組み合わせたハイブリッド方式という手法もあり、ウェブページのHTTPS化（SSL/TLS）で用いられてる
