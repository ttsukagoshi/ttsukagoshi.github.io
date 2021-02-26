---
permalink: /chrome-extensions/imgsrc-er/
title: ImgSrc-er
excerpt: Convert image link URL into an `<img>` tag
last_modified_at: 2021-01-12T00:00:00+09:00
toc: true
---

![Chrome Web Store](https://img.shields.io/chrome-web-store/v/mmalpdcdmbloijpgoagaeallfnmioika) [![GitHub Super-Linter](https://github.com/ttsukagoshi/chrome-ext_ImgSrc-er/workflows/Lint%20Code%20Base/badge.svg)](https://github.com/marketplace/actions/super-linter) [![Total alerts](https://img.shields.io/lgtm/alerts/g/ttsukagoshi/chrome-ext_ImgSrc-er.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/ttsukagoshi/chrome-ext_ImgSrc-er/alerts/)  
Convert image link URL into an `<img>` tag

![Image Sourcer icon]({{ site.url }}{{ site.baseurl }}/assets/images/ImgSrc-er/ImgSrc-er128.png){: .align-center}

## About
An open-source Google Chrome extension to convert selected image link URL into an HTML `<img>` tag with `src` attribute on the clipboard.

## Install
This extension can be easily installed via the Chrome Web Store.  

[Install](https://chrome.google.com/webstore/detail/imgsrc-er/mmalpdcdmbloijpgoagaeallfnmioika){: .btn .btn--primary .align-right}

## How to Use
When an image, e.g., `https://example.com/image.jpg`, is selected, right-click to get the context menu and select `Convert to <img> tag and save on clipboard`.  
![Screenshot from of the context menu]({{ site.url }}{{ site.baseurl }}/assets/images/ImgSrc-er/screenshot_ImgSrc-er.jpg){: .align-center}  
The string
```html
<img src="https://example.com/image.jpg" alt="">
```
will be saved on the clipboard. You can in turn use this to edit your website.

## Terms and Conditions
You must agree to the [Terms and Conditions]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/) to use this extension.

## Source Code
Source code is available on GitHub. Please make requests for enhancements or reports of bugs via the GitHub issue. License regarding the use of the code is available on the GitHub repository.  

[See GitHub](https://github.com/ttsukagoshi/chrome-ext_ImgSrc-er){: .btn .btn--primary .align-right}

## About the Icon
The icon of this Chrome extension was made by [Freepik](https://www.freepik.com/) from [www.flaticon.com](https://www.flaticon.com/).
