---
title: "FileMaker Server 2024 (21.1.1)に対応したfmcsadmin 2.3.0を公開しました"
emoji: "⌨️"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["filemaker", "fmcsadmin"]
published: true
published_at: 2025-03-06 19:40
---
Claris FileMaker Admin APIを用いてGo言語で実装したコマンドラインツールであるfmcsadminをGitHubで公開していますが、Claris FileMaker Server 2024 (21.1.1)に対応した[fmcsadmin 2.3.0](https://github.com/emic/fmcsadmin/releases/tag/2.3.0)を公開しました。本記事では、fmcsadmin 2.3.0の新機能と変更点について紹介します。

## fmcsadminの概要

fmcsadminはFileMaker Server管理者向けのコマンドラインツールです。オープンソースソフトウェアとしてGitHubで公開しており、LinuxだけでなくmacOSやWindowsでもご利用いただけます。

当初は以前販売されていたFileMaker Cloud for AWSでfmsadminコマンドを使用できない問題を解決するために開発しましたが、現在ではFileMaker Serverに付属する純正のfmsadminコマンドにはない機能として公開鍵認証やリモート管理機能を備えている点が特色となっています。

## FileMaker Server 2024 (21.1.1)に対応したfmcsadmin 2.3.0の新機能

2024年11月にFileMaker Server 2024 (21.1.1)の提供が開始されましたが、macOS Sequoia 15に対応した当該バージョンのFileMaker Serverでは、FileMaker Serverが起動したときにデータベースサーバーが停止する前に開いていたデータベースのみを開くように指定できるようになりました。また、HTTPSトンネリングがWindowsおよびmacOS上のFileMaker Serverでもサポートされるようになりました。

FileMaker Server 2024 (21.1.1)におけるFileMaker Admin APIの機能拡充を受けて、fmcsadmin 2.3.0では［最後に開いたデータベースのみを開く］設定および［HTTPS トンネリング］設定の表示と変更をサポートするようにしました。

## ［最後に開いたデータベースのみを開く］設定の表示および変更

FileMaker Server 2024 (21.1.1)では、FileMaker Serverが起動したときにデータベースサーバーが停止する前に開いていたデータベースのみを開くように指定できるようになりました。FileMaker Server Admin Consoleで設定を変更する場合、Admin Consoleの［構成］＞［一般設定］＞［最後に開いたデータベースのみを開く］を「有効」にすることで、本機能を使用できます。

fmcsadminで［最後に開いたデータベースのみを開く］設定を表示するにはgetコマンドを使います。使い方はfmsadminコマンドと同様で、使用例は次の通りです。

```
fmcsadmin -u USERNAME -p PASSWORD get serverprefs OnlyOpenLastOpenedDatabases
```

［最後に開いたデータベースのみを開く］設定を変更する場合にはsetコマンドを使います。OnlyOpenLastOpenedDatabases引数をtrueに設定すると、データベースサーバーが停止する前に開いていたデータベースのみを開くように指定できます。使い方はfmsadminコマンドと同様で、使用例は次の通りです。

```
fmcsadmin -u USERNAME -p PASSWORD set serverprefs OnlyOpenLastOpenedDatabases=true
```

OnlyOpenLastOpenedDatabases引数をfalseに設定すると、［最後に開いたデータベースのみを開く］設定が無効になり、FileMaker Serverが起動したときにすべてのデータベースを開く挙動に戻ります。

```
fmcsadmin -u USERNAME -p PASSWORD set serverprefs OnlyOpenLastOpenedDatabases=false
```

## HTTPSトンネリングオプションの取得および設定

FileMaker Server 2024 (21.1.1)では、HTTPSトンネリングがWindowsおよびmacOS上のFileMaker Serverでもサポートされるようになりました。FileMaker Server Admin Consoleで当該設定を有効化するには、Admin Consoleの［構成］＞［FileMaker クライアント］＞［HTTPS トンネリング］を「有効」に変更した後、FileMaker Serverを再起動します。

SSLサーバー証明書が適切に設定されている状態で当該設定を有効にすると、Claris FileMaker ProとClaris FileMaker GoはFileMaker Serverとの通信にポート5003ではなくポート443を使用できるようになります。

fmcsadminでHTTPSトンネリング設定を表示する場合もgetコマンドを使います。使用例は次の通りです。

```
fmcsadmin -u USERNAME -p PASSWORD get serverprefs EnableHttpProtocolNetwork
```

HTTPSトンネリング設定を変更する場合にはsetコマンドを使います。EnableHttpProtocolNetwork引数をtrueに設定すると、HTTPSトンネリング設定を有効にします。使い方はfmsadminコマンドと同様で、使用例は次の通りです。

```
fmcsadmin -u USERNAME -p PASSWORD set serverprefs EnableHttpProtocolNetwork=true
```

EnableHttpProtocolNetwork引数をfalseに設定すると、HTTPSトンネリング設定が再度無効になります。

```
fmcsadmin -u USERNAME -p PASSWORD set serverprefs EnableHttpProtocolNetwork=false
```

## macOS Sequoia 15に対応

fmcsadmin 2.3.0ではmacOS Sequoia 15に対応しています。その一方、macOS Monterey 12およびWindows 11 Version 21H2を動作保証対象外としました。同時に、バージョン19.6のFileMaker Serverもサポート対象外にしました。

fmcsadmin 2.3.0の動作環境は、Ubuntu Server 20.04 LTS（AMD64）、Ubuntu 20.04 Desktop（AMD64）、Ubuntu Server 22.04 LTS（AMD64およびARM64）、Ubuntu 22.04 Desktop（AMD64およびARM64）、macOS Ventura 13、macOS Sonoma 14、macOS Sequoia 15、Windows Server 2019、Windows Server 2022、Windows 10 Version 22H2およびWindows 11 Version 22H2以降であり、FileMaker Server 2023以降に対応しています。

なお、FileMaker Server 2023は2025年12月にサポートが終了する予定となっているため、2026年以降はFileMaker Server 2024以降の対応となります。

### （2025年3月7日追記）
「FileMaker Server 2023は2025年4月にサポートが終了する予定となっているため、2025年5月以降はFileMaker Server 2024以降の対応となります」を「FileMaker Server 2023は2025年5月にサポートが終了する予定となっているため、2025年6月以降はFileMaker Server 2024以降の対応となります」に修正しました。

### （2025年11月22日追記）
「FileMaker Server 2023は2025年5月にサポートが終了する予定となっているため、2025年6月以降はFileMaker Server 2024以降の対応となります」を「FileMaker Server 2023は2025年12月にサポートが終了する予定となっているため、2026年以降はFileMaker Server 2024以降の対応となります」に修正しました。

## まとめ

fmcsadmin 2.3.0の新機能と変更点について解説しました。fmcsadminは、FileMaker Server管理者向けのコマンドラインツールです。バージョン2.3.0では、Claris FileMaker Server 2024 (21.1.1)およびmacOS Sequoia 15に対応し、［最後に開いたデータベースのみを開く］設定および［HTTPS トンネリング］設定の表示と変更をサポートするようにしました。fmcsadminは、公開鍵認証やリモート管理にも対応していて、Linux、macOSおよびWindowsでご利用いただくことができます。
