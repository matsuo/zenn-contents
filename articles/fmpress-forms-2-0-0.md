---
title: "PHP 8.4に対応したFMPress Forms 2.0.0を公開しました"
emoji: "🔌"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["filemaker", "wordpress", "fmpress"]
published: true
published_at: 2025-11-22 19:50
---
PHP 8.4に対応した[FMPress Forms 2.0.0](https://ja.wordpress.org/plugins/fmpress-forms/)を2025年10月下旬に公開しました。本記事では、FMPress Forms 2.0.0の変更点について紹介します。

## FMPress Formsの概要

FMPress Formsは、Contact Form 7とClaris FileMaker Serverの連携を可能にするWordPressプラグインです。

WordPressで著名なフォームプラグインであるContact Form 7のアドオンプラグインとして動作し、Claris FileMakerのサーバー製品で使用できるClaris FileMaker Data APIを用いて実装されています。

Webフォーム自体はContact Form 7の機能を用いて作成し、不特定多数の方が訪れるWebサイトにFileMaker Serverと連動したフォームを設置したい場合に使用できます。オープンソースソフトウェアとして公開しているFMPress FormsのライセンスはWordPressと同じくGPLv2 or laterであり、[WordPressプラグインディレクトリ](https://ja.wordpress.org/plugins/fmpress-forms/)より無料でダウンロードできます。

## PHP 8.1、PHP 8.2、PHP 8.3およびPHP 8.4に対応

約3年ぶりの更新となるFMPress Forms 2.0.0では下記のソフトウェアに対応しています。

- Claris FileMaker Server 2024およびClaris FileMaker Server 2025
- PHP 8.1、PHP 8.2、PHP 8.3およびPHP 8.4
- WordPress 6.8（WordPress 6.1またはそれ以降）
- Contact Form 7 6.1.2（Contact Form 7 5.5またはそれ以降）

FMPress Forms 2.0.0では、新たにPHP 8.1、PHP 8.2、PHP 8.3およびPHP 8.4に対応し、PHP 5およびPHP 7を動作保証対象外としました。同時に、WordPress 5.7、WordPress 5.8、WordPress 5.9およびWordPress 6.0をサポート対象外にしました。

なお、FileMaker Server 2023は2025年12月にサポートが終了する予定となっているため、本バージョンではFileMaker Server 2024とFileMaker Server 2025のみの対応としました。

新しいバージョンのFileMaker ServerやPHPに対応したことで、セキュリティ更新が継続して提供される安全な環境でご利用いただくことができます。

## FileMakerの値一覧を使用した際に発生することがあった不具合を解消

FMPress Forms 1.3.1およびそれ以前において、Contact Form 7 5.9以降で、FileMakerの値一覧を使用して動的に項目を変更した場合に「未定義の値がこの項目を通じて送信されました。」と表示されて送信できない不具合がありました。

この不具合により一部のフォームで送信できないケースが発生していましたが、FMPress Forms 2.0.0で当該不具合を修正しました。

## FMPress Forms単体ではClaris FileMaker Cloudには非対応

FMPress Formsは、FileMaker Serverと連携して動作しますが、FMPress Forms単体ではClaris FileMaker Cloudとは連携しません。

以前、FMPress FormsからFileMaker Cloudへの接続を可能にするWordPressプラグインであるFMPress CloudAuthを併用することでFileMaker Cloudと連動したWebフォームを作成することができていましたが、[エミックラーニングの提供を2024年2月に終了](https://www.famlog.jp/article/4857)して以来、現在はFMPress CloudAuthの一般公開を行っていない状況です。

## まとめ

2025年10月に公開したFMPress Forms 2.0.0の変更点について解説しました。約3年ぶりの更新となるFMPress Forms 2.0.0では、FileMaker Server 2025やPHP 8.4といった新しいバージョンのソフトウェアに対応したことで、セキュリティ更新が継続して提供される安全な環境でご利用いただくことができます。
