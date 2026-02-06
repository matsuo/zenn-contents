---
title: "FileMaker Server 2025 (22.0.4)に対応したfmcsadmin 2.4.0を公開しました"
emoji: "⌨️"
type: "idea"
topics: ["filemaker", "fmcsadmin"]
published: true
published_at: 2026-02-06 22:00
---
Claris FileMaker Admin APIを用いてGo言語で実装したコマンドラインツールであるfmcsadminをGitHubで公開していますが、Claris FileMaker Server 2025 (22.0.4)に対応した[fmcsadmin 2.4.0](https://github.com/emic/fmcsadmin/releases/tag/2.4.0)を公開しました。本記事では、fmcsadmin 2.4.0の変更内容について紹介します。

## fmcsadminの概要

fmcsadminはFileMaker Server管理者向けのコマンドラインツールです。オープンソースソフトウェアとしてGitHubで公開しており、LinuxだけでなくmacOSやWindowsでもご利用いただけます。Go言語で記述されているfmcsadminは、Apache License, Version 2.0で配布しているオープンソースソフトウェアであり、無料でご利用いただくことが可能です。

当初は以前販売されていたFileMaker Cloud for AWSでfmsadminコマンドを使用できない問題を解決するために開発しましたが、現在ではFileMaker Serverに付属する純正のfmsadminコマンドにはない機能として公開鍵認証やリモート管理機能を備えている点が特色となっています。

## fmcsadmin 2.4.0でFileMaker Server 2025に対応

FileMaker プラットフォームは、Appleの子会社であるClaris International Inc.が開発しているローコード開発プラットフォームです。

Claris FileMaker 2025は2025年7月にリリースされていましたが、2025年12月に提供が開始されたClaris FileMaker Server 2025（バージョン22.0.4）でmacOS Tahoe 26のサポートが追加されたことを受けて、fmcsadminもFileMaker Server 2025およびmacOS Tahoe 26に正式に対応することにしました。

**関連リンク**
- [Claris が AI 機能がさらに強化された最新リリース Claris FileMaker 2025 の提供を開始](https://www.claris.com/ja/blog/2025/announcing-the-2025-release-of-claris-filemaker)

## macOS Tahoe 26だけでなくUbuntu 24.04 LTSにも対応

fmcsadmin 2.4.0では、Linux版FileMaker Server 2025の動作環境になっているUbuntu 24.04 LTSにも対応しました。その一方、macOS Ventura 13、Ubuntu 20.04 LTS、Windows 10、Windows 11 Version 22H2およびWindows Server 2019を動作保証対象外としました。同時に、FileMaker Server 2023もサポート対象外にしました。

fmcsadmin 2.4.0の動作環境は、Ubuntu Server 22.04 LTS（AMD64およびARM64）、Ubuntu 22.04 Desktop（AMD64およびARM64）、Ubuntu Server 24.04 LTS（AMD64およびARM64）、Ubuntu 24.04 Desktop（AMD64およびARM64）、macOS Sonoma 14、macOS Sequoia 15、macOS Tahoe 26、Windows Server 2022およびWindows 11 Version 23H2以降であり、FileMaker Server 2024およびFileMaker Server 2025に対応しています。

## まとめ

fmcsadmin 2.4.0の変更内容について解説しました。fmcsadminは、FileMaker Server管理者向けのコマンドラインツールであり、FileMaker Serverに付属する純正のfmsadminコマンドにはない機能として公開鍵認証やリモート管理機能を備えています。Go言語で記述されているfmcsadminは、Apache License, Version 2.0で配布しているオープンソースソフトウェアであり、無料でご利用いただくことが可能です。

Claris FileMaker 2025は2025年7月にリリースされていましたが、2025年12月に提供が開始されたClaris FileMaker Server 2025（バージョン22.0.4）でmacOS Tahoe 26のサポートが追加されたことを受けて、fmcsadminも今回公開したバージョン2.4.0でFileMaker Server 2025およびmacOS Tahoe 26に正式に対応することにしました。fmcsadmin 2.4.0は、macOS Tahoe 26だけでなくUbuntu 24.04 LTSにも対応しています。
