---
permalink: /gas-solutions/website-monitoring-by-gas/
title: Website Status Monitoring using Google Sheets
excerpt: Website Status Monitoring using Google Sheets and Google Apps Script
last_modified_at: 2022-07-04T11:15:00+09:00
toc: true
published: true
---

[![clasp](https://img.shields.io/badge/built%20with-clasp-4285f4.svg?style=flat-square)](https://github.com/google/clasp) [![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier) [![CodeQL](https://github.com/ttsukagoshi/website-monitoring-by-gas/workflows/CodeQL/badge.svg)](https://github.com/ttsukagoshi/website-monitoring-by-gas/actions?query=workflow%3ACodeQL) [![GitHub Super-Linter](https://github.com/ttsukagoshi/website-monitoring-by-gas/workflows/Lint%20Code%20Base/badge.svg)](https://github.com/marketplace/actions/super-linter) [![Publish Release](https://github.com/ttsukagoshi/website-monitoring-by-gas/actions/workflows/release.yml/badge.svg)](https://github.com/ttsukagoshi/website-monitoring-by-gas/actions/workflows/release.yml)

Website status monitoring using Google Sheets and Google Apps Script.

## About

![Screenshot of the dashboard worksheet in the Website Status Monitoring managing spreadsheet](https://lh3.googleusercontent.com/pw/AM-JKLXEoseETkZUmA6uPnRP-ozJpqDa4gHp-X06Uqcd2WxEhHIN9MFwp4e-YFsF6icsosUEWAszWrgz8z6bNucC-DuO0_BpBotOprnGer7z8fbxcxB2_34UD6YziJjfC4B88jiAgXu7XdUXvr_N88UM5XIl=w1908-h574-no)

A Spreadsheet-bound apps script solution to conduct automated status monitoring on websites listed by the user in a Google Sheets management file. A separate status log file in Google Sheets will be created so that users can easily integrate data with BI services such as Google Data Studio. Notifications of changes in website status will be sent to the user's Gmail. An optional setting to send notifications to Google Chat is available.

## Copy Sample Spreadsheet

Copy [this sample spreadsheet](https://docs.google.com/spreadsheets/d/1JvO090VcgvF-WwciNnzRb1_nonKJC5QHN73h_CXS1Cw/edit#gid=0) to your Google Drive by selecting from the menu `File` > `Make a copy`.

## How to Use

### Setup

![Screenshot of "Google hasn't verified this app"](https://lh3.googleusercontent.com/pw/AM-JKLVqrPDF5X98hwS8-JavaTuhTHt0rK1GXc0S_xtKX4O5y4FNVQTaa4fm03FVTmj8tGacF6eKsM0NkW8EepioZVtg4BMbWRt1GxJxdAGzyU5BVYPgFOYmIkmPRLGQ8097W6cX2p7e0ezEz4yRJYHgBmRH=w736-h282-no)
**Authorization** Users will be asked to authorized the script the first time they execute it. Free Gmail account users should expect to see the `Not Verified by Google` warning during this authorization process. You will have to agree with authorization to use this solution despite this warning, but please note that **the owner of the script is yourself**, and that **this solution will not send or receive any information to and from any other Google accounts or services outside the Google ecosystem** (except for checking the HTTP response codes of the websites that you designated because, well, that's what it does for status monitoring) unless you explicitly share the spreadsheet.
{: .notice--info}

| Worksheet         | To Do                                                                                                             |
| ----------------- | ----------------------------------------------------------------------------------------------------------------- |
| `01_Dashboard`    | Replace the `WEBSITE NAME` and `TARGET URL` columns with those of the website(s) that you want to monitor.        |
| `90_Spreadsheets` | Delete everything **except the first header row**.                                                                |
| `99_Options`      | Go over the parameters that you can set for this status monitoring and edit the `VALUE` items to suit your needs. |

Worksheets not listed above can be left alone; they will be updated automatically.

### Set Triggers

From the spreadsheet menu, select `Web Status` > `Triggers` > `Set Status Check Trigger`/`Set Log Extraction Trigger` to set up time-based triggers to conduct automated status checks. The latest results will be shown in the `01_Dashboard` worksheet.

### Enable Google Chat Notification

Users can optionally enable Google Chat notification that can be used with (or replace) email notifications of changes in website status. Enter the webhook URL of the Google Chat chatroom that you want the notification to be sent to. Steps to obtain this URL is described in [the official documentation by Google](https://developers.google.com/chat/how-tos/webhooks). The URL should look something like `https://chat.googleapis.com/v1/spaces/*****/messages?key=*****&token=*****`

## Updates

Updates will be distributed via [@ttsukagoshi/website-monitoring-by-gas (GitHub)](https://github.com/ttsukagoshi/website-monitoring-by-gas).

## Terms and Conditions

You must agree to the [Terms and Conditions]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/) to use this solution.

## Source Code

Source code is available on GitHub. Please make requests for enhancements or reports of bugs via the GitHub issue. License regarding the use of the code is available on the GitHub repository.

[See GitHub](https://github.com/ttsukagoshi/website-monitoring-by-gas){: .btn .btn--primary .align-right}
