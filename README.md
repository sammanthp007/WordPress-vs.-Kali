# Project 7 - WordPress Pentesting

Time spent: **8** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. Authenticated Stored Cross-Site Scripting via Image Filename
    - [x] Summary: Cross-site scripting (XSS) vulnerability in the media_handle_upload function in wp-admin/includes/media.php in WordPress before 4.6.1 might allow remote attackers to inject arbitrary web script or HTML by tricking an administrator into uploading an image file that has a crafted filename.
    - Vulnerability types: XSS
    - Tested in version: 4.2.2
    - Fixed in version: 4.6.1
    - [x] GIF Walkthrough: 
   
   <img src='https://github.com/sammanthp007/WordPress-Pentesting/blob/master/walkthrough1.gif' title='Video Walkthrough' width='' alt='Video Walkthrough' />
    GIF created with [Byzanz](https://github.com/GNOME/byzanz).

    - [x] Steps to recreate: 
        1. A WordPress admin uploads a malicious image file requested by a user this admin trusts or a popular malicious image that was spread via social media in the form of "attachment page".
        This involves social engineering. In the Proof of Concept the file name `<img src=a onerror=alert(document.cookie)>.jpg` was used.
        2. Whenever the attachment file is opened in its own page, xss expolited script is run.
    
    - [x] Affected source code:
        - [github link](https://github.com/WordPress/WordPress/commit/c9e60dab176635d4bfaaf431c0ea891e4726d6e0)

---

2. WordPress  4.0-4.7.2 - Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds
    - [x] Summary: 
        1. Reference: https://wpvulndb.com/vulnerabilities/8768
        2. Reference: https://wordpress.org/news/2017/03/wordpress-4-7-3-security-and-maintenance-release/
        3. Reference: https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8
        4. Reference: https://blog.sucuri.net/2017/03/stored-xss-in-wordpress-core.html
        5. Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-6817
    - Vulnerability types: XSS
    - Tested in version: 4.1.1
    - Fixed in version: 4.1.16
    - [x] GIF Walkthrough: 

    <img src='https://github.com/sammanthp007/WordPress-Pentesting/blob/master/walkthrough2.gif' title='Video Walkthrough' alt='Video Walkthrough' />
    GIF created with [Byzanz](https://github.com/GNOME/byzanz).

    - [x] Steps to recreate: 
        1. Create a new post
        2. Edit as text
        3. Put: ` [embed src='http://youtube.com/embed/12345\x3csvg onload=alert(hacked)\x3e'][/embed] `

    - [x] Affected source code:
        - [github link](https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8)
---

3. (Required) 
Title: 
    Reference: https://wpvulndb.com/vulnerabilities/8186
    
    
[i] Fixed in: 4.1.8

  - [x] Summary: WordPress <= 4.3 - Authenticated Shortcode Tags Cross-Site Scripting (XSS)
        1. Reference: https://wpvulndb.com/vulnerabilities/8186
        2. Reference: https://wordpress.org/news/2015/09/wordpress-4-3-1/
        3. Reference: http://blog.checkpoint.com/2015/09/15/finding-vulnerabilities-in-core-wordpress-a-bug-hunters-trilogy-part-iii-ultimatum/
        4. Reference: http://blog.knownsec.com/2015/09/wordpress-vulnerability-analysis-cve-2015-5714-cve-2015-5715/
        5. Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-5714
    - Vulnerability types:
    - Tested in version: 4.1.1
    - Fixed in version: 4.3.1
  - [x] GIF Walkthrough: 

    <img src='https://github.com/sammanthp007/WordPress-Pentesting/blob/master/walkthrough3.gif' title='Video Walkthrough' alt='Video Walkthrough' />
    GIF created with [Byzanz](https://github.com/GNOME/byzanz).

  - [x] Steps to recreate: 
    1. Create a post with the following shortcode:
    ```
    TEST!!![caption width="1" caption='<a href="' ">]</a><a href="http://onMouseOver='alert(1)'">Click me</a>
    ```
  - [x] Affected source code:
    - [github link](https://github.com/WordPress/WordPress/commit/f72b21af23da6b6d54208e5c1d65ececdaa109c8)

---

4. (Optional: FAILED attempt) 
  - [x] Summary: Title: WordPress 3.4-4.7 - Stored Cross-Site Scripting (XSS) via Theme Name fallback
        1. Reference: https://wpvulndb.com/vulnerabilities/8718
        2. Reference: https://www.mehmetince.net/low-severity-wordpress/
        3. Reference: https://wordpress.org/news/2017/01/wordpress-4-7-1-security-and-maintenance-release/
        4. Reference: https://github.com/WordPress/WordPress/commit/ce7fb2934dd111e6353784852de8aea2a938b359
        5. Reference: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5490
    - Vulnerability types:
    - Tested in version: 4.1.1
    - Fixed in version: 4.1.15
  - [x] GIF Walkthrough: 
  - [x] Steps to recreate: 
    1. Download any theme as zip
    2. Unzip the theme and perform the following changes in style.css:
        ```
        Theme Name: &lt;svg onload=alert(1)&gt;
        ... DO NOT CHANGES HERE ...
        ```
    3. Change the directory name to `"&lt;svg onload=alert(1)&gt;"`
    4. Compress the theme
    5. Login as administrator with administrator credential
    6. upload the theme

  - [x] Affected source code:
    - [github link](https://github.com/WordPress/WordPress/blob/dd6da701b286579819cd6aa518aa2d7018efd759/wp-admin/includes/class-theme-installer-skin.php)

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
