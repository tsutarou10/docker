## イメージのダウンロード

```
docker image pull [オプション] イメージ名[:タグ名]
```

- CentOSのイメージ取得
```
$ docker image pull centos:7
```

- URLを指定して取得 (TensorFlowのURLを指定してイメージ取得)
    - プロトコルは省略
```
dokcer image pull gcr.io/tensorflow/tensorflow
```

## イメージの一覧表示

```
docker image ls [オプション] [リポジトリ名]
```

```
$ docker image ls
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
ubuntu              16.04               9361ce633ff1        2 months ago        118MB
ubuntu              latest              94e814e2efa8        2 months ago        88.9MB
```

| オプション | 説明 |
| ---- | ---- |
| --all, -a | 全てのイメージ |
| --digests | ダイジェストを表示するかどうか |
| --no-trunc | 結果を全て表示する |
| --quiet, -q | Dockerイメージ名のみ |

## イメージのタグ設定

```
<Docker Hubのユーザ名>/イメージ名:[タグ名]
```

```
$ docker image ls
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
ubuntu              16.04               9361ce633ff1        2 months ago        118MB

$ docker image tag ubuntu tsutarou10/ubuntu:16.04
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
ubuntu              16.04               9361ce633ff1        2 months ago        118MB
tsutarou10/ubuntu   16.04               9361ce633ff1        2 months ago        118MB
```

## イメージの検索
Docker Hubに公開されているイメージを検索する

```
docker search [オプション] 検索キーワード
```

| オプション | 説明 |
| ---- | ---- |
| --no-trunc | 結果を全て表示 |
| --limit | n件の検索結果を表示 |
| --filter=stars=n | お気に入りの数 (n以上)の指定 |

```
$ docker search nginx --limit 3
NAME                                     DESCRIPTION                                     STARS               OFFICIAL            AUTOMATED
nginx                                    Official build of Nginx.                        11425               [OK]
jwilder/nginx-proxy                      Automated Nginx reverse proxy for docker con…   1599                                    [OK]
jrcs/letsencrypt-nginx-proxy-companion   LetsEncrypt container to use with nginx as p…   509                                     [OK]

$ docker search nginx --filter=stars=10000
NAME                DESCRIPTION                STARS               OFFICIAL            AUTOMATED
nginx               Official build of Nginx.   11425               [OK]

```

## イメージの削除

```
docker image rm [オプション] イメージ名 [イメージ名]
```

| オプション | 説明 |
| ---- | ---- |
| --force, -f | イメージを強制的に削除 |
| --no-prun | 中間イメージを削除しない |

未使用のDockerイメージを削除するときは、docker image pruneコマンドを使う

```
docker image prune [オプション]
```

| オプション | 説明 |
| ---- | ---- |
| --all, -a | 使用していないイメージを削除 |
| --force, -f | 強制的に削除 |


