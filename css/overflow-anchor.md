- ページをスクロールしている際、ページの上部に読み込みの遅いイメージが表示されたり新たな広告が表示された場合などに、意図しないスクロールが起きてしまうことがある
	- この問題を改善するために Chrome 56 以降などのブラウザでは **スクロールアンカリング** という機能を実装
	- ページ上部(viewport よりも上部)にコンテンツが追加されてもスクロール位置を保持するように改善した
	- この機能が逆に邪魔となるケースでは `overflow-anchor` に `none` を指定することにより無効化することが可能

- [`auto`](https://developer.mozilla.org/ja/docs/Web/CSS/overflow-anchor#auto)（初期値）
	その要素は、スクロール位置を調整するときにアンカー候補になる

- [`none`](https://developer.mozilla.org/ja/docs/Web/CSS/overflow-anchor#none)
	その要素はアンカー候補として選択されない