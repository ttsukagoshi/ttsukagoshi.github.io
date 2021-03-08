---
permalink: /ja/add-ons/group-merge/example-of-group-merge/
title: "Group Merge: まとめ差し込み（Group Merge）機能の使用例"
excerpt: An example of how the group merge feature of the add-on Group Merge works
last_modified_at: 2021-03-08T12:00:00+09:00
toc: true
published: true
---

このページはGoogle Workspaceアドオン「**Group Merge**」の機能である「まとめ差し込み（Group Merge）」の使用例を示すものです。  
[アドオンのページに戻る]({{ site.url }}{{ site.baseurl }}/ja/add-ons/group-merge/){: .btn .btn--primary .align-right}

## 宛先リストのサンプル
次のような宛先リストがあるとする：

| Email | 名前 | ミーティングID | 日付 | 開始時刻 | 終了時刻 |
| :--- | :---: | :---: | :---: | :---: | :---: |
|`tanaka@example.com`|田中|00001|2020年5月7日|13:00|14:00|
|`suzuki@sample.com`|鈴木|00002|2020年5月7日|14:30|15:30|
|`tanaka@example.com`|田中|00003|2020年5月8日|9:00|10:00|

{% raw %}
## テンプレート（Gmail下書き）のサンプル
そして以下のような本文を入力したGmailの下書きをテンプレートとして利用する：
```
{{名前}} 様,

この度はお申し込みいただき、誠にありがとうございます。
ウェブ会議システムのミーティングIDは次のとおりです：

[[
ミーティング{{i}}
日づけ: {{日付}}
時間: {{開始時刻}} – {{終了時刻}}
ミーティングID: {{ミーティングID}}

]]
当日お会いできるのを楽しみにしております。
```

## 結果
まとめ差し込み（Group Merge）機能を有効にした差し込み後のメールを、以下のようなものとなる：

### 田中さんへのメール
```
田中 様,

この度はお申し込みいただき、誠にありがとうございます。
ウェブ会議システムのミーティングIDは次のとおりです：

ミーティング1
日づけ: 2020年5月7日
時間: 13:00 – 14:00
ミーティングID: 00001

ミーティング2
日づけ: 2020年5月8日
時間: 9:00 - 10:00
ミーティングID: 00003

当日お会いできるのを楽しみにしております。
```

### 鈴木さんへのメール
```
鈴木 様,

この度はお申し込みいただき、誠にありがとうございます。
ウェブ会議システムのミーティングIDは次のとおりです：

ミーティング1
日づけ: 2020年5月7日
時間: 14:30 – 15:30
ミーティングID: 00002

当日お会いできるのを楽しみにしております。
```
{% endraw %}
  
[アドオンのページに戻る]({{ site.url }}{{ site.baseurl }}/ja/add-ons/group-merge/){: .btn .btn--primary .align-right}