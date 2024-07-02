## Requirement

* [docker](https://docs.docker.com/install/)
* [docker-compose](https://docs.docker.com/compose/)

## Installation

```bash
$ make create-env
$ make build
$ make up
```

1. 初回 make up で起動した際に各種インストールが行われる
2. 2回目以降の起動時は再度インストール処理を行わないようにしている。
3. プラグインの更新等を行い再度インストール処理を行いたい場合は `make force-up` を実行する

## Usage

http://localhost:8831 in your browser.<br>
http://localhost:8831/wp-admin in your browser.

## Plugin Install

### インストールが必要なプラグインをaws環境でも反映させる場合

`etc/docker/app/plugin/{site_name}`に `wpackagist-plugin/{plugin_name}:*`といった形式で記述する必要がある

例) `wpackagist-plugin/table-of-contents-plus:*`

#### 注意点

1. ローカル上で、appコンテナ起動時にプラグインがインストールされると、 etc/site/{サイト名}/composer.json, composer.lock が更新される
2. 1をgit commit し反映が必要
3. インストール後はWordPressのプラグイン設定から該当のプラグインの「有効化」が必要なので忘れずに行うこと
