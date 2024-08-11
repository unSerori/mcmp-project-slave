# mcmp-project-slave

## 概要

MultiPaperを使って負荷分散マイクラサーバを立てる。  
worldデータの保持とロードバランサーを行うMasterと実際のサーバ処理を行うslaveがある。これはSlave環境構築リポジトリ。  

今回はラズパイに[master](https://github.com/unSerori/mcmp-project-master)と常時起動用のslaveをインストールし、自分が参加する際などwin10PCを起動している間はslaveとして負荷分散に参加し負荷を受け持つ。  

## 環境構築

1. Dockerを入れる
2. mcmp-project-slaveをクローン

    ```bash
    # clone
    cd /home/mcmp
    git clone git@github.com:unSerori/mcmp-project-master.git
    ```

3. リモートvscodeに拡張機能を入れる

    ```bash
    # 拡張機能をインポート
    cat vscode-ext.txt | while read line; do code --install-extension $line; done
    ```

4. .envファイルをコピーまたは作成

    ```env:.env
    MULTIPAPER_SLAVE_URL=multipaper-x.y.z-a.jarのDLリンク
    BASE_IMAGE=jkdのベースイメージ。ここではeclipse-temurin:x.y.z_a-jdkを使用。
    ```

## サーバーアップデート

新しいバージョンがリリースされた場合の更新方法

- .env内のMULTIPAPER_SLAVE_URLを更新
- .env内のBASE_IMAGEを適切なJKDイメージに変更

```bash
# 再ビルド&再起動
docker compose build && docker compose up -d

# (詳細なログはbuildコマンドに以下を追加)
--progress=plain
```

## マイクラ鯖起動

```bash
# SSHで入った後以下実行でコンテナーup
docker compose up -d

# サーバーシャットダウン
```
