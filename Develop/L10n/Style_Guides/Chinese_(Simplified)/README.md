---
title: Chinese_(Simplified)
permalink: Develop/L10n/Style_Guides/Chinese_(Simplified)/

---

# Grammar

## Tense

Use the present tense.  
For example:

  - Correct: Media player selects songs: **媒体播放器会选择歌曲**
  - Incorrect: Media player will select songs: **媒体播放器将选择歌曲**

Follow the tense of the source language.  
For example: Configuring your system...: **正在配置系统...**

For example:

  - Correct: Create Account Setting: **创建帐户设置**
  - Incorrect: Account Settings are created: **帐户设置被创建**

For example:

  - Correct: Go to Settings: **转到“设置”**
  - Incorrect: User goes to Settings: **用户转到“设置”**

# Punctuation

In Chinese, always use the double-byte punctuation.

## Plurals

Change the plural form of abbreviations to the singular one.  
For example: This product is shipped with several CD-ROMs: **本产品随带了若干个
CD-ROM。**

# Numerals

For example:

  - Correct:1 message received: **收到了 1 条消息。**
  - Incorrect: One message received: **收到了一条消息。**

# Terminology

## Politically sensitive information

Please handle them as follows:

  - country: **国家/地区**
  - Taiwan: **中国台湾**
  - Hong Kong: **中国香港**
  - Macao: **中国澳门**

# Special instructions for the UI

<table>
<thead>
<tr class="header">
<th><p>Punctuation</p></th>
<th><p>Format</p></th>
<th><p>Spacing</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>full stop</p></td>
<td><p>double-byte</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>comma</p></td>
<td><p>double-byte</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>parentheses</p></td>
<td><p>single-byte</p></td>
<td><p>No space between it and the adjacent Chinese characters.</p>
<p>A space between it and the adjacent English characters.</p></td>
</tr>
<tr class="even">
<td><p>double quotation mark</p></td>
<td><p>double-byte</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>colon</p></td>
<td><p>single-byte</p></td>
<td><p>A space between it and the character after it.</p></td>
</tr>
<tr class="even">
<td><p>question mark</p></td>
<td><p>single-byte</p></td>
<td><p>No space between it and the Chinese character before it.</p>
<p>A space between it and the sentence after it.</p></td>
</tr>
<tr class="odd">
<td><p>ellipsis</p></td>
<td><p>single-byte</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>exclamation mark</p></td>
<td><p>single-byte</p></td>
<td><p>No space between it and the Chinese character before it.</p>
<p>A space between it and the sentence after it.</p></td>
</tr>
</tbody>
</table>

Use single-byte parentheses to enclose shortcut keys and leave no space
between Chinese characters and parentheses. For example:

  - \&File: **文件(\&F)**
  - About \&ABC: **关于 ABC(\&A)**
  - &50%: **50%(&5)**
  - \&Font…: **字体(\&F)…**
  - Le\&ft: **左(\&F)**

# Special instructions for technical writing

When translating UIs in documentation (or other technical writing),
always follow its terminology for consistency.

Spacing rules:

  - There should be a space between Chinese characters and single-byte
    characters (such as English characters, numbers and single-byte
    punctuation).
  - There should be no space before and after double-byte punctuation,
    including Chinese parentheses.

Please see the table below for UI reference format (source:
<http://www.ccjk.com/common-rule-on-translation>):

| Item                                                             | Format                                                                   | Example                                             |
| ---------------------------------------------------------------- | ------------------------------------------------------------------------ | --------------------------------------------------- |
| Menu name                                                        | Use double-byte double quotation mark                                    | The File menu                                       |
| Command name                                                     | The Page Setup command                                                   | “页面设置”命令                                            |
| Dialog box title                                                 | The Options dialog box                                                   | “选项”对话框                                             |
| Tab name                                                         | The View tab                                                             | “视图”选项卡                                             |
| Option name                                                      | The Portrait option                                                      | “纵向”选项                                              |
| Button name                                                      | The Cancel button                                                        | “取消”按钮                                              |
| List box name                                                    | The File of Type list box                                                | “文件类型”列表框                                           |
| List box content                                                 | Choose Arial from the Font list box.                                     | 从“字体”列表框中选择“Arial”。                                 |
| Text box name                                                    | The Password text box                                                    | “口令”文本框                                             |
| Check box name                                                   | The Read Only check box                                                  | “只读”复选框                                             |
| Radio button name                                                | The None radio button                                                    | “无”单项选择按钮                                           |
| UIs that are enclosed with format tags (such as bold and italic) | Follow the source format and don’t use double-byte double quotation mark | Click \<b\>Close\</b\> button                       |
| Press \<:cs "Helvetica9ptBold" 1\>CALL/ANSWER\<:/cs\>            | 按\<:cs "Helvetica9ptBold" 1\>呼叫/应答\<:/cs\>。                              |                                                     |
| Window name                                                      | Use double-byte double quotation mark                                    | The Print window                                    |
| Window (general description)                                     | Don’t use double-byte double quotation mark                              | In the document window                              |
| Manual name                                                      | Use double-byte book title mark                                          | See Chapter 6 in the User's Guide.                  |
| Chapter and appendix                                             | Use double-byte double quotation mark                                    | See "To Copy files" in chapter 2, "Managing files." |
