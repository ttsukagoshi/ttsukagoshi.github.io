---
permalink: /add-ons/group-merge/
title: 'Group Merge: Mail Merge for Gmail'
excerpt: Open-sourced Google Workspace add-on to send personalized emails based on Gmail template to multiple recipients. The unique Group Merge feature allows sender to group multiple contents for the same recipient in a single email.
last_modified_at: 2022-05-08T01:00:00+09:00
toc: true
published: true
---

English/[日本語]({{ site.url }}{{ site.baseurl }}/ja/add-ons/group-merge/)  
{: .align-center}

[![Get this add-on from Google Workspace Marketplace](https://img.shields.io/badge/Google%20Workspace%20Add--on-Available-green?style=flat-square)](https://workspace.google.com/marketplace/app/group_merge_mail_merge_for_gmail/586770229603) [![clasp](https://img.shields.io/badge/built%20with-clasp-4285f4.svg?style=flat-square)](https://github.com/google/clasp) [![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)  
[![CodeQL](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/codeql-analysis.yml) [![Deploy](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/deploy.yml/badge.svg)](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/deploy.yml) [![Labeler](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/label.yml/badge.svg)](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/label.yml) [![Lint Code Base](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/linter.yml/badge.svg)](https://github.com/ttsukagoshi/mail-merge-for-gmail/actions/workflows/linter.yml)

Open-sourced Google Workspace Add-on for mail merge using Gmail and Google Sheets.

**Legacy Spreadsheet Version**  
The version 1 series, a legacy version preceding the current Google Workspace Add-on versions, is no longer maintained. It is available as [a GitHub branch](https://github.com/ttsukagoshi/mail-merge-for-gmail/tree/legacy-v1.8.0-spreadsheet) together with the sample spreadsheet.
{: .notice--info}

{% raw %}

## Overview

![Group Merge icon](https://lh3.googleusercontent.com/pw/ACtC-3eZPKFkzQJvMs2P_HgJIwNRSy1OGklUpOr0gm9ncC3OGcJw-nVvNUDYta6mMWo3d57gEc9KD_KV-UNOJvcTCBjGru3MG1KUpzP3z15I-bjEfT3u1V12mzRQrcA89pzb_RoIbINO3B1WxT4qP0KefNs=s96-no){: .align-left} Send personalized emails based on Gmail template to multiple recipients using Gmail and Google Sheets. The namesake **Group Merge** feature allows the sender to group the contents of two or more rows into one email for a single recipient.

Similar to [the mail merge feature available in Microsoft Word](https://support.office.com/en-us/article/use-mail-merge-for-bulk-email-letters-labels-and-envelopes-f488ed5b-b849-4c11-9cff-932c49474705), **Group Merge** allows Gmail/Google Workspace users to send personalized emails to the recipients listed in a Google Sheets spreadsheet. Some notable features are:

- **Group Merge** feature combines contents of two or more entries for the same recipient into a single email.
- Use Gmail drafts as template for mail merge. **HTML styling**, **file attachments**, **CC & BCC recipients**, and **Gmail labels** are preserved in the personalized emails.

## How to Use

The below steps illustrate the basic flow for using this add-on, but that doesn't mean that you have to conform to it. The add-on is context-independent, i.e., it can be opened in the Gmail and Google Sheets UI regardless of which screen the user is currently seeing, be it the Gmail inbox, a particular message, drafting an email, or editing a cell in a spreadsheet. Feel free explore and find your own flow that best suits you!
{: .notice--info}

### 1. Install the Add-on

Install this add-on from [the Google Workspace Marketplace](https://workspace.google.com/marketplace/app/group_merge_mail_merge_for_gmail/586770229603). You have only to do this once per user; updates to the add-on will be automatically distributed via the Marketplace.

### 2. Create your List of Recipients

If you already have a spreadsheet listing the recipients of your email, you can continue working on it. If you don't, create a Google Sheets spreadsheet.  
![Sample view of a spreadsheet to use as recipient list](https://lh3.googleusercontent.com/pw/ACtC-3fIrGVp4uskIute2jXMV04In4ijDyxPoI8KAFAMG4l-PHfLWzHqz8HyMmsnL5vIf-SihZyn4RkJayLlSBFIbvw9asKjZgliO_xKHY3DicAFJBA_yfGprhoqWf7Ne7LUg7aGOmcDzCB9axQPoIiuHCA=w2548-h952-no){: .align-center}

1. Keep the first row of the spreadsheet as a header, i.e., the first row should be the name of each column, and nothing else.
2. The format of date & time values on the spreadsheet will be conserved during the mail merge process, i.e., the values will appear unchanged in your personalized emails.
3. Line breaks within a spreadsheet cell will be reflected in the merged mail. However, text stylings like <span style="color: red;">text colors</span> and **bold**, _italic_, and ~~strikethrough~~ letters will not. Try instead using the HTML styling available in composing the Gmail draft to use as the template for mail merge.
4. Note that non-alphanumeric letters can also be used as the header name and merge values.
5. The lower-case letter `i` is reserved as part of the Group Merge feature, as described below, and should not be used alone for a column name to avoid unexpected errors.

**Keep in mind** that the number of emails that you can send on Gmail/Google Workspace accounts is [quota-limited](https://developers.google.com/apps-script/guides/services/quotas); this add-on, or any of the Google Workspace Add-ons in fact, cannot work around this limitation.
{: .notice--warning}

### 3. Open the Group Merge add-on from Sheets Side Panel

Open the homepage card for Group Merge add-on by clicking on its icon in the Google Sheets side panel.  
![Group Merge icon in the Google Sheets side panel](https://lh3.googleusercontent.com/pw/ACtC-3ezL4YANFeGvtCQURMARrmqqCYY5uAxzFrztjhNKszO5LePgTrlJqi_MySzggICmdv04rRiONwK8AjPflkjX4Uhtgr3We-Ka4YI2l6Asjbws24DUqrvSMVY43FBTU5k7twh8RSBzG823lhoKiWdRHZy=w526-h319-no){: .align-center}  
You will see the Group Merge interface appear, like so:  
![Activated add-on side panel](https://lh3.googleusercontent.com/pw/ACtC-3evDtIezaBxpPAtlkrjm5qrrtOAd4dCAqokNB3oxxqlrWqJ0kl8dUIyNww0jW0TcUn0fyN5W4CJ8_dnGOgZyQHin-y6uTWn-Icdd4BLn3rMplV6L5u-KZcoHDd3NSi3FF59zrg3C6a3H4UvA4qGKovY=w1102-h567-no){: .align-center}

### 4. Fill in the Required Items (1) - Google Sheets View

Scroll down the side panel to fill in the required items of Section 1 (Recipient List): **Spreadsheet URL**, **Sheet Name**, and **To** recipient(s). The **CC** and **BCC** fields are optional and can be left blank.

- **Spreadsheet URL** will be pre-filled with the URL of the currently open spreadsheet if you are opening this add-on from Google Sheets, as you are if you are following this how-to-use.
- Set the **To** recipient using placeholders like `{{Email}}`. You cannot insert two or more placeholders like `{{Email1}},{{Email2}}`; this will result in an error. You can instead use the **CC** and **BCC** recipient fields to send the respective personalized emails to multiple, variable recipients. Note that inserting one recipient placeholder and adding multiple comma-seperated fixed email addresses is acceptable, as in `{{Email}},fixedEmail1@example.com,fixedEmail2@example.com`.
- \[Optional\] **CC** and **BCC** values are more flexible. You can use as many placeholders as you like, e.g., `{{cc1}},{{cc2}},{{cc3}}, ...`, as long as it's within the [Gmail's limitations](https://developers.google.com/apps-script/guides/services/quotas#current_quotas).

After filling in the three items, scroll down to the bottom of the side panel view. Click on the button that says **SAVE USER SETTINGS**.
![SAVE USER SETTINGS button](https://lh3.googleusercontent.com/pw/ACtC-3d1F8Rkr-W5IV8eSVU7yDOAxSwN3w6ek48FuIGpIYZ8QceLD8Da9nMQ0v-hmWAA_HJcgnez5ptQfvasgKExAaYg1FKUmU7NfASZqtfdg-D4d5N_e1ytzEhha1S6Zx398n3nin5K0ITcaBUUiYKVneHK=w500){: .align-center}

**Wondering about Settings?** See [Saving and Restoring Settings](#saving-and-restoring-settings) for details on how settings are saved and restored.
{: .notice--info}

### 5. Compose a Template Gmail Draft

Move on to the [Gmail UI](https://mail.google.com/mail/). Compose a draft to serve as the template.  
![Template Gmail draft](https://lh3.googleusercontent.com/pw/ACtC-3eQFoOuu3CyUzqg5nrP_kGlq6jxMcQ6sAJqc9faa7eAzbIoicoRqPV3JP82cdPylyzn8Y9a-T1jHlNjs9yVXFG7D-NkrC0Cd1oygD2orpgqwi2tgnwR_nZJlkFxytMmF2uCEYQPZg1xQ9FroUy8UOk6=w500){: .align-center}

#### 5-1. To's, CC's, BCC's, and Reply-To's

![Editing the To's, CC's, and BCC's of the template draft](https://lh3.googleusercontent.com/pw/ACtC-3dx3QJ0UDGJQRSqqCGuOXPwwm8wg6F05RnqOv7GggiIigi8az1Vyb8yMz_zlTPgPXtSz6gjgzm1Af0tHFyvj7kDfaUp495HLo9dqlyVmTUpJzytrEmYBYHTTi0GTr1grCBgC3f8ETZ9OvbW7b7xG2jx=w1020-h468-no){: .align-center}

- The **To**, **CC**, and **BCC** values of the draft should basically be left empty. Use the add-on's settings in the side panel instead. Any placeholder values, like `{{Email}}`, entered during this composition view will be ignored in the merge process. Fixed values, like the `myTeam@mydomain.com` entered in the screenshot above, will be reflected on the merged mails.
- **Reply-To** can be optionally designated via the add-on's side panel settings (but is disabled by default). See [Reply-To](#reply-to) in the Advanced Settings section.

#### 5-2. Subject and Body

You can use merge fields (placeholders) and [group merge](#5-5-group-merge) fields in the subject as well as the body of the template draft.  
![Editing the subject and body of the template draft](https://lh3.googleusercontent.com/pw/ACtC-3fHRxVSL-E7RkK_gU35V5g4sG1n7LxJ-N2j8TS1QKvwZQ1lPlXCSYj-fq2K_pLsSHwiBu_G_D16MrTeUZSVTvDNBiBpmwvQg8qiDITO3MESB3iVtZde5ue83FHsUdHdBA9Ej_FNrLgjU-U-DQFOkTMB=w1044-h761-no){: .align-center}

**The subject must be unique.** An error will be returned during the process of merging mails if there are two or more Gmail drafts with the same subject.
{: .notice--warning}

By default, the merge fields are specified by double curly brackets, as in

```
Dear {{Name}},
...
```

- The placeholders should correspond, case-sensitive, with the column names of the spreadsheet that you created in [2. Create your List of Recipients](#2-create-your-list-of-recipients).
- If an invalid placeholder is designated, e.g., a field name that does not match the column names, the field is replace by the text `NA` in the personalized emails. You can modify this replace value in the [Advanced Settings section](#replace-value).
- HTML styling will be reflected on the merged mails.

See the [Group Merge](#5-5-group-merge) section for the details on the feature to group multiple contents for the same recipient in a single email.

**Pro Tips💡**  
If you want to change the field markers, see [Field Markers](#field-markers-placeholders) in the Advanced Settings section.
{: .notice--info}

#### 5-3. File Attachments

File attachments including in-line image attachments attached to the draft will be reflected on the merged emails.  
![Sample of file and in-line image attachments](https://lh3.googleusercontent.com/pw/ACtC-3das9KldhoGPNWRQv7HEWM6-XMyjndPNfrnn1LqV18j83W8NSSntjd8gXOwSV3TQQHtP7xN4BobcgmqB3ODSnikkWA7ylhOQHtwiwPf1sJahIInoQAoShEcsW-Fq2M7RS8-ZbAeaSHZzg6-hfjyK5Pw=w1016-h632-no){: .align-center}

**Pro Tips💡**  
In-line images can only be attached if you have HTML styling enabled.
{: .notice--info}

#### 5-4. Gmail Labels

The Gmail labels that you add to the template will be copied and attached to the personalized emails as well.  
![Attaching labels to Gmail drafts](https://lh3.googleusercontent.com/pw/ACtC-3dfi3QkCBLJ7jZ0zuGYFdPTiGlMy6gdULn7xTgIUs1ih5c-bfOptMfHMMXnAuPDSdjW-lRAhf_fpLVaPGCAdcfC587fVGTMESKxpcy4ytNAZ-e2UxYefInFWLzffqbv4nlZcKA1rhtZN5hwlAs5gOzH=w1006-h576-no){: .align-center}

#### 5-5. Group Merge

In a case where there are two or more entries in your list with the same recipient, you might want to group the entries into a single email rather than sending the recipient similar emails more than once. Group merge enables you to specify which field to list individually and which to combine in an email, as shown on {% endraw %}[the example page]({{ site.url }}{{ site.baseurl }}/add-ons/group-merge/example-of-group-merge/){% raw %}.

The group merge field is, by default, marked by double square brackets, i.e., `[[Meeting ID: {{Meeting ID}}]]`. The merge fields (the curly brackets) nested inside this group merge field will be merged reclusively if there are two or more rows for the same recipient. A special index field `{{i}}` can be used inside the group merge field to indicate the index number within the group merge.

Group Merge is enabled by default. Whether Group Merge is enabled or disabled makes no in the outcomes of the add-on when group merge field `[[ ]]` is not present.  
{% endraw %}[Example of Group Merge]({{ site.url }}{{ site.baseurl }}/add-ons/group-merge/example-of-group-merge/){: .btn .btn--primary .align-right}{% raw %}

### 6. Fill in the Required Items (2) - Gmail View

Open the homepage card for Group Merge add-on by clicking on its icon in the Gmail side panel. The side panel should open with the values you entered in [4. Fill in the Required Items (1) - Google Sheets View](#4-fill-in-the-required-items-1---google-sheets-view) pre-filled.  
![Group Merge icon in the Gmail side panel](https://lh3.googleusercontent.com/pw/ACtC-3fxLaktUg8UZ5NdVDYlRhdaA8Fepce0b94M5pAsA3YoApvdxqFJG7g_0iIUCUECpxJumHYXvtIy_3nYMOzEchsSSMefNHDintCDSLaxJaAFBC8zCS0GgPOVr2vcDNUG1MK_c1gKOp2ExVHd8vZ9ytMN=w998-h618-no)

Continue to fill in the rest of the items in Section 2 (Template Draft) and after: for a starter, you should only need to fill in **Subject of Template Draft**, which you can copy & paste from the template draft that you were just editing. The [Group Merge feature](#5-5-group-merge) is enabled by default.  
![Copy and paste the subject of the template to the side panel form](https://lh3.googleusercontent.com/pw/ACtC-3eGnI8aa2iQW2jZDvLvTZTxDfu3ID0_X15gewYT42gjOCXQtaMxykLv6YsMveANuDFPJSQdKMOlMsZS_mwXFGNm2kUCOlyQkbONudSM8enZ5BQPvWKHr7M4xaMtlhgzYE003ar6HYte-yj9_pSNHIuZ=w1102-h631-no)

See the [Settings](#settings) section for details of other advanced settings.

### 7. Merge Mails

You can choose either to **CREATE DRAFTS** or directly **SEND EMAILS** based on the template from the bottom-most buttons in the side panel.
![Screenshot of Create Drafts and Send Emails button in the bottom-most part of the add-on side panel](https://lh3.googleusercontent.com/pw/ACtC-3cpNZA037gie2ZTd3pGIqY1ea7uFAIdSpus93oX3EdMLOv44GUXY6x5eeI6T1GWlE4URdAyIHrZfKRpFqhX8tI0DLmnEDffqaK-teRUv_zti-FSfCttcXEPXo2fGefkDZ73GU76RLaeMOHGn8RKWGQb=w1336-h748-no)

- **CREATE DRAFTS**: Drafts of the merged mails will be saved in your draft box. You can check to see if the mails are correctly merged in the way you intended them to be.
- **SEND EMAILS**: Directly send the merged emails.

**SEND CREATED DRAFTS button**  
You can bulk send the drafts created by the **CREATE DRAFTS** button by pressing the **SEND CREATED DRAFTS** button, located at the top of the side panel. This button will be enabled once you have created a set of merged drafts from **CREATE DRAFTS**, and on pressing, will send **only the drafts created by the _latest_ CREATE DRAFTS action**.  
![SEND CREATED DRAFTS button](https://lh3.googleusercontent.com/pw/ACtC-3eQ3bHLMf-nAZK4biEU0nRX8S9AQrrl5pI1pZyVO4-1LV7xk15K30UvxkeVu1rnDr0pcFai9Kp21rD-fe2SmWbEy6HO89FRz_ZNE2-TNvJKssA7alg0ci5xlxJwSGaNXOcMgKPBcXlMmBbtEha_tpZz=w762-h340-no)  
This is done so by saving the set of draft IDs, unique strings for each drafts of merged emails, to [User Property](https://developers.google.com/apps-script/guides/properties?hl=en). The value is overwritten every time the user executes **CREATE DRAFTS** or **SEND CREATED DRAFTS**, so only the latest drafts created will be subject to this bulk send action.
{: .notice--info}

## Settings

Details of the respective items to be filled in on the add-on side panel view can be found below:

### Basic Settings

- **Spreadsheet URL**: Full URL of the Google Sheets to use as the list of recipients. This item will be pre-filled with the URL of the currently open spreadsheet if you are opening the add-on from Google Sheets, as you will be if you are following this how-to-use steps.
- **Sheet Name**: Name of the worksheet of the recipient list, which should be `Sample List` in [the screenshot example above](#3-open-the-group-merge-add-on-from-sheets-side-panel).
- **To**: Recipient's email address. You cannot insert two or more placeholders like `{{Email1}},{{Email2}}`; this will result in an error. You can instead use the **CC** and **BCC** recipient fields to send the respective personalized emails to multiple, variable recipients. Note that inserting one recipient placeholder and adding multiple comma-seperated fixed email addresses is acceptable, as in `{{Email}},fixedEmail1@example.com,fixedEmail2@example.com`.
- **CC** and **BCC**: \[Optional\] CC and BCC recipients' email address. Use as many comma-separated placeholders as you like, e.g., `{{cc1}},{{cc2}},{{cc3}}, ...`, as long as it's within the [Gmail's limitations](https://developers.google.com/apps-script/guides/services/quotas#current_quotas).
- **Subject of Template Draft Mail**: Word-for-word copy of the template subject. Be sure to make it unique; an error will be returned if there are two or more draft messages with the same subject.
- **Enable Group Merge**: Switched on by default to enable [Group Merge](#5-5-group-merge).

### Advanced Settings

Advanced settings can be optionally tuned, folded in the collapsible section of the side panel.

#### Reply-To

- Reply-To values for each personalized mails can be set by switching on **Enable Reply-To** and entering the appropriate value under **Reply-To**. **Enable Reply-To** is switched off by default.
- The **Reply-To** value can either be a fixed value like `contact@example.com` or a value with placeholder(s) like `{{replyTo}}@example.com`. In the latter case, the respective values in the field name **replyTo** in the recipient list spreadsheet will be set for the personalized emails.

**IMPORTANT**  
If you want to combine the Reply-To settings with **CREATE DRAFTS** rather than sending the personalized mails directly via **SEND EMAILS**, note that [Reply-To settings will NOT be preserved when sending the emails via the `Send` button in the Gmail website](https://stackoverflow.com/questions/65878696/how-can-i-keep-the-reply-to-setting-in-gmail-drafts-created-by-gmailapp-createdr). You have to instead [use the **SEND CREATED DRAFTS** button](#7-merge-mails) to send the drafts.
{: .notice--warning}

#### Replace Value

The text value that will replace placeholders with empty or invalid data. Defaults to `NA`.

#### Field Markers (Placeholders)

The markers for merge fields and group merge fields can modified by adjusting the values in **Merge Field Marker** and **Group Field Marker**, respectively. You will need to be familiar with [the regular expressions of JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions). Be sure to use parentheses to denote the [capturing group](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions/Groups_and_Ranges) to mark the content of the field, i.e., the word `field` in `{{field}}`. Note that the backslash itself does not need to be escaped, i.e., does not need to be repeated.

The index field marker for group merge `{{i}}` can also be modified through the value **Row Index Marker**.

**Pro Tips💡**  
If HTML is enabled in your Gmail, make sure that your modified markers can still be detected in the HTML string.
{: .notice--warning}

#### Debug Mode

<!--**Under Review** This feature is currently under review by the Google team to be updated on the Google Workspace Marketplace.
{: .notice--info}
-->

Disabled by default, this mode visualizes the background settings and personal logs of the mail merge process for the user when enabled. Users will receive emails on the debug info sent by their own Gmail/Google Workspace account for every mail merge process that they execute.

{% endraw %}

### Saving and Restoring Settings

When opening the side panel of this add-on, the parameters, like the spreadsheet URL and sheet name, are pre-filled based on a certain rule:

1. If a saved set of **user settings** is present, this will be the set of values pre-entered.
2. If the set of **user settings** is not available, then the add-on searches for **previous settings** and pre-sets the values if present.
3. If both **user** and **previous settings** could not be found, then the add-on side panel is opened with a set of **default settings**.
4. **There is an exception** to this rule: when the add-on is opened in Google Sheets, the spreadsheet URL will always be pre-filled with **the URL of the current spreadsheet**.

The definition of the respective types of settings are as follows:

- **User Settings**: The set of parameters that were entered when the user last clicked the **SAVE USER SETTINGS** button (as in [4. Fill in the Required Items (1) - Google Sheets View](#4-fill-in-the-required-items-1---google-sheets-view)). Does not exist if the user has never clicked the button. Can be reproduced by clicking the **RESTORE USER SETTINGS** button.
- **Previous Settings**: The set of parameters that were entered when the user last executed **CREATE DRAFTS** or **SEND EMAILS**. Does not exist if the user has never completed either of the process.
- **Default Settings**: The set of parameters predefined in the add-on. Can be restored by clicking the **RESTORE DEFAULT SETTINGS** button.

**User** and **previous settings** are saved in the add-on's [User Properties](https://developers.google.com/apps-script/guides/properties?hl=en), to which only the add-on user has read and write access. The properties will not be shared with the add-on's developers, other add-ons or apps, or anyone else.

## Terms and Conditions

You must agree to the [Terms and Conditions]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/) to use this add-on.

### Disclosure on Privacy and OAuth Scopes

This section constitutes an addition to the [Terms and Conditions]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/) as defined by its [Additional Terms clause]({{ site.url }}{{ site.baseurl }}/terms-and-conditions/#additional-terms) to clarify how the user's private information is handled in this add-on.
{: .notice--info}

**Group Merge: Mail Merge for Gmail**, hereinafter referred to as the Add-on in this section, is in compliance with the [Privacy Policy]({{ site.url }}{{ site.baseurl }}/privacy-policy/) with regard to the processing of your private data, which includes the contents of your Gmail and Google Sheets files.

**Disclosure**  
The Add-on's use and transfer to any other app of information received from Google APIs will adhere to [Google API Services User Data Policy](https://developers.google.com/terms/api-services-user-data-policy#additional_requirements_for_specific_api_scopes), including the Limited Use requirements.
{: .notice--warning}

Separate from these policies, Google provides protection for the add-on users' privacy by limiting the _scope_ of authorized information that an add-on can have access to, called the [Google OAuth Scopes](https://developers.google.com/identity/protocols/oauth2/scopes). The list of OAuth Scopes that this Add-on requests from the user is as follows. As you may notice, Google does not define an authorization scope that is completely fit to the purpose and required functions of this Add-on in their [Gmail](https://developers.google.com/gmail/api/auth/scopes#gmail_scopes) and [Google Sheets](https://developers.google.com/sheets/api/guides/authorizing#OAuth2Authorizing) authorization scopes, so some of the scopes may seem broader than necessary. As a supplement to the Terms and Conditions, this is a legally binding statement that this Add-on will not process any authorized data in the manner not described in the below table:

The prefix `...` for the scopes in the table stands for `https://www.googleapis.com/auth`
{: .notice--info}

| Scope                       | Meaning                                                            | How this Add-on uses this Scope                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| --------------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `.../gmail.addons.execute`  | Execute as a Gmail add-on                                          | Open and execute this Add-on.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `.../gmail.compose`         | Create, read, update, and delete drafts. Send messages and drafts. | Create merged draft mails, and send the created drafts on behalf of the user.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `.../gmail.modify`          | View and modify but not delete your email                          | Search for the user's template Gmail draft based on its subject, read the contents of the designated template, and add label(s) that were on the template draft to the merged mail drafts.                                                                                                                                                                                                                                                                                                                                |
| `.../script.locale`         | View your locale and timezone information                          | Use your locale to provided localized side panel view and add-on messages.                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `.../script.send_email`     | Send email as you                                                  | Send email to yourself to notify debug info of the add-on. The add-on will also use this scope to notify you via email when a post-process mail merge execution is completed or terminated with an error. This post-process is triggered when a mail merge takes longer than [the 30-sec limit set for Google Workspace Add-on card actions](https://developers.google.com/workspace/add-ons/concepts/actions#callback_functions), upon which the merge will be carried over to a time-triggered background post-process. |
| `.../auth/script.scriptapp` | Execute this application on your behalf                            | Create and execute a time-triggered function for the post-process described above.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `.../spreadsheets`          | Allows read/write access to your sheets and their properties.      | Search for the spreadsheet using the URL that the user designated. Read the contents of the worksheet specified by the user by its sheet name in the spreadsheet. The only reason that this Add-on uses this broad scope rather than using `.../spreadsheets.readonly`, a read-only scope, is that Google limits the use of `SpreadsheetApp.openByUrl(url)`, the method used behind linking the URL you entered to the actual spreadsheet object, to add-ons with the authorization of the former scope.                  |
| `.../userinfo.email`        | View the user's email address                                      | Used in the UI message to confirm if the user is sending/drafting the merged mail in the account that user intended as the sender. This message appears only if the user is merging the mails from the Google Sheets UI.                                                                                                                                                                                                                                                                                                  |

<!--**Under Review** The scope(s) below are currently under review by the Google team to be updated on the Google Workspace Marketplace.
{: .notice--info}

| Scope | Meaning | How this Add-on uses this Scope |
| --- | --- | --- |
| `.../script.send_email` | Send email as you | Send email to yourself to notify debug info of the add-on. The add-on will also use this scope to notify you via email when a post-process mail merge execution is completed or terminated with an error. This post-process is triggered when a mail merge takes longer than [the 30-sec limit set for Google Workspace Add-on card actions](https://developers.google.com/workspace/add-ons/concepts/actions#callback_functions), upon which the merge will be carried over to a time-triggered background post-process. |-->

## Source Code

Source code is available on GitHub. Please make requests for enhancements or reports of bugs via the GitHub issue. License regarding the use of the code is available on the GitHub repository.

[See GitHub](https://github.com/ttsukagoshi/mail-merge-for-gmail){: .btn .btn--primary .align-right}

## Attributes

The original icon of this add-on was made by [Freepik](https://www.freepik.com) from [www.flaticon.com](https://www.flaticon.com/) and its colors are modified to fit the theme color of the app.

## Acknowledgements

This work was inspired by [Tutorial: Simple Mail Merge (Google Apps Script Tutorial)](https://developers.google.com/apps-script/articles/mail_merge).
