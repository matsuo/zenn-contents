---
title: "FileMaker Server 19.6に対応したfmcsadmin 2.1.0を公開しました"
emoji: "⌨️"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["filemaker", "fmcsadmin"]
published: true
published_at: 2023-05-17 12:30
---
FileMaker Admin APIを用いてGo言語で実装したコマンドラインツールであるfmcsadminをGitHubで公開していますが、FileMaker Server 19.6に対応した[fmcsadmin 2.1.0](https://github.com/emic/fmcsadmin/releases/tag/2.1.0)を公開しました。本記事では、fmcsadmin 2.1.0の新機能と変更点について紹介します。

## FileMaker プラットフォームについて

FileMaker プラットフォームは、Appleの子会社であるClaris International Inc.が開発しているローコード開発プラットフォームです。

FileMaker プラットフォームであれば、プログラミング言語を使った開発経験がない方でも、iPadでもデスクトップでも動作する業務アプリを作成できます。WindowsおよびmacOSで動作するFileMaker Proを用いて“カスタム App”と呼ばれるファイルを作成し、そのファイルを業務アプリとして活用できます。

FileMaker プラットフォームには2種類のサーバー製品が用意されています。1つはクラウドサービスとして提供されているFileMaker Cloud、もう1つはオンプレミス向けに販売されているFileMaker Serverです。

## fmcsadminの概要

fmcsadminはFileMaker Server管理者向けのコマンドラインツールです。本記事執筆時点では、FileMaker Cloudには対応していません。

当初は以前販売されていたFileMaker Cloud for AWSでfmsadminコマンドを使用できない問題を解決するために開発しましたが、現在ではFileMaker Serverに付属する純正のfmsadminコマンドにはない機能としてリモート管理機能を備えている点が特色となっています。

fmcsadminは、オープンソースソフトウェアとしてGitHubで公開しており、無料でご利用いただくことが可能です。ライセンスは、バージョン1.0.0以降ではMITライセンスでしたが、バージョン2.0.0でApache License, Version 2.0に変更しました。

## FileMaker Server 19.6に対応したfmcsadmin 2.1.0の新機能

昨年12月にFileMaker Server 19.6.1の提供が開始されましたが、当該バージョンのFileMaker ServerではFileMaker Admin APIの機能が拡充され、PKI（パブリックキーインフラストラクチャ）での認証がサポートされるようになりました。

FileMaker Server 19.6の機能拡充を受けてfmcsadminでもPKIでの認証をサポートするようにしました。本記事執筆時点では、当該機能はFileMaker Serverに付属する純正のfmsadminコマンドにはない機能です。

fmcsadmin 2.1.0に追加された-iオプションを使うことで当該機能を利用できます。新設された-iオプションを使用することで、FileMaker Server Admin Consoleの管理者アカウントとパスワードを使わずに、別途用意したプライベートキーファイルを用いて各種コマンドを実行できるようになります。使用例は次の通りですが、いくつか事前の準備が必要です。

```
% fmcsadmin -i /path/to/PRIVATEKEYFILE list files
```

## PKI認証にはキーファイルの準備とAdmin Consoleでの設定が必要

FileMaker Server 19.6では、FileMaker Serverフォルダの直下にあるToolsフォルダ内にあるAdminAPI_PKIAuthフォルダに、プライベートキー、パブリックキーおよびWebトークンの作成に使用できるPythonスクリプトファイルやREADME.txtファイルがインストールされるようになっています。

fmcsadmin 2.1.0に追加された-iオプションを使うには、AdminAPI_PKIAuthフォルダ内にあるPythonスクリプトでプライベートキーとパブリックキーを作成し、Admin Consoleの［管理］ページにある［管理者］タブにおいてFileMaker Admin API用のパブリックキーを登録しておく必要があります。

本記事ではキーファイルの作成方法に関する解説を省略します。詳しくは、上述のREADME.txtファイルやFileMaker Server Admin API Reference等を参照するようにしてください。

## macOS Ventura 13に対応

FileMaker Server 19.6に対応したfmcsadmin 2.1.0では、macOS Ventura 13に正式に対応することにしました。

その一方、macOS Catalina 10.15.7とWindows 10 Version 21H1を動作保証対象外としました。同時に、バージョン19.2およびそれ以前のFileMaker Serverもサポート対象外にしました。

fmcsadmin 2.1.0の動作環境は、Ubuntu Server 18.04 LTS、Ubuntu 18.04 Desktop、Ubuntu Server 20.04 LTS、Ubuntu 20.04 Desktop、CentOS Linux 7、macOS Big Sur 11以降（macOS Ventura 13で動作確認済み）およびWindows 10 Version 21H2以降（Windows 11で動作確認済み）であり、FileMaker Server 19.3以降に対応しています。

## まとめ

fmcsadmin 2.1.0の新機能と変更点について解説しました。fmcsadminは、FileMaker Server管理者向けのコマンドラインツールです。バージョン2.1.0では、FileMaker Server 19.6およびmacOS Ventura 13に対応し、PKI（パブリックキーインフラストラクチャ）での認証をサポートするための-iオプションを新たに追加しました。fmcsadminは、リモート管理にも対応していて、Linux、macOSおよびWindowsでご利用いただくことができます。
