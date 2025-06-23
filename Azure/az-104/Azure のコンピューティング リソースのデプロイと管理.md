- Azure SQL Database
	- オンプレミス環境にホストされているMicrosoft SQLサーバーはAzure SQL Databaseを利用して移行することが可能
	- フル マネージド型のSQL データベースを使用して、高可用性、チューニング、バックアップ、その他のデータベース タスクの設定と管理の複雑さを軽減することが可能
	- アクティブ geo レプリケーションを利用することでプライマリ データベースに対して継続的に同期された読み取り専用のセカンダリデータベースを作成できる

- Azure Automation State Configuration
	- Azureまたはオンプレミス環境の仮想マシンのノード上にPowerShell Desired State Configuration (DSC) 構成を記述、管理、およびコンパイルするための構成管理サービス
	- Azure仮想マシン構成の整合性を管理することができる
	- 以下の手順が必要
		1. DSC構成を作成する
		2. DSC構成をAzure Automation State Configurationにアップロードする 
		3. DSC 構成をノード構成 (MOF ドキュメント) にコンパイルする 
		4. VMにノード構成を適用して、State Configurationを使用した仮想マシンの管理を有効にする
		5. ノードのコンプライアンス対応状態を確認する