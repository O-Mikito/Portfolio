# ポートフォリオ 
## 1. 株価データの配信基盤
### ◆プロジェクトの概要
  〈プロジェクトの内容〉  
    本プロジェクトは仮想の顧客である証券会社に対して日々の株価をデータを配信する基盤を構築するものです。  
    以下の3つのフェーズに分かれています。  
  
  1. サーバー、クライアントの基本的な環境構築
  2. エラー監視・チェック機能の実装
  3. FTP→SFPTへの仕様変更対応  
  
  〈プロジェクトの工程〉   
1. サーバー、クライアントの基本的な環境構築
- 開発開始 2024/10/28
- 環境構築~ 2024/11/5
- 設計~ 2024/11/19
- 開発~ 2025/12/2
- テスト~ 2025/12/19
    
2. エラー監視・チェック機能の実装
- 開発開始 2024/12/20
- 開発~ 2025/1/6
- テスト~ 3. FTP→SFPTへの仕様変更対応と併せて実施

3. FTP→SFPTへの仕様変更対応
- 開発開始 2024/1/7
- 開発~ 2025/1/16
- テスト~ 2025/1/24  
### ◆開発環境  
本プロジェクトは、ローカルのDockerコンテナ内にセットアップしたUbuntu Linux環境で開発を行いました。  

  使用技術・言語（フレームワーク・ライブラリ）  
- Python (pandas, Numpy, subprocess, csv, os, mysql.connector)
- Shellscript
- (S)FTP
- SSH
### ◆システム構成図
![システム構成図](https://github.com/user-attachments/assets/f4a40a97-f23d-46ff-8888-19bc110135da)
### ◆シーケンス図  
シーケンス図  
![シーケンス図](https://github.com/user-attachments/assets/bc649177-4db0-45b3-b0fd-4c83d7d0c6d2)  

### ◆ドキュメント  
[データ仕様書.pdf](https://github.com/user-attachments/files/18597028/default.pdf)

[接続仕様書.pdf](https://github.com/user-attachments/files/18597031/default.pdf)

[バッチ一覧.pdf](https://github.com/user-attachments/files/18597034/default.pdf)
 
[テスト仕様書.pdf](https://github.com/user-attachments/files/18597035/default.pdf)

### ◆機能  
※以下はすべてバッチによる自動実行です。  
クライアント側  
- データファイル作成
- フォーマットチェック
- データファイル転送

サーバー側  
- データファイル突合と差分データ出力
- アーカイブファイル作成
- アーカイブファイル削除

### ◆デモ  
ファイル作成からフォーマットチェック、転送、突合、アーカイブ作成・削除の一連の流れを説明します。  
(デモは手動実行時のもの)  

〈ファイル作成〉  
clientコンテナ内で以下のコマンドを実行します。  
`python3 /usr/local/sbin/stock_csv_create.py`  

[実行結果]  
![ファイル作成コマンド実行結果](https://github.com/user-attachments/assets/d6986601-3579-42d3-ba38-f53c1c03a722)  


〈フォーマットチェック〉
clientコンテナ内で以下のコマンドを実行します。  
`python3 /usr/local/sbin/csv_check.py`  

[実行結果]
![フォーマットチェックコマンド実行結果](https://github.com/user-attachments/assets/be8991ec-01e4-4ea1-837b-fe5de9a01b9a)  


〈ファイル転送〉  
serverコンテナ内で以下のコマンドを実行し、パーミッションを変更します。  
※SFTPを使用するため、このときclient側でキーペアを生成し、サーバーに公開鍵を配置する工程がありますが割愛させていただきます。
`chmod 775 /`  
次にclientコンテナ内で以下のコマンドを実行します。  
`/usr/local/sbin/transfer.sh`

[実行結果]  
1. transfer.shを実行
![transfer.sh実行](https://github.com/user-attachments/assets/8007d193-eeea-47bb-bf69-4b2a68845afe)  
2. serverコンテナにファイルが転送されていることを確認  
![サーバーにファイルが転送されている](https://github.com/user-attachments/assets/893ab6d2-a802-4c0e-9c18-5f44fd257f8b)


〈データ突合〉  
serverコンテナ内で以下のコマンドを実行します。  
`python3 /usr/local/sbin/matching.py`  

[実行結果]  
差分ログファイルを確認する（差分がなかったため、銘柄コードの記載なし）
![差分チェック](https://github.com/user-attachments/assets/f3745e57-3782-440b-a2bf-bee3ecd1cfd7)  


〈アーカイブファイル作成〉  
serverコンテナ内で以下のコマンドを実行します。  
`/usr/local/sbin/archive.sh`  

[実行結果]  
![アーカイブファイル作成](https://github.com/user-attachments/assets/618f4b77-36b1-4780-80ea-abaee4a4d2af)  


〈アーカイブファイル削除〉  
serverコンテナ内で以下のコマンドを実行します。  
`/usr/local/sbin/delete.sh`  

[実行結果]  
![アーカイブファイル削除](https://github.com/user-attachments/assets/5846743c-f637-465a-b0ab-7ea02d8d52a6)  












　　
