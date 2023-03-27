---
permalink: /add-ons/sheetsl/
title: 'SheetsL: DeepL&trade; Translation for Google Sheets&trade;'
excerpt: Use DeepL™ Translation without leaving Google Sheets™. The add-on that's open-sourced and FREE!
last_modified_at: 2023-03-25T02:00:00+09:00
toc: true
published: true
---

English/[日本語]({{ site.url }}{{ site.baseurl }}/ja/add-ons/sheetsl/)  
{: .align-center}

<!--
[![Get this add-on from Google Workspace Marketplace](https://img.shields.io/badge/Google%20Workspace%20Add--on-Available-green?style=flat-square)](https://workspace.google.com/marketplace/app/group_merge_mail_merge_for_gmail/586770229603) [![clasp](https://img.shields.io/badge/built%20with-clasp-4285f4.svg?style=flat-square)](https://github.com/google/clasp) [![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)
[![CodeQL](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/codeql-analysis.yml) [![Deploy](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/deploy.yml/badge.svg)](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/deploy.yml) [![Labeler](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/label.yml/badge.svg)](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/label.yml) [![Lint Code Base](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/linter.yml/badge.svg)](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/linter.yml)
-->

Open-sourced Google Sheets&trade; add-on to use DeepL translation without leaving Google Sheets&trade;. Translate the contents of the selected range and paste them in the range of cells adjacent to the original range. You need to have your own DeepL API Free or Pro account.

![SheetsL icon]({{ site.url }}{{ site.baseurl }}/assets/images/sheetsl/SheetsL_Application Card Banner_220.png)

## Prerequisite: Sign up for the DeepL API

Create a [DeepL API account](https://www.deepl.com/account). You will need its authentication key. The key can be found on [the DeepL account page](https://www.deepl.com/account/summary) once you have created the account.

![Screenshot of the DeepL API account page]({{ site.url }}{{ site.baseurl }}/assets/images/sheetsl/deepl-account-page.png)

See the following official documentations of DeepL for more details:

- [DeepL API Free vs. DeepL API Pro – DeepL Help Center](https://support.deepl.com/hc/en-us/articles/360021183620-DeepL-API-Free-vs-DeepL-API-Pro)
- [DeepL API Free – DeepL Help Center](https://support.deepl.com/hc/en-us/articles/360021200939-DeepL-API-Free)
- [Authentication Key – DeepL Help Center](https://support.deepl.com/hc/en-us/articles/360020695820-Authentication-Key)

## How to Use

### 1. Install the Add-on

This add-on is currenly going through Google's verification process. Please wait until it is available in the Google Workspace Marketplace.
{: .notice--warning}

Install this add-on from [the Google Workspace Marketplace](). You have only to do this once per user; updates to the add-on will be automatically distributed via the Marketplace.

### 2. Set your DeepL API authentication key

From the Google Sheets menu, go to Extensions > SheetsL > Settings > Set Auth Key. Enter the authentication key of your DeepL API account, which can be found in the [DeepL account page](https://www.deepl.com/account/summary).

![Screenshot of the menu in SheetsL to set the DeepL API authentication key]({{ site.url }}{{ site.baseurl }}/assets/images/sheetsl/set-auth-key.png)

See [How are my DeepL API authentication key saved in SheetsL?](#how-are-my-deepl-api-authentication-key-saved-in-sheetsl) if you are wondering how the authentication is securely saved.
{: .notice--info}

### 3. Set your target language

From the Google Sheets menu, go to Extensions > SheetsL > Settings > Set Language. You will be asked to enter the language code of your source and target languages, respectively. Choose one of the languages available in DeepL, listed in the prompt message.

While the target language must be designated, the source language can be left blank to use DeepL's language auto-detection.
{: .notice--info}

### 4. Translate

Select the range of cells that you want to be translated by DeepL. Go to Extensions > SheetsL > Translate and wait for the translated texts to be copied in an adjacent range on the right side of the original range.

![Screenshot of how the translated text will be shown on the spreadsheet]({{ site.url }}{{ site.baseurl }}/assets/images/sheetsl/source-target-ranges.png)

For example, if you selected the range `A2:B4` for translation, the translated text will appear in range `C2:D4` ("target range"). If the target range is not empty at the time of translation, you will be asked if SheetsL can overwrite the cells.
{: .notice--info}

## Frequently Asked Questions

### How are my DeepL API authentication key saved in SheetsL?

The DeepL API authentication key that you entered in [Set your DeepL API authentication key](#2-set-your-deepl-api-authentication-key) section is saved in the add-on's [User Properties](https://developers.google.com/apps-script/guides/properties?hl=en), to which only the add-on user has read and write access. The properties will NOT be shared with the add-on's developers, other add-ons or apps, users you are sharing the Google Sheets file with, or anyone else.

<!--**Under Review** This feature is currently under review by the Google team to be updated on the Google Workspace Marketplace.
{: .notice--info}
-->

## Terms and Conditions

You must agree to the [Terms and Conditions]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/) to use this add-on.

### Disclosure on Privacy and OAuth Scopes

This section constitutes an addition to the [Terms and Conditions]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/) as defined by its [Additional Terms clause]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/#additional-terms) to clarify how the user's private information is handled in this add-on.
{: .notice--info}

**SheetsL: DeepL Translation for Google Sheets&trade;**, hereinafter referred to as the Add-on in this section, is in compliance with the [Privacy Policy]({{ site.url }}{{ site.baseurl }}/privacy-policy/) with regard to the processing of your private data, which includes the contents of your Google Sheets files and the authentication information for your DeepL API account. Please note that the handling of your data by the DeepL API is outside the scope of this policy; please be sure to understand their privacy policy as well when creating your DeepL API account.

Separate from these policies, Google provides protection for the add-on users' privacy by limiting the _scope_ of authorized information that an add-on can have access to, called the [Google OAuth Scopes](https://developers.google.com/identity/protocols/oauth2/scopes). The list of OAuth Scopes that this Add-on requests from the user is as follows. As you may notice, Google does not define an authorization scope that is completely fit to the purpose and required functions of this Add-on in their [Google Sheets](https://developers.google.com/sheets/api/guides/authorizing#OAuth2Authorizing) authorization scopes, so some of the scopes may seem broader than necessary. As a supplement to the Terms and Conditions, this is a legally binding statement that this Add-on will not process any authorized data in the manner not described in the below table:

**Under Review** The scope(s) below are currently under review by the Google team to be updated on the Google Workspace Marketplace.
{: .notice--warning}

The prefix `...` for the scopes in the table stands for `https://www.googleapis.com/auth`
{: .notice--info}

| Scope                          | Meaning                                                                  | How this Add-on uses this Scope                                                                                      |
| ------------------------------ | ------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------- |
| `.../spreadsheets.currentonly` | View and manage spreadsheets that this application has been installed in | Read the contents of the range selected by the user and update the adjacent range to show the DeepL-translated text. |
| `.../script.external_request`  | Connect to an external service.                                          | Send requests to the DeepL API                                                                                       |

<!--**Under Review** The scope(s) below are currently under review by the Google team to be updated on the Google Workspace Marketplace.
{: .notice--info}

| Scope | Meaning | How this Add-on uses this Scope |
| --- | --- | --- |
| `.../script.send_email` | Send email as you | Send email to yourself to notify debug info of the add-on. The add-on will also use this scope to notify you via email when a post-process mail merge execution is completed or terminated with an error. This post-process is triggered when a mail merge takes longer than [the 30-sec limit set for Google Workspace Add-on card actions](https://developers.google.com/workspace/add-ons/concepts/actions#callback_functions), upon which the merge will be carried over to a time-triggered background post-process. |-->

## Source Code

Source code is available on GitHub. Please make requests for enhancements or reports of bugs via the GitHub issue. License regarding the use of the code is available on the GitHub repository.

[See GitHub](https://github.com/ttsukagoshi/sheetsL){: .btn .btn--primary .align-right}

## Attributes

The original icon of this add-on is the [Document icons created by Freepik - Flaticon](https://www.flaticon.com/free-icons/document), modified by [ttsukagoshi](https://github.com/ttsukagoshi).
