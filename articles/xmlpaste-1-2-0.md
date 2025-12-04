---
title: "FileMaker Pro 2025（バージョン22.0.4）に対応したXMLPaste 1.2.0を公開しました"
emoji: "📋"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["filemaker", "xmlpaste"]
published: true
published_at: 2025-12-04 20:35
---
Claris FileMaker Proのクリップボードデータを出力できるコマンドラインツールであるXMLPasteをGitHubで公開していますが、FileMaker Pro 2025（バージョン22.0.4）に対応した[XMLPaste 1.2.0](https://github.com/emic/XMLPaste/releases/tag/1.2.0)を公開しました。本記事では、XMLPaste 1.2.0の変更内容について紹介します。

## XMLPasteの概要

オープンソースソフトウェアとして公開しているXMLPasteは、Claris FileMakerのテーブルやフィールド、スクリプト、スクリプトステップ、レイアウトオブジェクト、カスタム関数、テーマなどに関する情報をUTF-8のXMLテキストとしてペーストできるコマンドラインツールです。Go言語で記述されており、ライセンスはMITライセンスです。

マルチプラットフォームに対応しているXMLPasteは、macOSとWindowsの両プラットフォームでご利用いただくことができます。コマンドプロンプトやPowerShell (Windows) 、ターミナルアプリケーション (macOS) 等でクリップボードデータの内容を表示できます。

## XMLPaste 1.2.0でClaris FileMaker 2025に対応

FileMaker プラットフォームは、Appleの子会社であるClaris International Inc.が開発しているローコード開発プラットフォームです。

Claris FileMaker 2025は2025年7月にリリースされていましたが、2025年11月に提供が開始されたClaris FileMaker Pro 2025（バージョン22.0.4）でmacOS Tahoe 26のサポートが追加されたことを受けて、XMLPasteもFileMaker Pro 2025およびmacOS Tahoe 26に正式に対応することにしました。

**関連リンク**
- [Claris が AI 機能がさらに強化された最新リリース Claris FileMaker 2025 の提供を開始](https://www.claris.com/ja/blog/2025/announcing-the-2025-release-of-claris-filemaker)

## macOS Tahoe 26だけでなくmacOS Sequoia 15にも対応

FileMaker Pro 2025（バージョン22.0.4）に対応したXMLPaste 1.2.0では、macOS Tahoe 26だけでなくmacOS Sequoia 15にも対応しています。

一方で、Claris、AppleおよびMicrosoftによるサポートが終了したバージョンについては動作保証対象外とする方針にしているため、FileMaker Pro 19.6および2025年12月にサポートが終了する予定となっているFileMaker Pro 2023をサポート対象外にしました。同時に、macOS Monterey 12、macOS Ventura 13、Windows 10、Windows 11 Version 21H2およびWindows 11 Version 22H2もサポート対象外としました。

2025年12月現在、XMLPaste 1.2.0の動作環境は、macOS Sonoma 14、macOS Sequoia 15、macOS Tahoe 26およびWindows 11 Version 23H2以降であり、FileMaker Pro 2024およびFileMaker Pro 2025に対応しています。

## まとめ

XMLPaste 1.2.0の変更内容について解説しました。XMLPasteは、Claris FileMakerのテーブルやフィールド、スクリプト、スクリプトステップ、レイアウトオブジェクト、カスタム関数、テーマなどに関する情報をUTF-8のXMLテキストとしてペーストできるコマンドラインツールです。Go言語で記述されているXMLPasteは、MITライセンスで配布しているオープンソースソフトウェアであり、無料でご利用いただくことが可能です。

Claris FileMaker 2025は2025年7月にリリースされていましたが、2025年11月に提供が開始されたClaris FileMaker Pro 2025（バージョン22.0.4）でmacOS Tahoe 26のサポートが追加されたことを受けて、XMLPasteも今回公開したバージョン1.2.0でFileMaker Pro 2025およびmacOS Tahoe 26に正式に対応することにしました。XMLPaste 1.2.0は、macOS Tahoe 26だけでなくmacOS Sequoia 15にも対応しています。
