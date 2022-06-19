---
permalink: /add-ons/unshare/
title: 'Unshare'
excerpt: Open-sourced Google Workspace Add-on to "un"share Google Drive files that you own with a tap.
last_modified_at: 2022-06-20T03:00:00+09:00
toc: true
published: true
---

<!--English/[日本語]({{ site.url }}{{ site.baseurl }}/ja/add-ons/unshare/)
{: .align-center}-->

<!--[![Get this add-on from Google Workspace Marketplace](https://img.shields.io/badge/Google%20Workspace%20Add--on-Available-green?style=flat-square)](https://workspace.google.com/marketplace/app/group_merge_mail_merge_for_gmail/586770229603)-->

[![clasp](https://img.shields.io/badge/built%20with-clasp-4285f4.svg?style=flat-square)](https://github.com/google/clasp) [![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)  
[![Lint Code Base](https://github.com/ttsukagoshi/unshare/actions/workflows/linter.yml/badge.svg)](https://github.com/ttsukagoshi/unshare/actions/workflows/linter.yml) [![CodeQL](https://github.com/ttsukagoshi/unshare/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/ttsukagoshi/unshare/actions/workflows/codeql-analysis.yml) [![Deploy](https://github.com/ttsukagoshi/unshare/actions/workflows/deploy.yml/badge.svg)](https://github.com/ttsukagoshi/unshare/actions/workflows/deploy.yml)

Open-sourced Google Workspace Add-on to "un"share Google Drive files that you own with a tap.

## Overview

![Unshare icon](https://lh3.googleusercontent.com/pw/AM-JKLUeE_Ws9D1PaPh9_8CVmjpbscs1hQc8viJ_eBoZQ6OdolI3GyNrfAoWAy3w7hhvM2NSWY1EdFLsvCu2j5U7gtExx7Ou5uEctsImUiIvzDlKFRJl0LwRVqBMD7j2FHAiIsfS0-Vy7aFn5kaDh4MSvXZ4=s96-no){: .align-left} Unshare is a Google Workspace Add-on to bulk remove all editors, commenters, and viewers from the selected Google Drive file/folder except for you, the owner. If the target file/folder is shared with a class of users who have general access, for example, if it is shared with the user's domain, that access setting will be changed to Private, where only the users explicitly granted permission can access.

## How to use

### 1. Install the add-on

Install this add-on from the Google Workspace Marketplace. You have only to do this once per user; updates to the add-on will be automatically distributed via the Marketplace.

This add-on is currently under review by Google. It will be made available on the Google Workspace Marketplace as soon as the verification is complete.
{: .notice--warning}

### 2. Select target file/folder(s)

Select the files and folders that you want to "un"share. Click on the add-on's icon on the right side and follow the instructions. That's it!

You can also use this add-on by opening independent files on Google Docs, Sheets, and Slides.
{: .notice--info}

## Terms and Conditions

You must agree to the [Terms and Conditions]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/) to use this add-on.

### Disclosure on Privacy and OAuth Scopes

This section constitutes an addition to the [Terms and Conditions]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/) as defined by its [Additional Terms clause]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/#additional-terms) to clarify how the user's private information is handled in this add-on.
{: .notice--info}

**Unshare**, hereinafter referred to as the Add-on in this section, is in compliance with the [Privacy Policy]({{ site.url }}{{ site.baseurl }}/privacy-policy/) with regard to the processing of your private data, which includes the contents of your Google Drive files.

Separate from this policy, Google provides protection for the add-on users' privacy by limiting the _scope_ of authorized information that an add-on can have access to, called the [Google OAuth Scopes](https://developers.google.com/identity/protocols/oauth2/scopes). The list of OAuth Scopes that this Add-on requests from the user is as follows. As you may notice, Google does not define an authorization scope that is completely fit to the purpose and required functions of this Add-on in their [Drive API](https://developers.google.com/identity/protocols/oauth2/scopes#drive) authorization scopes, so some of the scopes may seem broader than necessary. As a supplement to the Terms and Conditions, this is a legally binding statement that this Add-on will not process any authorized data in the manner not described in the below table:

The prefix `...` for the scopes in the table stands for `https://www.googleapis.com/auth`
{: .notice--info}

| Scope                                | Description                                                                           | How this Add-on uses this Scope                                                                                |
| ------------------------------------ | ------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `.../documents.currentonly`          | View and manage documents that this application has been installed in                 | View and edit the sharing status of the Google Docs document that this add-on is executed on                   |
| `.../drive`                          | See, edit, create, and delete all of your Google Drive files                          | Change the sharing status of the selected Google Drive files/folders by calling the `File.setSharing()` method |
| `.../drive.addons.metadata.readonly` | View basic data about the Google Drive folders or files you select                    | Get the owner, editors, and viewers of the selected folders and files                                          |
| `.../presentations.currentonly`      | View and manage the Google Slides presentations that this application is installed in | View and edit the sharing status of the Google Slides presentation that this add-on is executed on             |
| `.../script.locale`                  | View your country, language, and timezone                                             | Use your locale to provide localized side panel view and add-on messages.                                      |
| `.../spreadsheets.currentonly`       | View and manage spreadsheets that this application has been installed in              | View and edit the sharing status of the Google Sheets spreadsheet that this add-on is executed on              |
| `.../userinfo.email`                 | See your primary Google Account email address                                         | User your email address as the key to determine whether you are the selected file/folders' owner               |

<!--**Under Review** The scope(s) below are currently under review by the Google team to be updated on the Google Workspace Marketplace.
{: .notice--info}-->

## Source Code

Source code is available on GitHub. Please make requests for enhancements or reports of bugs via the GitHub issue. License regarding the use of the code is available on the GitHub repository.

[See GitHub](https://github.com/ttsukagoshi/unshare){: .btn .btn--primary .align-right}
