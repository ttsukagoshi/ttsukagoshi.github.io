---
permalink: /add-ons/group-merge/example-of-group-merge/
title: "Group Merge: Example of Group Merge"
excerpt: An example of how the group merge feature of the add-on Group Merge works
last_modified_at: 2021-02-22T22:00:00+09:00
toc: true
published: true
---

This is a page to illustrate how group merging works in the Google Workspace Add-on **Group Merge**.  
[Go back to Group Merge]({{ site.url }}{{ site.baseurl }}/add-ons/group-merge/){: .btn .btn--primary .align-right}

## Sample List of Recipients
Given a list of email addresses below:

| Email | Name | Meeting ID | Date | Start Time | End Time |
| :--- | :---: | :---: | :---: | :---: | :---: |
|`john@example.com`|John|00001|May 7, 2020|13:00|14:00|
|`mary@sample.com`|Mary|00002|May 7, 2020|14:30|15:30|
|`john@example.com`|John|00003|May 8, 2020|9:00|10:00|

{% raw %}
## Sample Template
And a Gmail draft with the below text as its body:  
```
Dear {{Name}},

Thank you for your application.
Details of your meeting are as below:

[[
Meeting No. {{i}}
Date: {{Date}}
Time Slot: {{Start Time}} – {{End Time}}
Meeting ID: {{Meeting ID}}

]]

We look forward to seeing you!
```

## Outcome
The personalized emails using group merge will look like this:

### Email to John
```
Dear John,

Thank you for your application.
Details of your meeting are as below:

Meeting No. 1
Date: May 7, 2020
Time Slot: 13:00 – 14:00
Meeting ID: 00001

Meeting No. 2
Date: May 8, 2020
Time Slot: 9:00 – 10:00
Meeting ID: 00003

We look forward to seeing you!
```

### Email to Mary
```
Dear Mary,

Thank you for your application.
Details of your meeting are as below:

Meeting No. 1
Date: May 7, 2020
Time Slot: 14:30 – 15:30
Meeting ID: 00002

We look forward to seeing you!
```
{% endraw %}