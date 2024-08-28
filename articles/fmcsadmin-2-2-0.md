---
title: "FileMaker Server 2024に対応したfmcsadmin 2.2.0を公開しました"
emoji: "⌨️"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["filemaker", "fmcsadmin"]
published: true
published_at: 2024-08-28 18:00
---
Claris FileMaker Admin APIを用いてGo言語で実装したコマンドラインツールであるfmcsadminをGitHubで公開していますが、Claris FileMaker Server 2024に対応した[fmcsadmin 2.2.0](https://github.com/emic/fmcsadmin/releases/tag/2.2.0)を公開しました。本記事では、fmcsadmin 2.2.0の新機能と変更点について紹介します。

## fmcsadminの概要

fmcsadminはFileMaker Server管理者向けのコマンドラインツールです。LinuxだけでなくmacOSやWindowsでもご利用いただけます。

当初は以前販売されていたFileMaker Cloud for AWSでfmsadminコマンドを使用できない問題を解決するために開発しましたが、現在ではFileMaker Serverに付属する純正のfmsadminコマンドにはない機能として公開鍵認証やリモート管理機能を備えている点が特色となっています。

fmcsadminは、オープンソースソフトウェアとしてGitHubで公開しており、無料でご利用いただくことが可能です。ライセンスは、バージョン1.0系統ではMITライセンスとしていましたが、バージョン2.0系統ではApache License, Version 2.0に変更しました。

## FileMaker Server 2024に対応したfmcsadmin 2.2.0の新機能

今年6月にFileMaker Server 2024の提供が開始されましたが、データベースのアップロードや管理者の役割への対応、データベースサインイン設定の取得など、当該バージョンのFileMaker ServerではFileMaker Admin APIの機能が大幅に拡充されています。

FileMaker Server 2024におけるFileMaker Admin APIの機能拡充を受けて、fmcsadminでは新規ユーザーのブロックならびに持続的なキャッシュ設定の表示および変更をサポートするようにしました。

昨年提供が開始されていたFileMaker Server 2023では、共有データベースファイルの最大数が125から256に増加していたので、その増加への対応もあわせて行いました。

## 新規ユーザーブロック設定の表示および変更

FileMaker Server 2024では、FileMaker Server上でホストされているデータベースへの新規接続を禁止できる機能が新たに追加されています。

FileMaker Server Admin Consoleで設定を変更する場合、Admin Consoleの［構成］＞［一般設定］＞［新規ユーザをブロックする］を「有効」にすることで、本機能を使用できます。当該機能を有効化する前から接続していた場合、そのユーザーは影響を受けず、接続を維持できます。

fmcsadminで新規ユーザーのブロック設定を表示するにはgetコマンドを使います。使い方はfmsadminコマンドと同様で、使用例は次の通りです。

```
fmcsadmin -u USERNAME -p PASSWORD get serverprefs BlockNewUsersEnabled
```

新規ユーザーのブロック設定を変更する場合にはsetコマンドを使います。BlockNewUsersEnabled引数をtrueに設定すると、新規ユーザーのブロック設定を有効にします。使い方はfmsadminコマンドと同様で、使用例は次の通りです。

```
fmcsadmin -u USERNAME -p PASSWORD set serverprefs BlockNewUsersEnabled=true
```

BlockNewUsersEnabled引数をfalseに設定すると、新規ユーザーのブロック設定が再度無効になります。

```
fmcsadmin -u USERNAME -p PASSWORD set serverprefs BlockNewUsersEnabled=false
```

## 持続的なキャッシュ設定の表示および変更

FileMaker Server 2024では、データベースサーバーのプロセスが突然終了した場合にデータベースの破損を避けるために用意されている持続的なキャッシュがプレビュー機能ではなくなっています。

FileMaker Server Admin Consoleで当該設定を有効化するには、Admin Consoleの［構成］＞［一般設定］＞［持続的なキャッシュ］を「有効」に変更します。

fmcsadminで持続的なキャッシュ設定を表示する場合もgetコマンドを使います。使用例は次の通りです。

```
fmcsadmin -u USERNAME -p PASSWORD get serverprefs PersistCacheEnabled
```

持続的なキャッシュ設定を変更する場合にはsetコマンドを使います。PersistCacheEnabled引数をtrueに設定すると、持続的なキャッシュ設定を有効にします。使い方はfmsadminコマンドと同様で、使用例は次の通りです。

```
fmcsadmin -u USERNAME -p PASSWORD set serverprefs PersistCacheEnabled=true
```

PersistCacheEnabled引数をfalseに設定すると、持続的なキャッシュ設定が再度無効になります。

```
fmcsadmin -u USERNAME -p PASSWORD set serverprefs PersistCacheEnabled=false
```

持続的なキャッシュを有効にしている場合において、PersistCacheEnabled引数の代わりにSyncPersistCache引数を用いると、電源オフ時に持続的なキャッシュをディスクに自動的に保存する［持続的なキャッシュをディスクと同期］設定を表示および変更できます。

設定を表示する場合にはgetコマンドを、設定を変更する場合にはsetコマンドを使います。

```
fmcsadmin -u USERNAME -p PASSWORD get serverprefs SyncPersistCache
```

```
fmcsadmin -u USERNAME -p PASSWORD set serverprefs SyncPersistCache=true
```

同様に、PersistCacheEnabled引数の代わりにDatabaseServerAutoRestart引数を用いると、データベースサーバーが予期せず終了した場合に自動的に再起動する［データベースサーバーの自動再起動］設定を表示および変更できます。

```
fmcsadmin -u USERNAME -p PASSWORD get serverprefs DatabaseServerAutoRestart
```

```
fmcsadmin -u USERNAME -p PASSWORD set serverprefs DatabaseServerAutoRestart=true
```

fmcsadminでは、FileMaker Server Admin Consoleと同様に、持続的なキャッシュを有効にしている場合にのみ［持続的なキャッシュをディスクと同期］および［データベースサーバーの自動再起動］設定を変更できるようになっています。

## Ubuntu 22.04 LTS、Ubuntu 22.04 LTS for ARMおよびmacOS Sonoma 14に対応

fmcsadmin 2.2.0では、Ubuntu 22.04 LTS（AMD64およびARM64）、macOS Sonoma 14、Windows Server 2019およびWindows Server 2022に正式に対応することにしました。FileMaker Server 2023でUbuntu 22.04 LTS for ARMがサポートされるようになったことを受けて、fmcsadminも今回公開したバージョン2.2.0からARMに対応したLinux版（配布ファイル名は「fmcsadmin-2.2.0-linux-arm64.tar.gz」）の提供を開始することにしました。

その一方、Ubuntu 18.04 LTS、CentOS Linux 7、macOS Big Sur 11およびWindows 10 Version 21H1を動作保証対象外としました。同時に、バージョン19.5およびそれ以前のFileMaker Serverもサポート対象外にしました。

fmcsadmin 2.2.0の動作環境は、Ubuntu Server 20.04 LTS（AMD64）、Ubuntu 20.04 Desktop（AMD64）、Ubuntu Server 22.04 LTS（AMD64およびARM64）、Ubuntu 22.04 Desktop（AMD64およびARM64）、macOS Monterey 12以降（macOS Sonoma 14で動作確認済み）、Windows Server 2019、Windows Server 2022およびWindows 10 Version 22H2以降（Windows 11で動作確認済み）であり、FileMaker Server 19.6以降に対応しています。

なお、FileMaker Server 19.6は2024年12月にサポートが終了する予定となっているため、来年以降はFileMaker Server 2023以降の対応となります。

## まとめ

fmcsadmin 2.2.0の新機能と変更点について解説しました。fmcsadminは、FileMaker Server管理者向けのコマンドラインツールです。バージョン2.2.0では、Ubuntu 22.04 LTS（AMD64およびARM64）、macOS Sonoma 14、Windows Server 2019およびWindows Server 2022に対応し、新規ユーザーのブロックならびに持続的なキャッシュ設定の表示および変更をサポートするようにしました。FileMaker Server 2023以降でUbuntu 22.04 LTS for ARMがサポートされるようになったことを受けて、ARMに対応したLinux版の提供も新たに開始しています。fmcsadminは、公開鍵認証やリモート管理にも対応していて、Linux、macOSおよびWindowsでご利用いただくことができます。
