# FAQ

## What does SingleFile do?
SingleFile is a browser extension designed to help users save web pages as complete, self-contained files. The extension's primary function is to capture an entire web page, including its HTML, CSS, JavaScript, images, and other resources, and package them into a single HTML file.

## I am a web archivist, is it ok to use SingleFile to archive content?
No, SingleFile is not a tool used by professionals to archive content on the Web, especially in the academic field. Professionals prefer to rely on tools based on the [WARC specification](https://iipc.github.io/warc-specifications/) instead. 

## Does SingleFile upload any data to third-party servers?
As stated in the [privacy policy](https://github.com/gildas-lormeau/SingleFile/blob/master/privacy.md), SingleFile does not upload any data to third-party servers. All the work is done in your browser. However, when you save a page with SingleFile, it can download resources (images, CSS, frame contents, fonts etc.) that are not displayed or not already cached but present in the page.

## Why can't I save some pages like https://addons.mozilla.org/addon/single-file?
For security purposes, browsers block web extensions on certain domains. This prevents a malicious extension to remove or change bad reviews, for example.

## Why aren't images saved on sites like sspai.com or weibo.com?
These sites require the HTTP header "referer" to be present in order to download images.  For privacy reasons, this feature is not enabled by default in SingleFile. To enable it, you need to check the option "Network > pass "Referer" header after a cross-origin request error".

## Why don't interactive elements like folding titles, dynamic maps or carousels work properly in saved pages?
These elements need JavaScript to work properly. By default, SingleFile removes scripts because they can alter the rendering and there is no guarantee they will work offline. However, you can save them by unchecking the option "Network > blocked resources > scripts", and optionally  unchecking "HTML Content > remove hidden elements", unchecking "Stylesheets > remove unused styles", and checking the option "HTML content > save raw page".

## Why isn't the infobar displayed / Why cannot I save a page from the filesystem in Chrome?
By default, Chrome extensions are not allowed to access to pages stored on the filesystem. Therefore, you must enable the option "Allow access to file URLs" in the extension page to display the infobar when viewing a saved page, or to save a page stored on the filesystem.

## How does the self-extracting ZIP format work?
The self-extracting ZIP files created by SingleFile are essentially regular ZIP files. They take advantage of the flexibility in the ZIP specification, which allows for additional data to be included before and after the ZIP payload. See this [presentation](https://github.com/gildas-lormeau/Polyglot-HTML-ZIP-PNG) for more info.

## What are the permissions requested by SingleFile for?
The permissions requested by SingleFile are defined in the [manifest.json](https://github.com/gildas-lormeau/SingleFile/blob/master/manifest.json) file. Below are the reasons why they are necessary.
 - `identity`: allows SingleFile to connect to your Google Drive account.
 - `storage`: allows SingleFile to store your settings.
 - `menus/contextMenus`: allows SingleFile to display an entry in the context menu of web pages.
 - `tabs` (all_urls): allows SingleFile to inject the code needed to process a page in any tab. This permission is needed for saving several tabs in one click, for example.
 - `downloads`: allows SingleFile to save pages as if they were downloaded from the web.
 - `clipboardWrite`: allows SingleFile to copy the content of a page into the clipboard instead of saving it.
 - `nativeMessaging`: allows you to use [SingleFile Companion](https://github.com/gildas-lormeau/single-file-companion) to save pages.

## SingleFile is slow on my computer/tablet/phone, can it run faster?
The default configuration of SingleFile is optimized to produce small pages. This can sometimes slow down the save process considerably. Below are the options you can disable to save time and CPU.
 - HTML content > remove hidden elements
 - Stylesheets > remove unused styles

You can also disable the options below. Some resources (e.g. images, frames) on the page may be missing though.
 - HTML content > remove frames
 - Images > save deferred images
