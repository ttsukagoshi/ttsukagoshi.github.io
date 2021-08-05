---
permalink: /chrome-extensions/openbd-checker/
title: openBD Checker
excerpt: Check Reference Book Data Registered on openBD
last_modified_at: 2021-08-05T18:00:00+09:00
toc: true
---

![Chrome Web Store](https://img.shields.io/chrome-web-store/v/jmbcpombnleepfponcjibgeohkfcocgg) [![GitHub Super-Linter](https://github.com/ttsukagoshi/openbd-checker/workflows/Lint%20Code%20Base/badge.svg)](https://github.com/marketplace/actions/super-linter) [![Total alerts](https://img.shields.io/lgtm/alerts/g/ttsukagoshi/openbd-checker.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/ttsukagoshi/openbd-checker/alerts/)  
Check Reference Book Data Registered on openBD

![openBD Checker icon]({{ site.url }}{{ site.baseurl }}/assets/images/openBD-checker/books128.png){: .align-center}

## About

An open-source Google Chrome extension to reference the book data registered on [openBD](https://openbd.jp/) by right-clicking on an ISBN.

> openBD is a project based in Japan to make cover images and book data openly available to anyone who loves books. This extension uses its API to refer to the data. Please note that the API, and consequently this extension, is available only in the Japanese language.

## Install

This extension can be easily installed via the Chrome Web Store.

[Install](https://chrome.google.com/webstore/detail/openbd%E6%83%85%E5%A0%B1%E3%83%81%E3%82%A7%E3%83%83%E3%82%AB%E3%83%BC/jmbcpombnleepfponcjibgeohkfcocgg){: .btn .btn--primary .align-right}

## How to Use

Select an ISBN in a web page, right-click to get the context menu and select `ISBN「*****」でopenBDを検索する`.  
![Screenshot from of the context menu]({{ site.url }}{{ site.baseurl }}/assets/images/openBD-checker/screenshot_openBD_1.jpg){: .align-center}

A new tab will open with the data of the book registered in openBD, if available.
![Screenshot from of the new tab]({{ site.url }}{{ site.baseurl }}/assets/images/openBD-checker/screenshot_openBD_2.jpg){: .align-center}

### Note

- Hyphens between ISBN digits are optional; openBD Checker works with or without them.
- The openBD API accepts both ISBN-10 and ISBN-13

## Terms and Conditions

You must agree to the [Terms and Conditions]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/) and the [openBD API Terms of Use](https://openbd.jp/terms/) to use this extension.

## Source Code

Source code is available on GitHub. Please make requests for enhancements or reports of bugs via the GitHub issue. License regarding the use of the code is available on the GitHub repository.

[See GitHub](https://github.com/ttsukagoshi/openbd-checker){: .btn .btn--primary .align-right}

## About the Icon

The icon of this Chrome extension was made by [Freepik](https://www.freepik.com/) from [www.flaticon.com](https://www.flaticon.com/).

## Updates

See [Releases](https://github.com/ttsukagoshi/openbd-checker/releases) on GitHub.
