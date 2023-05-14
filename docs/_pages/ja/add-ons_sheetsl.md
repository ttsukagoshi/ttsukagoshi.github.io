---
permalink: /ja/add-ons/sheetsl/
title: 'SheetsL: Google スプレッドシート&trade;のための DeepL 翻訳'
excerpt: DeepL&trade; 翻訳を Google スプレッドシート&trade; で直接利用するためのアドオン。無料＆オープンソース。
last_modified_at: 2023-05-12T02:00:00+09:00
toc: true
published: true
---

[English]({{ site.url }}{{ site.baseurl }}/add-ons/sheetsl/)/日本語  
{: .align-center}

[![このアドオンをGoogle Workspace Marketplaceでインストールする](https://img.shields.io/badge/Google%20Workspace%20Add--on-Available-green?style=flat-square)](https://workspace.google.com/marketplace/app/sheetsl/1006481107276) [![claspのGitHubレポジトリへのリンク](https://img.shields.io/badge/built%20with-clasp-4285f4.svg?style=flat-square)](https://github.com/google/clasp) [![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)
[![CodeQL](https://github.com/ttsukagoshi/sheetsL/actions/workflows/codeql.yml/badge.svg)](https://github.com/ttsukagoshi/sheetsL/actions/workflows/codeql.yml) [![Lint Code Base](https://github.com/ttsukagoshi/sheetsL/actions/workflows/linter.yml/badge.svg)](https://github.com/ttsukagoshi/sheetsL/actions/workflows/linter.yml) [![Publish Release](https://github.com/ttsukagoshi/sheetsL/actions/workflows/deploy.yml/badge.svg)](https://github.com/ttsukagoshi/sheetsL/actions/workflows/deploy.yml)

DeepL&trade; 翻訳を Google スプレッドシート&trade; で直接利用するための、オープンソースのアドオンです。選択したセル範囲の内容を DeepL API で翻訳して、その結果を、選択したセル範囲の右隣に表示します。DeepL API Free または Pro アカウントが必要です。

![SheetsL icon](/assets/images/sheetsl/SheetsL_Application_Card_Banner_220.png)

## 前提条件：DeepL API アカウントを持っていること

[DeepL API アカウント](https://www.deepl.com/ja/account)を作成し、その認証キーを使用します。認証キーは、[DeepL のアカウント情報ページ](https://www.deepl.com/ja/account/summary)で確認できます。

![DeepL APIアカウント情報ページのスクリーンショット]({{ site.url }}{{ site.baseurl }}/assets/images/sheetsl/deepl-account-page.png)

詳細は以下の公式ドキュメントをご確認ください:

- [DeepL API Free と DeepL API Pro – DeepL ヘルプセンター](https://support.deepl.com/hc/ja/articles/360021183620-DeepL-API-Free%E3%81%A8DeepL-API-Pro)
- [DeepL API Free – DeepL ヘルプセンター](https://support.deepl.com/hc/ja/articles/360021200939-DeepL-API-Free)
- [認証キー – DeepL ヘルプセンター](https://support.deepl.com/hc/ja/articles/360020695820-%E8%AA%8D%E8%A8%BC%E3%82%AD%E3%83%BC)

## 使い方

### 1. アドオンをインストールする

[Google Workspace Marketplace](https://workspace.google.com/marketplace/app/sheetsl/1006481107276) からこのアドオンをインストールします。アップデートは自動的に配信されます。

### 2. DeepL API の認証キーを設定する

Google Sheets のメニューから、「拡張機能」→「SheetsL」→「Settings」→「Set Auth Key」と進みます。[DeepL のアカウント情報ページ](https://www.deepl.com/ja/account/summary)で確認できる、DeepL API アカウントの認証キーを入力します。

![SheetsLでDeepL API認証キーを設定するメニューのスクリーンショット]({{ site.url }}{{ site.baseurl }}/assets/images/sheetsl/set-auth-key.png)

DeepL API の認証キーが、SheetsL 内でどのように安全に保存されるのかが気になる方は、「[SheetsL で DeepL API 認証キーはどのように保存される？](#deepl-api-認証キーはどのように保存される)」をご覧ください。
{: .notice--info}

### 3. 翻訳先の言語を設定する

Google Sheets のメニューから、「拡張機能」→「SheetsL」→「Settings」→「Set Language」と進みます。ソース言語（原文の言語）とターゲット言語（翻訳後の言語）の言語コードをそれぞれ入力するよう求められます。メッセージに記載されている、DeepL で利用可能な言語のいずれかを選択して入力してください。

ターゲット言語（翻訳後の言語）の指定は必須ですが、ソース言語（原文の言語）は空白にしておくことができます。その場合は、DeepL の自動言語検出により原文の言語が判定されます。
{: .notice--info}

### 4. 翻訳する

DeepL で翻訳するセル範囲を選択した後、「拡張機能」→「SheetsL」→「Translate」を選択します。しばらくすると、元の範囲の右側に隣接する同じ行数・列数の範囲に、翻訳されたテキストがコピーされます。

![翻訳されたテキストがどのようにスプレッドシート上で表示されるかのスクリーンショット]({{ site.url }}{{ site.baseurl }}/assets/images/sheetsl/source-target-ranges.png)

例えば、`A2:B4`の範囲を翻訳対象として選択した場合、翻訳されたテキストは`C2:D4`の範囲（「ターゲット範囲」）に表示されます。翻訳時にターゲット範囲が空でない場合、セルを上書きしてよいかどうかの確認メッセージが表示されます。
{: .notice--info}

## よくある質問

### DeepL API 認証キーはどのように保存される？

[DeepL API の認証キーを設定する](#2-deepl-api-の認証キーを設定する)で入力した DeepL API 認証キーは、アドオンの[ユーザプロパティ](https://developers.google.com/apps-script/guides/properties?hl=ja)に保存されます。ユーザプロパティは、そのユーザのみがアクセス権を持つもので、アドオンの開発者や、他のアドオン・アプリ、Google Sheets ファイルを共有している他のユーザなど、他の誰とも共有されません。

## 利用規約

アドオンの使用には、[利用規約（英）]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/)への同意が必要です。

### プライバシーと OAuth スコープに関する情報公開

本節は、[利用規約（Terms and Conditions）]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/)の条項「[Additional Terms（追加条件）]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/#additional-terms)」で定義されたように利用規約の追補となるものであり、このアドオンのユーザの個人情報がどこように扱われるかをより詳細に明示したものです。
{: .notice--info}

[原文を見る]({{ site.url }}{{ site.baseurl }}/add-ons/sheetsl/#disclosure-on-privacy-and-oauth-scopes){: .btn .btn--primary .align-right}

## ソースコード

本アドオンのソースコードは GitHub 上で公開されています。機能追加・強化に関する要望や、バグ等の報告については GitHub 上の Issues によりご連絡ください。ソースコードに関するライセンスは、当該 GitHub レポジトリで明示しています。

[GitHub を見る](https://github.com/ttsukagoshi/sheetsL){: .btn .btn--primary .align-right}

## アイコンの出典

The original icon of this add-on is the [Document icons created by Freepik - Flaticon](https://www.flaticon.com/free-icons/document), modified by [ttsukagoshi](https://github.com/ttsukagoshi).
