# Project 7 - WordPress Pentesting

Time spent: **1** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) Vulnerability Name or ID: Authenticated Stored Cross-Site Scripting via Image Filename
  - [x] Summary: Cross-site scripting (XSS) vulnerability in the media_handle_upload function in wp-admin/includes/media.php in WordPress before 4.6.1 might allow remote attackers to inject arbitrary web script or HTML by tricking an administrator into uploading an image file that has a crafted filename.

    - Vulnerability types: XSS
    - Tested in version: 4.2.2
    - Fixed in version: 4.6.1
  - [x] GIF Walkthrough: 

<img src='https://github.com/sammanthp007/WordPress-Pentesting/blob/master/walkthrough1.gif' title='Video Walkthrough' width='' alt='Video Walkthrough' />

GIF created with [Byzanz](https://github.com/GNOME/byzanz).

  - [x] Steps to recreate: 
    1. A WordPress admin uploads a malicious image file requested by a user this admin trusts or a popular malicious image that was spread via social media in the form of "attachment page". This involves social engineering. In the Proof of Concept the file name ```<img src=a onerror=alert(document.cookie)>.jpg``` was used.
    2. Whenever the attachment file is opened in its own page, xss expolited script is run.
  
  - [x] Affected source code:
    - [github link](https://github.com/WordPress/WordPress/commit/c9e60dab176635d4bfaaf431c0ea891e4726d6e0)


2. (Required) Vulnerability Name or ID
  - [x] Summary: 
    Title: WordPress  4.0-4.7.2 - Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds
    Reference: https://wpvulndb.com/vulnerabilities/8768
    Reference: https://wordpress.org/news/2017/03/wordpress-4-7-3-security-and-maintenance-release/
    Reference: https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8
    Reference: https://blog.sucuri.net/2017/03/stored-xss-in-wordpress-core.html
    Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-6817

    - Vulnerability types:
    - Tested in version: 4.1.1
    - Fixed in version: 4.1.16
  - [x] GIF Walkthrough: 

<img src='https://github.com/sammanthp007/WordPress-Pentesting/blob/master/walkthrough2.gif' title='Video Walkthrough' width='' alt='Video Walkthrough' />

GIF created with [Byzanz](https://github.com/GNOME/byzanz).

  - [x] Steps to recreate: 
    * Create a new post
    * Edit as text
    * Put: `[embed src='http://youtube.com/embed/12345\x3csvg onload=alert(hcked)\x3e'][/embed]`

  - [x] Affected source code:
    - [github link](https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8)


3. (Required) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
1. (Optional) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
1. (Optional) Vulnerability Name or ID
  - [ ] Summary: 
    - Vulnerability types:
    - Tested in version:
    - Fixed in version: 
  - [ ] GIF Walkthrough: 
  - [ ] Steps to recreate: 
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php) 

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [yyyy] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
