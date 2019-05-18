## Dockerコンテナの生成

- イメージからコンテナを作成
    - イメージの実体：Dockerでサーバ昨日を動かすために必要なディレクトリ/ファイル群 (Linuxの動作に必要なetcや/binなdのディレクトリ/ファイル群

- ``docker container create``はコンテナを作成するだけで、起動はしない

## コンテナの生成、起動

``docker container run [オプション] イメージ名[:タグ名] [引数]``

| オプション | 説明 |
| ---- | ---- |
| --attach, -a | 標準入力/出力/エラー出力にアタッチ |
| --cidfile | コンテナIDをファイルに出力 |
| --detach, -d | コンテナを生成し、バックグラウンドで実行 |
| --interactive, -i | コンテナの標準入力を開く |
| --tty, -t | 端末デバイスを使う |

```bash
$ docker container run -it --name hoge1 centos /bin/cal
      May 2019
Su Mo Tu We Th Fr Sa
          1  2  3  4
 5  6  7  8  9 10 11
12 13 14 15 16 17 18
19 20 21 22 23 24 25
26 27 28 29 30 31
```

- イメージから、コンテナを生成し、コンテナ上で任意のプロセスを起動できる

### コンテナのバックグラウンド実行
```bash
docker container run [実行オプション] イメージ名[:タグ名] [引数]
```

| オプション | 説明 |
| ---- | ---- |
| --detach, -d | バックグラウンドで実行 |
| --user, -u | ユーザ名を指定 |
| --rm | コマンド実行完了後にコンテナを自動で削除 |

```bash
$ docker container run -d centos /bin/ping localhost
```


## コンテナ起動

`` docker container start``
- 停止中のコンテナを起動

## コンテナを停止

``docker container stop``
- 起動しているコンテナを停止 (削除するときに必要)
- 再起動するときは、``docker container restart``

## コンテナ削除

``docker container rm``
- コンテナを削除

## コンテナのネットワーク設定
```bash
docker container run [ネットワークオプション] イメージ名[:タグ名] [引数]
```

- コンテナのポート番号とホストOSのポート番号をマッピングする
- nginxという名前のイメージをもとにして、コンテナを生成し、バックグラウンドで実行
- ホストのポート番号8080とコンテナのポート番号80をマッピング
- ホストの8080ポートにアクセスすると、コンンテナ上で動作しているNginxにアクセスできる
```bash
$ docker container run -d -p 8080:80 nginx
```

## コンテナを生成/起動する環境を指定

```bash
$ docker container run -it -w=/tensorflow centos /bin/bash
```

## 稼働コンテナの一覧

```bash
$ docker container ls [オプション]
```
