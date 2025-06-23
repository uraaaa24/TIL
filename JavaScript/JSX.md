# 概要
- **JSX(JavaScript XML):**
	- コンポーネント思考のJavaScriptライブラリやフレームワークで使用されているJavaScriptの拡張構文
	- JavaScriptのコード内にHTMLタグのような構文が埋め込み可能になる

# JSXとECMAScriptの違い
| 項目     | EcmaScript    | JSX                     |
| ------ | ------------- | ----------------------- |
| 規格     | EcmaScriptで規定 | JavaScriptの構文を独自に拡張した言語 |
| ブラウザ実行 | そのまま実行できる     |                         |
| 変換ツール  |               |                         |


- **JavaScript:** EcmaScriptという言語仕様で規定されている
- **JSX:** JavaScriptの構文を独自に拡張した言語（JavaScriptの言語仕様にはない）
- ブラウザがJavaScriptエンジンを実装する場合、ECMAScript(標準)に準拠する
	- ブラウザで直接JSXを解釈し、実行することができない現状がある
	- この問題を解決するために、トランスパイルという過程が必要となる
	- トランスパイル作業を助けるツールとして、BabelやTypeScriptコンパイラーが使われる
- トランスパイル: JSXをブラウザが認識できるJavaScriptに変換する過程

# JSX構文とHTML構文の違い
