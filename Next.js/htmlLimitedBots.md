- Next.jsには、動的なメタタグを埋め込むための `generateMetadata`というAPIがある
	- Next.js 15.2以前では、このAPIを利用した際、これまでは非同期なページ遷移をした場合に、`<head>`に入るメタデー画が揃うまでHTML全体の配信がブロックされ、初期表示が遅延していた
	- v15.2のアップデートによって、ストリーミングが使われるようになり、パフォーマンスが改善された

- この挙動はボットごとに変えることが可能
	- ボットごとに細かく制御したい場合、`next.config.js`の`htmlLimitedBots`オプションで正規表現を上書きしてカスタマイズ可能

- ボット
	- Next.js のドキュメントやブログが言う **ボット（bot）** とは、  **検索エンジンや SNS が自動でページを取得する ― 人間のブラウザではなく “クローラ／プレビュー生成ツール” の総称** 

https://nextjs.org/docs/app/api-reference/config/next-config-js/htmlLimitedBots
https://github.com/vercel/next.js/issues/79135