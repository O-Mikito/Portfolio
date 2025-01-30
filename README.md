# ポートフォリオ 
## 1. 株価データの配信基盤
### ◆プロジェクトの概要
  プロジェクトの内容  
  本プロジェクトは顧客である証券会社に対して日々の株価をデータを配信する基盤を構築するというものです。  
  本プロジェクトでは以下のの3つのフェーズに分かれています。  
  1. ファイル転送機能の実装
  2. エラー監視・チェック機能の実装
  3. セキュリティ機能の実装  
  
  プロジェクトの工程  
  1. ファイル転送機能の実装
  - 開発開始 2024/10/28
  - 環境構築~ 2024/11/5
  - 設計~ 2024/11/19
  - 開発~ 2025/12/2
  - テスト~ 2025/12/19
    
2. エラー監視・チェック機能の実装
  - 開発開始 2024/12/20
  - 開発~ 2025/1/6
  - テスト~ 3. セキュリティ機能の実装と併せて実施  

3. セキュリティ機能の実装
  - 開発開始 2024/1/7
  - 開発~ 2025/1/16
  - テスト~ 2025/1/24
### ◆開発環境  
本プロジェクトは、ローカルのDockerコンテナ内にセットアップしたUbuntu Linux環境で開発を行いました。  

  使用言語（フレームワーク・ライブラリ）  
- Python (pandas, Numpy, subprocess, csv, os, mysql.connector)
- Shellscript
### ◆システム構成図
![システム構成図](https://github.com/user-attachments/assets/f4a40a97-f23d-46ff-8888-19bc110135da)
### ◆シーケンス図  
シーケンス図  
![シーケンス図](https://github.com/user-attachments/assets/bc649177-4db0-45b3-b0fd-4c83d7d0c6d2)  

### ◆ドキュメント  
データ仕様書  
[データ仕様書.pdf](https://github.com/user-attachments/files/18596942/データ仕様書.pdf)

接続仕様書  
[接続仕様書.pdf](https://github.com/user-attachments/files/18596925/接続仕様書.pdf)  

バッチ一覧  
[バッチ一覧.pdf](https://github.com/user-attachments/files/18596955/バッチ一覧.pdf)

テスト仕様書  
[テスト仕様書.pdf](https://github.com/user-attachments/files/18596930/テスト仕様書.pdf)

### ◆機能
クライアント側  

サーバー側


