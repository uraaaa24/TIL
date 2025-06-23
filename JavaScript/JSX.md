# 概要
- **JSX(JavaScript XML):**
	- コンポーネント思考のJavaScriptライブラリやフレームワークで使用されているJavaScriptの拡張構文
	- JavaScriptのコード内にHTMLタグのような構文が埋め込み可能になる

# JSXとECMAScriptの違い
| 項目     | ECMAScript                       | JSX                               |     |
| ------ | -------------------------------- | --------------------------------- | --- |
| 規格     | ECMAScriptで規定                    | JavaScriptの構文を独自に拡張した言語           |     |
| ブラウザ実行 | ブラウザはECMAScriptに準拠するため、そのまま実行できる | ブラウザで直接JSXを解釈・実行できない → トランスパイルが必要 |     |
| 変換ツール  | 不要                               | Babel / SWC / TypeScript (tsc) など |     |

- トランスパイル: JSXをブラウザが認識できるJavaScriptに変換する過程

# JSX構文とHTML構文の違い
