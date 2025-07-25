Ansible Role: RH_cmd_executor/OS_build
=======================================================
# Description
本ロールは、RHEL9に関する任意の設定コマンド実行、および任意パスにファイルのアップロードを行います。

# Supports
- 管理マシン(Ansibleサーバ)
  * Linux系OS（RHEL8）
  * Ansible バージョン 2.11.0 以上 (動作確認バージョン [core 2.11.12])
  * Python バージョン 3.x  (動作確認バージョン 3.6.8)
- 管理対象マシン
  * RHEL9

# Requirements
- 管理マシン(Ansibleサーバ)
  * Ansibleサーバは管理対象マシンへssh接続できる必要があります。
- 管理対象マシン
  * RHEL9

# Dependencies

本ロールでは、他のロールは必要ありません。

# Role Variables

本ロールで指定できる変数値について説明します。

## Mandatory Variables

ロール利用時に以下の変数値を指定する必要があります。

| Name | Description |
| ---- | ----------- |
| `VAR_RH_cmd_executor` | |
| `- type` | 以下のいずれかのタイプを指定する。<br>command：commandでコマンドを実行。コマンドを安全に使用する場合に最適。<br/>shell：shellでコマンドを実行。シェルを使用し、環境変数、パイプ・リダイレクト等使用可能で高い利便性。<br/>upload：ファイルをアップロードして指定のパスに配置する。 |
| &nbsp;&nbsp;&nbsp;&nbsp;`cmd` | 実行したいコマンドを指定する。<br>typeがcommandとshellの場合に有効。<br>例：export PATH=$PATH:/usr/local/custom/bin |
| &nbsp;&nbsp;&nbsp;&nbsp;`chdir` | 移動先のディレクトリパスを指定する。<br>typeがcommandとshellの場合に有効。<br>指定したディレクトリに移動してからcmdに指定したコマンドが実行される。<br/>例：somedir/ |
| &nbsp;&nbsp;&nbsp;&nbsp;`executable` | コマンドを実行するときに使われるシェルを指定する。<br>typeがshellの場合に有効。<br/>例：/bin/sh |
| &nbsp;&nbsp;&nbsp;&nbsp;`path` | アップロードするファイルの配置先パスを指定する。<br>typeがuploadの場合に有効。<br>例：/etc/foo.conf |
| &nbsp;&nbsp;&nbsp;&nbsp;`file` | アップロードするファイルを登録する。<br>typeがuploadの場合に有効。 |

### Example
~~~
VAR_RH_cmd_executor:
- type: upload
  path: /usr/bin/make_database.sh
  file: make_database.sh
- type: command
  cmd: make_database.sh db_user db_name
  chdir: /usr/bin
~~~

~~~
VAR_RH_cmd_executor:
- type: command
  cmd: touch /tmp/newfile.txt
- type: shell
  cmd: somescript.sh >> somelog.log
- type: shell
  cmd: cat < /tmp/*txt
  executable: /bin/bash
~~~

```
VAR_RH_cmd_executor:
- type: command
  cmd: dnf install -y httpd
```

## Optional Variables

特にありません。

# Usage

1. 本ロールを用いたPlaybookを作成します。
2. 変数を必要に応じて設定します。
3. Playbookを実行します。

# Example Playbook

本ロールを"roles"ディレクトリに配置して、以下のようなPlaybookを作成してください。

- フォルダ構成

~~~
 - playbook/
    │── roles/
    │     └── RH_cmd_executor/
    │          └── OS_build/
    │               │── tasks/
    │               │      build_flat.yml
    │               │      main.yml
    │               └─ README.md
    └─ master_playbook.yml
~~~

- マスターPlaybook サンプル[master_playbook.yml]

~~~
#master_playbook.yml
---
- hosts: all
  gather_facts: true
  roles:
    - role: RH_cmd_executor/OS_build
      VAR_RH_cmd_executor:
      - type: upload
        path: /usr/bin/make_database.sh
        file: make_database.sh
      - type: command
        cmd: make_database.sh db_user db_name
        chdir: /usr/bin
  strategy: free
~~~

- Running Playbook

~~~
> ansible-playbook master_playbook.yml
~~~

# Remarks
-------
特にありません。

# License
-------

# Copyright
---------
Copyright (c) 2025 NEC Corporation

# Author Information
------------------
NEC Corporation
