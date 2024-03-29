---
layout: post
title: "Amping-Up Windows Command Prompt with cURL and JQ"
author: anantharajuc
categories: [ cURL, JQ, CMD, CLI, Windows ]
tags: [ cURL, JQ, CMD, CLI, Windows ]
date: 2018-10-09 17:40
image: /assets/images/curl-logo.svg
---

<a href="https://curl.haxx.se/" target="_blank" >cURL</a> stands for **Client URL**. It is a command-line tool for getting or sending files using URL syntax. cURL uses libcurl and supports a range of common Internet protocols, currently including HTTP, HTTPS, FTP, FTPS, SCP, SFTP, TFTP, LDAP, DAP, DICT, TELNET, FILE, IMAP, POP3, SMTP and RTSP.

<a href="https://stedolan.github.io/jq/" target="_blank" >jq</a> is a lightweight and flexible command-line JSON processor. It can be used to slice and filter and map and transform structured data. it is available for use on Linux, OS X, FreeBSD, Solaris and Windows OS platforms.

#### Classification

- [cURL Installation](#curl-installation)
- [cURL Commands](#curl-commands)
- [jq Installation](#jq-installation)
- [jq Commands](#jq-commands)
- [Resources](#resources)

#### cURL Installation

- In the *Source Archives* section of the **<a href="https://curl.haxx.se/download.html" target="_blank" >Download</a>** page on the **<a href="https://curl.haxx.se/" target="_blank" >curl://</a>** website, click on the zip file to download the most recent version of the curl release.
- Extract the zip file and navigate to the **`bin`** folder and add this folder location to **`Path`** system variable

#### cURL Commands

- To test if the tool is configured correctly, open the command prompt and execute the command **`curl https://postman-echo.com/get?test=123`**
- Correct configuration of the tool will return the following response 

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/curl-example.PNG" /></div>

- cURL can also be used with a web URL, **`curl www.example.com`**

- **`-o`** flag can be used to store the output in a file **`curl -o example.html www.example.com`**

#### jq Installation

- jq can be installed on the Windows operating system platforma via <a href="https://chocolatey.org/" target="_blank" >Choclatey</a> package manager for Windows or by downloading the <a href="https://stedolan.github.io/jq/download/" target="_blank" >executables</a>.

#### jq Commands

- To pretty print the JSON response append **` | jq`** to the command. Example **`curl https://postman-echo.com/get?test=123 | jq`**

<div style="text-align:center"><img src="{{ site.baseurl }}/assets/images/curl-example-pretty-print.PNG" /></div>

```
{
  "args": {
    "test": "123"
  },
  "headers": {
    "host": "postman-echo.com",
    "accept": "text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8",
    "accept-encoding": "gzip, deflate, br",
    "accept-language": "en-US,en;q=0.9",
    "cookie": "sails.sid=s%3ADexAdKWXxr2RZM2U-6F9xyUQBvuZyaLo.3%2BnzoTpZ5FCrEtZAcAKIl1eU%2FbNW2BC0iajUmZNLFyU",
    "if-none-match": "W/\"22a-Q9lcTyXWV1v2NXWIuNgz34YwP7U\"",
    "referer": "https://anantharajuc.github.io/cURL-for-Windows/",
    "upgrade-insecure-requests": "1",
    "user-agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.3497.100 Safari/537.36",
    "x-forwarded-port": "443",
    "x-forwarded-proto": "https"
  },
  "url": "https://postman-echo.com/get?test=123"
}
```

#### Resources

- <a href="https://curl.haxx.se/book.html" target="_blank" >Everything curl</a> - eBook - Web Version, PDF, Mobi, ePub.
- cURL source <a href="https://github.com/curl/curl" target="_blank" >code</a> on GitHub.
- A <a href="https://jqplay.org/" target="_blank" >playground</a> for jq, (written in Go) with examples and cheatsheet.
