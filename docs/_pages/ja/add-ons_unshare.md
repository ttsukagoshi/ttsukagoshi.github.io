---
permalink: /ja/add-ons/unshare/
title: 'Unshare'
excerpt: Googleドライブ内にある指定したファイルの共同編集者＆閲覧者を一括で削除するための、オープンソースのGoogle Workspaceアドオン
last_modified_at: 2022-06-21T00:30:00+09:00
toc: true
published: true
---

[English]({{ site.url }}{{ site.baseurl }}/add-ons/unshare/)/日本語
{: .align-center}

[![Google Workspaceマーケットプレイスでこのアドオンを入手する](https://img.shields.io/badge/Google%20Workspace%20Add--on-Available-green?style=flat-square)](https://workspace.google.com/marketplace/app/unshare/493847743062) [![clasp](https://img.shields.io/badge/built%20with-clasp-4285f4.svg?style=flat-square)](https://github.com/google/clasp) [![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)  
[![Lint Code Base](https://github.com/ttsukagoshi/unshare/actions/workflows/linter.yml/badge.svg)](https://github.com/ttsukagoshi/unshare/actions/workflows/linter.yml) [![CodeQL](https://github.com/ttsukagoshi/unshare/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/ttsukagoshi/unshare/actions/workflows/codeql-analysis.yml) [![Deploy](https://github.com/ttsukagoshi/unshare/actions/workflows/deploy.yml/badge.svg)](https://github.com/ttsukagoshi/unshare/actions/workflows/deploy.yml)

Google ドライブ内にある指定したファイルの共同編集者＆閲覧者を一括で削除するための、オープンソースの Google Workspace アドオン

## 概要

![Unshare icon](https://lh3.googleusercontent.com/pw/AM-JKLUeE_Ws9D1PaPh9_8CVmjpbscs1hQc8viJ_eBoZQ6OdolI3GyNrfAoWAy3w7hhvM2NSWY1EdFLsvCu2j5U7gtExx7Ou5uEctsImUiIvzDlKFRJl0LwRVqBMD7j2FHAiIsfS0-Vy7aFn5kaDh4MSvXZ4=s96-no){: .align-left} Google ドライブ内にある指定したファイルやフォルダのうち、自分がオーナー権限を持つものについて、共同編集者・閲覧者（コメント含む）を一括で削除するための Google Workspace アドオンです。特定のユーザだけでなく、「組織内で共有」といった共有設定も「制限付き（自分のみ）」に変更されます。

## 使い方

### 1. アドオンをインストール

[Google Workspace Marketplace](https://workspace.google.com/marketplace/app/unshare/493847743062) から本アドオンをインストール。  
このインストール作業は基本的にユーザごとに 1 回行えば、以降、特別な作業は不要。アップデート等の更新は自動的に行われる。

### 2. ファイル/フォルダを選択する

Google ドライブにて、共有を解除したいファイル/フォルダを選択します。画面右側にある本アドオンのアイコンをクリックして、表示されるサイドメニューの指示に従えば、共有解除は完了します。

対応するファイルでは、Google ドキュメント、Google スプレッドシート、Google スライドそれぞれの画面で、個別に Unshare を実行することができます。この場合も、画面右側にあるアドオンのアイコンをクリックします。
{: .notice--info}

## 利用規約

アドオンの使用には、[利用規約（英）]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/)への同意が必要です。

### プライバシーと OAuth スコープに関する情報公開

本節は、[利用規約（Terms and Conditions）]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/)の条項「[Additional Terms（追加条件）]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/#additional-terms)」で定義されたように利用規約の追補となるものであり、このアドオンのユーザの個人情報がどこように扱われるかをより詳細に明示したものです。
{: .notice--info}

[原文を見る]({{ site.url }}{{ site.baseurl }}/add-ons/unshare/#disclosure-on-privacy-and-oauth-scopes){: .btn .btn--primary .align-right}

## ソースコード

本アドオンのソースコードは GitHub 上で公開されています。機能追加・強化に関する要望や、バグ等の報告については GitHub 上の Issue によりご連絡ください。ソースコードに関するライセンスは、当該 GitHub レポジトリで明示しています。

[GitHub を見る](https://github.com/ttsukagoshi/unshare){: .btn .btn--primary .align-right}
