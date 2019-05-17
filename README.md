# Dockerに関するリポジトリ

## ディレクトリ構成

```
.
├── Dockerfile
├── README.md
└── docker-compose.yml
```

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
