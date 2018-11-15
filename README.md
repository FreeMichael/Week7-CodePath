# Week7-CodePath

# Project 7 - WordPress Pentesting

Time spent: **X** hours spent in total

> Objective: Find, analyze, recreate, and document **three vulnerabilities** affecting an old version of WordPress

## Pentesting Report


1. Authenticated Stored Cross-Site Scripting via Image Filename
  - [ ] Summary: By inserting javascript infront of filename of image when the file is uploaded and the image is selected the script will run. This is due to Word Press not filtering javascript in the filenames text when an image is uploaded.
    - Vulnerability types: Cross Site Scripting (XSS)
    - Tested in version: 4.2
    - Fixed in version: 4.0.13
  - [ ] GIF Walkthrough: https://gfycat.com/anothersorrowfulfritillarybutterfly
  - [ ] Steps to recreate: Include script <img src=a onclick=alert("Oh_Baby_a_Triple!")> infront of the .img
  - [ ] Affected source code: 
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
2. Authenticated Stored Cross-Site Scripting
  - [ ] Summary: By inserting malicious javascript (“<a title='x onclick=alert(unescape(/Pwned/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px "64kb characters"><a>") in the comment section followed by 64kb of characters, this creates a buffer overflow that allows the script to run when on the Post's page.
    - Vulnerability types: Cross Site Scripting (XSS)
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [ ] GIF Walkthrough: https://gfycat.com/CriminalWhichDoctorfish
  - [ ] Steps to recreate: Add the javascript in the comment section and after posting the comment click the page to activate XSS onclick.
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



## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [giphy](https://giphy.com/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [2018] [Michael Freeman]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
