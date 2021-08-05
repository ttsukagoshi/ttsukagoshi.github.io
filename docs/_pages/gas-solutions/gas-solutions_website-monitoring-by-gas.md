---
permalink: /gas-solutions/website-monitoring-by-gas/
title: Website Status Monitoring using Google Sheets
excerpt: Website Status Monitoring using Google Sheets and Google Apps Script
last_modified_at: 2021-08-06T00:00:00+09:00
toc: true
published: true
---

[![GitHub Super-Linter](https://github.com/ttsukagoshi/website-monitoring-by-gas/workflows/Lint%20Code%20Base/badge.svg)](https://github.com/marketplace/actions/super-linter) [![clasp](https://img.shields.io/badge/built%20with-clasp-4285f4.svg?style=flat-square)](https://github.com/google/clasp) [![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)

Website status monitoring using Google Sheets and Google Apps Script.

## About

A Spreadsheet-bound apps script solution to conduct automated status monitoring on websites listed by the user in a Google Sheets management file. A separate status log file in Google Sheets will be created so that users can easily integrate data with BI services such as Google Data Studio.

## Install

Copy [this sample spreadsheet](https://docs.google.com/spreadsheets/d/1JvO090VcgvF-WwciNnzRb1_nonKJC5QHN73h_CXS1Cw/edit#gid=0) to your Google Drive.

## How to Use

### Setup

**Authorization** Users will be asked to authorized the script the first time they execute it. Free Gmail account users should expect to see the `Not Verified by Google` warning during this authorization process. You will have to agree with authorization to use this solution despite this warning, but please note that **the owner of the script is yourself**, and that **this solution will not send or receive any information to and from any other Google accounts or services outside the Google ecosystem** (except for checking the HTTP response codes of the websites that you designated because, well, that's what it does for status monitoring) unless you explicitly share the spreadsheet.
{: .notice--info}

| Worksheet         | To Do                                                                                                             |
| ----------------- | ----------------------------------------------------------------------------------------------------------------- |
| `01_Dashboard`    | Replace the `WEBSITE NAME` and `TARGET URL` columns with those of the website(s) that you want to monitor.        |
| `90_Spreadsheets` | Delete everything **except the first header row**.                                                                |
| `99_Options`      | Go over the parameters that you can set for this status monitoring and edit the `VALUE` items to suit your needs. |

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
