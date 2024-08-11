---
title: "FileMaker Pro 2024に対応したXMLPaste 1.1.0を公開しました"
emoji: "📋"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["filemaker", "xmlpaste"]
published: true
published_at: 2024-08-11 09:00
---
Claris FileMaker Proのクリップボードデータを出力できるコマンドラインツールであるXMLPasteをGitHubで公開していますが、FileMaker Pro 2024に対応した[XMLPaste 1.1.0](https://github.com/emic/XMLPaste/releases/tag/1.1.0)を公開しました。本記事では、XMLPaste 1.1.0の新機能と変更点について紹介します。

## Claris FileMaker 2024について

FileMaker プラットフォームは、Appleの子会社であるClaris International Inc.が開発しているローコード開発プラットフォームです。

今年6月に登場したClaris FileMaker 2024では、AIに関するスクリプトステップと関数が追加されており、大規模言語モデル (LLM) を活用したセマンティック検索を既存のカスタム Appに追加できるようになっています。

カスタム Appにセマンティック検索を組み込むことにより、キーワードの一致ではなく意味に基づいてデータを検索する新しい方法をユーザーに提供できるようになります。さらに、自然言語を使って質問できることから、以前は見つけられなかった回答を既存データから得ることも可能になります。

**関連リンク**
- [Claris が 最新リリース Claris FileMaker 2024 の提供を開始（Claris）](https://www.claris.com/ja/blog/2024/filemaker2024-release)
- [蓄積したデータからさらに価値を引き出す Claris FileMaker 2024（Claris）](https://www.claris.com/ja/blog/2024/get-even-more-value-from-your-company-data-with-claris-filemaker-2024)

## XMLPasteの概要

XMLPasteは、Claris FileMakerのテーブルやフィールド、スクリプト、スクリプトステップ、レイアウトオブジェクト、カスタム関数、テーマなどに関する情報をUTF-8のXMLテキストとしてペーストできるコマンドラインツールです。

XMLPasteは、オープンソースソフトウェアであり、無料でご利用いただくことが可能です。Go言語で記述されており、ライセンスはMITライセンスです。

マルチプラットフォームに対応しているXMLPasteは、macOSとWindowsの両プラットフォームでご利用いただくことができます。コマンドプロンプトやPowerShell (Windows) 、ターミナルアプリケーション (macOS) 等でクリップボードデータの内容を表示できます。

## FileMaker Pro 2024に対応したXMLPaste 1.1.0の新機能

約5年ぶりにバージョンを更新したXMLPaste 1.1.0では、FileMaker Pro 2024のテーマに対応し、Windows版FileMaker Pro 2024でコピーしたテーマをペーストできるようになりました。

FileMaker Pro 2024では、テーマをコピーしたときの内部仕様が一部変更されており、Windows版XMLPaste 1.0.0でFileMaker Pro 2024でコピーしたテーマをペーストできなくなっていたことから、今回調整を行った次第です。

同時に、macOS版をIntel プロセッサとApple シリコン両対応のユニバーサルバイナリとしてビルドされるように調整し、Apple Silicon搭載Macに正式対応しました。

## macOS Sonoma 14およびWindows 11に対応

FileMaker Pro 2024に対応したXMLPaste 1.1.0では、macOS Monterey 12、macOS Ventura 13、macOS Sonoma 14およびWindows 11に正式に対応することにしました。

その一方、macOS Catalina 10.15およびそれ以前、Windows 7やWindows 10 Version 21H2およびそれ以前、および32bit版Windowsを動作保証対象外としました。同時に、バージョン19.5およびそれ以前のFileMaker Proもサポート対象外にしました。今後、AppleおよびClarisによるサポートが終了したバージョンについては動作保証対象外とする予定です。

2024年8月現在、XMLPaste 1.1.0の動作環境は、macOS Monterey 12、macOS Ventura 13、macOS Sonoma 14、 Windows 10 Version 22H2およびWindows 11であり、FileMaker Pro 19.6以降に対応しています。なお、FileMaker 19.6は2024年12月にサポートが終了する予定となっているため、来年以降はFileMaker Pro 2023以降の対応となります。

## まとめ

XMLPaste 1.1.0の新機能と変更点について解説しました。XMLPasteは、Claris FileMakerのテーブルやフィールド、スクリプト、スクリプトステップ、レイアウトオブジェクト、カスタム関数、テーマなどに関する情報をUTF-8のXMLテキストとしてペーストできるコマンドラインツールです。Go言語で記述されているXMLPasteは、MITライセンスで配布しているオープンソースソフトウェアであり、無料でご利用いただくことが可能です。

バージョン1.1.0では、Claris FileMaker Pro 2024のテーマに対応し、Windows版FileMaker Pro 2024でコピーしたテーマをペーストできるようになりました。また、macOS版がIntel プロセッサとApple シリコン両対応のユニバーサルバイナリとしてビルドされるようになり、Apple Silicon搭載Macに正式対応しました。
