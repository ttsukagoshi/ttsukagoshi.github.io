---
permalink: /ja/add-ons/group-merge/
title: 'Group Merge - Gmailのための差し込みメール作成'
excerpt: Gmailのテンプレート（下書き）を元にして受信者ごとに宛名などを差し込んだメールを作成する、オープンソースのGoogle Workspaceアドオン。GmailとGoogleスプレッドシート連携。宛先リストに、同じ宛先（メールアドレス）が複数入力されている場合、内容を1通のメールにまとめて送信できる**「まとめ差し込み（Group Merge）」**機能つき。
last_modified_at: 2022-05-08T01:00:00+09:00
toc: true
published: true
---

[English]({{ site.url }}{{ site.baseurl }}/add-ons/group-merge/)/日本語  
{: .align-center}

[![Google Workspaceマーケットプレイスでこのアドオンを入手する](https://img.shields.io/badge/Google%20Workspace%20Add--on-Available-green?style=flat-square)](https://workspace.google.com/marketplace/app/group_merge_mail_merge_for_gmail/586770229603) [![clasp](https://img.shields.io/badge/built%20with-clasp-4285f4.svg?style=flat-square)](https://github.com/google/clasp) [![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)  
[![CodeQL](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/codeql-analysis.yml) [![Deploy](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/deploy.yml/badge.svg)](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/deploy.yml) [![Labeler](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/label.yml/badge.svg)](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/label.yml) [![Lint Code Base](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/linter.yml/badge.svg)](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/linter.yml)

Gmail のテンプレート（下書き）を元にして受信者ごとに宛名などを差し込んだメールを作成する、オープンソースの Google Workspace アドオン

**レガシー（スプレッドシート）版**  
Google Workspace アドオンとして提供される前に公開していたレガシー版（スプレッドシート版）は現在、開発が停止しています。今後、Google 側での仕様変更等により使用できなくなる可能性もありますので、ご注意ください。ソースコードやサンプルスプレッドシートを確認したい方のために[GitHub 上のブランチ](https://github.com/ttsukagoshi/mail-merge-for-gmail/tree/legacy-v1.8.0-spreadsheet)として残していますので、必要に応じてご参照ください。
{: .notice--info}

{% raw %}

## 概要

![Group Mergeのアイコン](https://lh3.googleusercontent.com/pw/ACtC-3eZPKFkzQJvMs2P_HgJIwNRSy1OGklUpOr0gm9ncC3OGcJw-nVvNUDYta6mMWo3d57gEc9KD_KV-UNOJvcTCBjGru3MG1KUpzP3z15I-bjEfT3u1V12mzRQrcA89pzb_RoIbINO3B1WxT4qP0KefNs=s96-no){: .align-left} Gmail と Google スプレッドシートを使って、宛名や会議の日時などの情報を宛先ごとに個別化したメールを作成して送信するための、オープンソースの Google Workspace アドオン。

- 宛先リスト内に同じメールアドレスの宛先が 2 つ以上ある場合に、内容を 1 通のメールにまとめられる「**まとめ差し込み（Group Merge）**」機能つき。
- Gmail の下書きをテンプレートとして利用。**書式設定**（文字の色など）や**添付ファイル**、**CC**及び**BCC**、そして**Gmail ラベル**が差し込み後のメールにも引き継がれる。

## 使い方

このセクションで説明されている「使い方」は**あくまで開発者オススメの基本となる流れ**であって、**「遵守すべし」というものではありません**。アドオン自体はコンテキスト非依存型、つまり Gmail・Google スプレッドシートのいずれの画面でも自由に呼び出すことができるものなので、ユーザ側で使いやすいそれぞれの「流れ」を見つけていただければ幸いです。オープンソースなので、それこそ、ご自由に。
{: .notice--info}

### 1. アドオンをインストール

[Google Workspace Marketplace](https://workspace.google.com/marketplace/app/group_merge_mail_merge_for_gmail/586770229603)から本アドオンをインストール。  
このインストール作業は基本的にユーザごとに 1 回行えば、以降、特別な作業は不要。アップデート等の更新は自動的に行われる。

### 2. 宛先リストを作成

Google スプレッドシートで宛先リストを作成する。既存のスプレッドシートでも可。  
![宛先リストとして使用しているスプレッドシートのスクリーンショット例](https://lh3.googleusercontent.com/pw/ACtC-3fIrGVp4uskIute2jXMV04In4ijDyxPoI8KAFAMG4l-PHfLWzHqz8HyMmsnL5vIf-SihZyn4RkJayLlSBFIbvw9asKjZgliO_xKHY3DicAFJBA_yfGprhoqWf7Ne7LUg7aGOmcDzCB9axQPoIiuHCA=w2548-h952-no){: .align-center}

1. リストとなるシートの 1 行目はヘッダーとして、列名以外は入力しない。
2. 日付や時刻の表示は、スプレッドシートに表示されている形式がそのまま差し込みメールとして反映される。宛先が英語圏の場合は`Apr. 1, 2021`、日本人の場合は`2021年4月1日`などと差し込みデータの形式を相手によって変えたい時は、宛先リストの表示形式を調整する。
3. セル内の改行は差し込み後のメールにも反映されるが、<span style="color: red;">文字色</span>や**太字**、_イタリック体_、~~取り消し線~~などの書式設定は引き継がれない。代わりに、Gmail 画面にてテンプレートとなる下書きメールを作成する際に、各種 HTML による書式設定が可能となる。
4. スクリーンショット ↑ にあるように、ひらがなや漢字といった基本的な全角文字をヘッダ行（列名）に使うことも可能。
5. 小文字の`i`単体を列名として使用することは、予期しないエラーを防ぐためにも避けること。後述しているように、この`i`はまとめ差し込み（Group Merge）機能の一部として使用されている要素。

**ご注意ください** 1 日に送信できる Gmail/Google Workspace メールの数は、[Google によって制限されています](https://developers.google.com/apps-script/guides/services/quotas)。このアドオンは、あくまでその制限の中でメールを一括送信するためのものです。
{: .notice--warning}

### 3. Google スプレッドシートからアドオンを開く

Group Merge アドオンのアイコンをクリックし、サイドパネルを開く。  
![GoogleスプレッドシートのサイドパネルにあるGroup Mergeアイコン](https://lh3.googleusercontent.com/pw/ACtC-3ezL4YANFeGvtCQURMARrmqqCYY5uAxzFrztjhNKszO5LePgTrlJqi_MySzggICmdv04rRiONwK8AjPflkjX4Uhtgr3We-Ka4YI2l6Asjbws24DUqrvSMVY43FBTU5k7twh8RSBzG823lhoKiWdRHZy=w526-h319-no){: .align-center}  
以下のようにアドオンのページがサイドパネルとして表示される：  
![サイドパネルで起動したGroup Mergeアドオン](https://lh3.googleusercontent.com/pw/ACtC-3evDtIezaBxpPAtlkrjm5qrrtOAd4dCAqokNB3oxxqlrWqJ0kl8dUIyNww0jW0TcUn0fyN5W4CJ8_dnGOgZyQHin-y6uTWn-Icdd4BLn3rMplV6L5u-KZcoHDd3NSi3FF59zrg3C6a3H4UvA4qGKovY=w1102-h567-no){: .align-center}

### 4. 設定項目を入力する (1) - Google スプレッドシート編

サイドパネルをスクロールしながら、セクション 1「宛先リストの設定」の各項目（**スプレッドシート URL**、**シート名**、および**宛先メールアドレス**）を入力していく。任意入力の**CC**と**BCC**は空白でも問題ない。

- **スプレッドシート URL**は、Google スプレッドシートからこのアドオンを開いている場合、開いているスプレッドシートの URL が自動入力されている。
- **To**は差し込みフィールド（merge fields）として入力する（例：`{{Email}}`）。2 つ以上の差し込みフィールドは入力できないことに注意（不可の例：`{{Email1}},{{Email2}}`）。この場合はエラーが返される。宛先によって複数の可変な送信先を設定したい場合は**CC**や**BCC**を活用する。1 つの差し込みフィールドに、複数の固定メールアドレスをカンマ区切りで入力することは可能（例：`{{Email}},fixedEmail1@example.com,fixedEmail2@example.com`）。
- \[任意\] **CC**や**BCC**には、[Google が定める制限内](https://developers.google.com/apps-script/guides/services/quotas#current_quotas)であれば、いくらでも差し込みフィールドを入れられる（例：`{{cc1}},{{cc2}},{{cc3}}, ...`）。

セクション 1「宛先リストの設定」の各項目を入力したのち、サイドパネルを下までスクロールして「**ユーザ設定として保存**」ボタンをクリック。  
![「ユーザ設定として保存」ボタン](https://lh3.googleusercontent.com/pw/ACtC-3d1F8Rkr-W5IV8eSVU7yDOAxSwN3w6ek48FuIGpIYZ8QceLD8Da9nMQ0v-hmWAA_HJcgnez5ptQfvasgKExAaYg1FKUmU7NfASZqtfdg-D4d5N_e1ytzEhha1S6Zx398n3nin5K0ITcaBUUiYKVneHK=w500){: .align-center}

**設定はどこに保存される？** [設定の保存と呼び出し](#設定の保存と呼び出し)に、設定がどのように保存されて、呼び出されるかの詳細があります。
{: .notice--info}

### 5. テンプレートとなる下書きメールを Gmail で作成

[Gmail](https://mail.google.com/mail/)に移動し、テンプレートとなる下書きを作成する。  
![テンプレートとなるGmail下書き例のスクリーンショット](https://lh3.googleusercontent.com/pw/ACtC-3eQFoOuu3CyUzqg5nrP_kGlq6jxMcQ6sAJqc9faa7eAzbIoicoRqPV3JP82cdPylyzn8Y9a-T1jHlNjs9yVXFG7D-NkrC0Cd1oygD2orpgqwi2tgnwR_nZJlkFxytMmF2uCEYQPZg1xQ9FroUy8UOk6=w500){: .align-center}

#### 5-1. To、CC、BCC、および Reply-To 設定

![テンプレートのTo、CC、BCCを編集する](https://lh3.googleusercontent.com/pw/ACtC-3dx3QJ0UDGJQRSqqCGuOXPwwm8wg6F05RnqOv7GggiIigi8az1Vyb8yMz_zlTPgPXtSz6gjgzm1Af0tHFyvj7kDfaUp495HLo9dqlyVmTUpJzytrEmYBYHTTi0GTr1grCBgC3f8ETZ9OvbW7b7xG2jx=w1020-h468-no){: .align-center}

- メールの編集画面では、基本的に**To**、**CC**、**BCC**は空白とする（アドオンのサイドパネルで設定するため）。編集画面で差し込みフィールド付きの宛先（例：`{{Email}}`）を入力しても、無効にされる。ただし上のスクリーンショット例のように`myTeam@mydomain.com`といった固定のメールアドレスであれば、差し込み後の各メールにも引き継がれる。
- **Reply-To**設定はオプションでアドオンのサイドパネルから有効にして任意の値を指定することができる（初期設定では無効）。[「高度な設定」の「Reply-To」](#reply-to)を参照のこと。

#### 5-2. 件名と本文

テンプレートの件名及び本文では、差し込みフィールド（merge fields）`{{ }}`や[まとめ差し込み（group merge）](#5-5-group-merge)フィールド`[[ ]]`を使うことで、受信者ごとに個別化したメールを作成することができる。  
![テンプレートとなる下書きの件名と本文の編集画面](https://lh3.googleusercontent.com/pw/ACtC-3fHRxVSL-E7RkK_gU35V5g4sG1n7LxJ-N2j8TS1QKvwZQ1lPlXCSYj-fq2K_pLsSHwiBu_G_D16MrTeUZSVTvDNBiBpmwvQg8qiDITO3MESB3iVtZde5ue83FHsUdHdBA9Ej_FNrLgjU-U-DQFOkTMB=w1044-h761-no){: .align-center}

テンプレートとなる下書きメールの**件名に重複がないようご注意ください**。入力した件名を持つ下書きメールが 2 通以上ある場合、エラーとなります。
{: .notice--warning}

初期設定では、`{{二重の中かっこ（半角）で括られた文字列}}`が差し込みフィールドとして認識される。

```
{{会社名}} {{氏名}}様
〜〜〜
```

- フィールド名は、[2. 宛先リストを作成](#2-宛先リストを作成)で作成した宛名リストのフィールド名と一致している必要がある。**全角・半角や大文字・小文字も区別されることに注意。**
- テンプレートでフィールドとして指定したもののそのようなフィールドが宛先リストに存在しない場合、もしくは該当するフィールドの値が空白だった場合に差し込む文字列は、任意に設定できる。初期設定では`NA`となっている。この文字列は[「高度な設定」の「データ不在時の差し込みテキスト」](#データ不在時の差し込みテキスト)で調整できる。
- リッチテキスト（HTML メール）で下書きを作成したのであれば、書式設定等も引き継がれる。

宛先リストで、同じ宛先についてのエントリーが複数存在する場合に、その宛先についての内容を 1 通のメールにまとめることができる<span style="color: red;">まとめ差し込み（Group Merge）機能</span>については、[専用の項目を設けてある](#5-5-まとめ差し込みgroup-merge)ので、そちらを参照のこと。

**Pro Tips💡**  
差し込みフィールド及びまとめ差し込みフィールドのマーカーは[「高度な設定」の「フィールドマーカー」](#フィールドマーカー)にて変更可能です。
{: .notice--info}

#### 5-3. 添付ファイル

テンプレートとなる下書きメールに添付された添付ファイル（インライン画像を含む）は、差し込み後のメールにも同じように添付される。  
![通常の添付ファイルとインライン画像のスクリーンショット例](https://lh3.googleusercontent.com/pw/ACtC-3das9KldhoGPNWRQv7HEWM6-XMyjndPNfrnn1LqV18j83W8NSSntjd8gXOwSV3TQQHtP7xN4BobcgmqB3ODSnikkWA7ylhOQHtwiwPf1sJahIInoQAoShEcsW-Fq2M7RS8-ZbAeaSHZzg6-hfjyK5Pw=w1016-h632-no){: .align-center}

**Pro Tips💡**  
インライン画像は、Gmail のメール作成でリッチテキスト（HTML）形式が有効になっている場合にのみ添付できます。
{: .notice--info}

#### 5-4. Gmail ラベル

テンプレートとなる下書きメールに付けられたラベルは、差し込み後のメールにも付加される。  
![Attaching labels to Gmail drafts](https://lh3.googleusercontent.com/pw/ACtC-3dfi3QkCBLJ7jZ0zuGYFdPTiGlMy6gdULn7xTgIUs1ih5c-bfOptMfHMMXnAuPDSdjW-lRAhf_fpLVaPGCAdcfC587fVGTMESKxpcy4ytNAZ-e2UxYefInFWLzffqbv4nlZcKA1rhtZN5hwlAs5gOzH=w1006-h576-no){: .align-center}

#### 5-5. まとめ差し込み（Group Merge）

宛先リストで、同じ宛先についてのエントリーが複数存在する場合に、その宛先に対して 1 通ずつ（複数回）メールを送るのではなく、内容を 1 通のメールにまとめて送信したい時には「**まとめ差し込み（Group Merge）機能**」を利用すると便利。{% endraw %}[使用例のページ]({{ site.url }}{{ site.baseurl }}/ja/add-ons/group-merge/example-of-group-merge/){% raw %}にあるように、まとめたいフィールドと個別に列挙したいフィールドをそれぞれ指定して、メールを作成できる。

初期設定では、二重の大かっこ（`[[ ]]`）で括られた文字列内の`{{フィールド}}`がまとめ差し込み（Group Merge）を行う時に個別に列挙したいフィールドとして認識され、宛先リストにある同一宛先のエントリー数分の差し込みが反復して行われる。特別なフィールド`{{i}}`は、インデックス番号を挿入したい時に使用する。

まとめ差し込み（Group Merge）は初期設定で有効になっている。まとめ差し込みフィールド`[[ ]]`が存在しないテンプレートにおいてまとめ差し込みが有効になっていたとしても、通常と同様の差し込み処理が行われるだけなので、大概は「有効」のままで問題ない。  
{% endraw %}[まとめ差し込み（Group Merge）の使用例]({{ site.url }}{{ site.baseurl }}/ja/add-ons/group-merge/example-of-group-merge/){: .btn .btn--primary .align-right}{% raw %}

### 6. 設定項目を入力する (2) - Gmail 編

Gmail のサイドパネルからアイコンをクリックすると、[4. 設定項目を入力する (1) - Google スプレッドシート編](#4-設定項目を入力する-1---googleスプレッドシート編) で記入した項目（スプレッドシート URL など）が入力された状態でサイドパネルが開く。  
![GmailサイドパネルのGroup Mergeアイコン](https://lh3.googleusercontent.com/pw/ACtC-3fxLaktUg8UZ5NdVDYlRhdaA8Fepce0b94M5pAsA3YoApvdxqFJG7g_0iIUCUECpxJumHYXvtIy_3nYMOzEchsSSMefNHDintCDSLaxJaAFBC8zCS0GgPOVr2vcDNUG1MK_c1gKOp2ExVHd8vZ9ytMN=w998-h618-no)

セクション 2「テンプレートの設定」以降を記入する。初めての方は、テンプレートとして作成した下書きメールの件名を「**テンプレートとなる下書きメールの件名**」にコピー＆ペーストするだけで、ひとまず基本的な差し込みメール作成の準備は整う。[まとめ差し込み（Group Merge）機能](#5-5-まとめ差し込みgroup-merge)は初期設定で有効になっている。  
![テンプレートとして作成した下書きメールの件名を「テンプレートとなる下書きメールの件名」にコピー＆ペーストしているスクリーンショット](https://lh3.googleusercontent.com/pw/ACtC-3eGnI8aa2iQW2jZDvLvTZTxDfu3ID0_X15gewYT42gjOCXQtaMxykLv6YsMveANuDFPJSQdKMOlMsZS_mwXFGNm2kUCOlyQkbONudSM8enZ5BQPvWKHr7M4xaMtlhgzYE003ar6HYte-yj9_pSNHIuZ=w1102-h631-no)

「高度な設定」セクションなど、設定項目の詳細については[設定](#設定)を参照のこと。

### 7. 差し込みメールの作成

前項までの設定項目と Gmail テンプレートをもとに、差し込みメールを作成。サイドメニュー最下部にあるボタン「**下書き作成（差込テスト）**」もしくは「**送信（差込メール送信）**」のいずれかを選択する。  
![「下書き作成（差込テスト）」ボタンと「送信（差込メール送信）」ボタンのスクリーンショット](https://lh3.googleusercontent.com/pw/ACtC-3cpNZA037gie2ZTd3pGIqY1ea7uFAIdSpus93oX3EdMLOv44GUXY6x5eeI6T1GWlE4URdAyIHrZfKRpFqhX8tI0DLmnEDffqaK-teRUv_zti-FSfCttcXEPXo2fGefkDZ73GU76RLaeMOHGn8RKWGQb=w1336-h748-no)

- **下書き作成（差込テスト）**：差し込み済みのメールを Gmail の下書きとして保存する。それぞれのメールについて差し込みが想定どおり行われているかなどを確認し、必要に応じて通常のメールと同じように修正・編集できる。
- **送信（差込メール送信）**：差し込みメールを作成し、直接送信する。

**Pro Tips💡**  
「下書き作成（差込テスト）」ボタンで作成したメールは、アドオンのサイドパネル上部にある「**作成済みの下書きを送信（Send Created Drafts）**」ボタンによって一括送信できます。「作成済みの下書きを送信」ボタンは、「下書き作成（差込テスト）」を実行して差し込みメールが作成されると有効になり、押下することで**直近の「下書き作成（差込テスト）」操作によって作成されたメールのみが送信される仕組みとなっています**。  
![「作成済みの下書きを送信（Send Created Drafts）」ボタンのスクリーンショット](https://lh3.googleusercontent.com/pw/ACtC-3eQ3bHLMf-nAZK4biEU0nRX8S9AQrrl5pI1pZyVO4-1LV7xk15K30UvxkeVu1rnDr0pcFai9Kp21rD-fe2SmWbEy6HO89FRz_ZNE2-TNvJKssA7alg0ci5xlxJwSGaNXOcMgKPBcXlMmBbtEha_tpZz=w762-h340-no)  
Gmail で作成される全ての下書きには draft ID という固有の文字列が付与されていて、「作成済みの下書きを送信」での送信対象となる下書きメールは、この ID によって管理しています。「下書き作成（差込テスト）」の処理が実行される都度、その時に作成された一連の下書きメールの draft ID が、アドオンに付帯する[ユーザプロパティ](https://developers.google.com/apps-script/guides/properties)に保存されます。このプロパティはユーザが「下書き作成（差込テスト）」または「送信（差込メール送信）」を実行するたびに上書きされるようになっていることから、「作成済みの下書きを送信」では常に最新の差し込み済み下書きメールのみが送信される仕組みとなっています。
{: .notice--info}

## 設定

アドオンのサイドメニューで入力する設定項目の詳細は次のとおり。

### 基本的な設定

- **スプレッドシート URL**：宛先リストとして使用する Google スプレッドシートの URL。アドオンをスプレッドシートから起動している場合、この項目は常にその時に開いているスプレッドシートの URL が自動入力される。
- **シート名**：当該スプレッドシート内で、宛先リストが記載されているシートの名前。1 行目が差込フィールド名となっていることを確認。
- **宛先メールアドレス**：宛先となるメールアドレスが記載されているフィールド（列）の名前。差し込みフィールド（merge fields）として入力する（例：`{{Email}}`）。2 つ以上の差し込みフィールドは入力できないことに注意（不可の例：`{{Email1}},{{Email2}}`）。この場合はエラーが返される。宛先によって複数の可変な送信先を設定したい場合は**CC**や**BCC**を活用する。1 つの差し込みフィールドに、複数の固定メールアドレスをカンマ区切りで入力することは可能（例：`{{Email}},fixedEmail1@example.com,fixedEmail2@example.com`）。
- \[任意\] **CC**や**BCC**：CC や BCC としてメールを送付する宛先。[Google が定める制限内](https://developers.google.com/apps-script/guides/services/quotas#current_quotas)であれば、いくらでも差し込みフィールドを入れられる（例：`{{cc1}},{{cc2}},{{cc3}}, ...`）。
- **テンプレートとなる下書きメールの件名**：テンプレートとして使用する Gmail 下書きの件名。入力した件名を持つ下書きが 2 通以上ある場合、エラーとなる。
- **まとめ差し込み（Group Merge）を有効にする**：[まとめ差し込み（Group Merge）機能](#5-5-まとめ差し込みgroup-merge)を有効にするためのスイッチ。初期設定では有効となっている。

### 高度な設定

普段は折りたたまれている、調整可能な高度な設定。

#### Reply-To

- **Reply-To 設定を有効にする**を有効にし、**Reply-To メールアドレス**に適切なメールアドレスを入力することで、それぞれの差し込みメールに Reply-To を設定できるようになる。初期設定では無効。
- **Reply-To メールアドレス**は `contact@example.com` のような固定値であったり、差し込みフィールドを使った `{{replyTo}}@example.com` のような変数とすることも可。後者の例では、受信者ごとに`replyTo`列に設定した値が、Reply-To メールアドレス（の一部）として使用される。

**❗️ 重要 ❗️**  
Reply-To を設定した上で、「**下書き作成（差込テスト）**」によって差し込み済みメールの下書きをいったん作成する人は、**[Gmail 上で通常のように「送信」ボタンを押してしまうと Reply-To 設定が無視（上書き）されてしまうことに注意](https://stackoverflow.com/questions/65878696/how-can-i-keep-the-reply-to-setting-in-gmail-drafts-created-by-gmailapp-createdr)**する。メールを送信する際は必ず、本アドオンの[「**作成済みの下書きを送信**」ボタンを使用](#7-差し込みメールの作成)すること。
{: .notice--warning}

#### データ不在時の差し込みテキスト

テンプレートでフィールドとして指定したもののそのようなフィールドが宛先リストに存在しない場合、もしくは該当するフィールドの値が空白だった場合に差し込む文字列は、任意に設定できる。初期設定では`NA`となっている。

#### フィールドマーカー

差し込みフィールドおよびまとめ差し込みフィールドのマーカーは、それぞれ設定項目である**差し込みフィールドのマーカー**および**まとめ差し込みフィールドのマーカー**にて[JavaScript の正規表現](https://developer.mozilla.org/ja/docs/Web/JavaScript/Guide/Regular_Expressions)として設定できる。バックスラッシュ（`\`）そのものはエスケープ不要。

まとめ差し込み番号マーカー`{{i}}`も、設定項目である**まとめ差し込み番号マーカー**から変更できる.

**Pro Tips💡**  
Gmail で HTML 形式を有効にしたテンプレートを作成していて、フィールドマーカーを編集する場合は、HTML 上でもマーカーが検出できることを確認しておくことをお勧めします。
{: .notice--warning}

#### デバッグモード

<!--**Under Review** この新機能を伴うアップデートは現在、Google Workspaceマーケットプレイスで掲載するためのGoogleによる審査を受けているところです。
{: .notice--info}
-->

このモードを有効にすると、差し込みメール作成に伴う各種設定や、その操作における簡単なログがアドオン上で表示されるようになる。また、差し込みが行われるたびに、ユーザは自身のメールアドレスにてその内容をメールで通知される。初期設定では無効。

{% endraw %}

### 設定の保存と呼び出し

本アドオンをサイドパネルで開く時、設定項目のほとんどは一定のルールに基づいて事前に入力されている：

1. もし保存された**ユーザ設定**が存在するならば、この設定が自動で呼び出される。
2. ユーザ設定が存在しない時、アドオンは**前回設定**を呼び出して、事前入力される。
3. **ユーザ設定**と**前回設定**がどちらも存在しないときは**初期設定**が適用される。
4. **【例外】** アドオンが Google スプレッドシートから呼び出されたときは、ユーザ設定や前回設定の存否にかかわらず、**その時に開かれているスプレッドシートの URL**が自動入力される。

各設定の定義は次のとおり：

- **ユーザ設定**：（[4. 設定項目を入力する (1) - Google スプレッドシート編](#4-設定項目を入力する-1---googleスプレッドシート編)にあるように）ユーザが最後に「**ユーザ設定として保存**」ボタンを押した時の設定。このボタンを押したことがなければ、ユーザ設定は存在しない。「**保存した設定を使用**」ボタンにより復元可能。
- **前回設定**：ユーザが最後に「**下書き作成（差込テスト）**」または「**送信（差込メール送信）**」ボタンを押して処理が完了した時の設定。完了した処理がなければ存在しない。
- **初期設定**：アドオンインストール時の初期設定。「**初期設定に戻す**」ボタンにより復元可能。

**ユーザ設定**と**前回設定**は、いずれもユーザのみが読み書き権限を持つ、アドオンの[User Properties](https://developers.google.com/apps-script/guides/properties)に保存されている。ここに保存された情報は、アドオンの開発者や他のアドオンをはじめとするユーザ以外の第三者に共有されることはない。

## 利用規約

アドオンの使用には、[利用規約（英）]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/)への同意が必要です。

### プライバシーと OAuth スコープに関する情報公開

本節は、[利用規約（Terms and Conditions）]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/)の条項「[Additional Terms（追加条件）]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/#additional-terms)」で定義されたように利用規約の追補となるものであり、このアドオンのユーザの個人情報がどこように扱われるかをより詳細に明示したものです。
{: .notice--info}

[原文を見る]({{ site.url }}{{ site.baseurl }}/add-ons/group-merge/#disclosure-on-privacy-and-oauth-scopes){: .btn .btn--primary .align-right}

## ソースコード

本アドオンのソースコードは GitHub 上で公開されています。機能追加・強化に関する要望や、バグ等の報告については GitHub 上の Issues によりご連絡ください。ソースコードに関するライセンスは、当該 GitHub レポジトリで明示しています。

[GitHub を見る](https://github.com/ttsukagoshi/mail-merge-for-gmail){: .btn .btn--primary .align-right}

## アイコンの出典

The original icon of this add-on was made by [Freepik](https://www.freepik.com) from [www.flaticon.com](https://www.flaticon.com/) and its colors are modified to fit the theme color of the app.

## 謝辞

This work was inspired by [Tutorial: Simple Mail Merge (Google Apps Script Tutorial)](https://developers.google.com/apps-script/articles/mail_merge).
