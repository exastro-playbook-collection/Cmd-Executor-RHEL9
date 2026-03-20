Cmd-Executor-RHEL9
===============================
# Trademarks
-----------
* Linuxは、Linus Torvalds氏の米国およびその他の国における登録商標または商標です。
* RedHat、RHEL、CentOSは、Red Hat, Inc.の米国およびその他の国における登録商標または商標です。
* Windows、PowerShell、IIS、.NET Frameworkは、Microsoft Corporation の米国およびその他の国における登録商標または商標です。
* Ansibleは、Red Hat, Inc.の米国およびその他の国における登録商標または商標です。
* pythonは、Python Software Foundationの登録商標または商標です。
* NECは、日本電気株式会社の登録商標または商標です。
* その他、本ロールのコード、ファイルに記載されている会社名および製品名は、各社の登録商標または商標です。

# Description
-----------
RHEL9に関する任意の設定コマンド実行、および任意パスにファイルのアップロード、指定したファイルおよびディレクトリのダウンロードを行うロールを提供します。

-------------

## 注意
OS関連のロール利用は、パラメータ内容を十分に確認し、事前評価を行ってからご利用ください。パラメータ値が誤っていると、ターゲットマシンへのアクセスができなくなるなど、トラブルが発生する可能性があります。

-------------

# Specification

## Ansibleサーバ

* Ansible バージョン 2.18.0 以上 (動作確認バージョン [core 2.18.1])
* Python バージョン 3.12以上  (動作確認バージョン 3.12.1)

# OS用ロールを使うまでの前準備
OS用ロールを利用する前に、ターゲットマシン(管理対象サーバ)へ事前に実施してください。

RHELサーバは、OSのインストール後、以下の設定を実施してください。（sshはデフォルトで動作している前提です）

* Ansible サーバと接続するネットワークの設定
* Ansibleがアクセスする、管理者権限のあるユーザーアカウントの作成


# 提供ロール一覧
## 情報取得ロール一覧
情報の取得に使用する以下のロールを提供します。

| ロール名 | Description | 
| ------- | ----------- | 
| [RH_cmd_executor/OS_gathering](RH_cmd_executor/OS_gathering) | 任意の設定コマンド実行、および任意ファイルまたはディレクトリのダウンロード | 

## 情報取得ロールのマニュアル一覧
各ロールで情報取得可能なパラメータは、以下の各ロールのマニュアル内のResultセクションに記載されたものとなります。

| 情報取得ロールのマニュアル | 
| ------- | 
| [RH_cmd_executor/OS_gathering マニュアル](RH_cmd_executor/OS_gathering/README.md) |

## 情報設定ロール一覧
情報の設定に使用する以下のロールを提供します。

| ロール名                            | Description                      |
| ----------------------------------- | -------------------------------- |
| [RH_cmd_executor/OS_build](RH_cmd_executor/OS_build) | 任意の設定コマンド実行、および任意パスにファイルのアップロード |

## 情報設定ロールのマニュアル一覧
各ロールで情報設定可能なパラメータは、以下の各ロールのマニュアル内のRole Variablesセクションに記載されたものとなります。

| 情報設定ロールのマニュアル |
| ------- |
| [RH_cmd_executor/OS_build マニュアル](RH_cmd_executor/OS_build/README.md) |

# Remarks
-------
OS仕様に依存する情報の設定ロールでは、実行は成功するが設定したパラメタが反映されない場合があります。

# License
-------

# Copyright
---------
Copyright (c) 2025 NEC Corporation

# Author Information
------------------
NEC Corporation
