---
layout: default
title: Meta Tags
parent: HTML
---

# HTML Meta Tags Cheatsheet

---

## Essential

```html
<!--
  The following 2 meta tags *must* come first in the <head>
  to consistently ensure proper document rendering.
  Any other head element should come *after* these tags.
-->
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">

<!-- Short description of the document (limit to 150 characters) -->
<!-- This content *may* be used as a part of search engine results. -->
<meta name="description" content="A description of the page">
```

---

## Optional/Situational

```html
<!--
  Allows control over where resources are loaded from.
  Place as early in the <head> as possible, as the tag
  only applies to resources that are declared after it.
-->
<meta http-equiv="Content-Security-Policy" content="default-src 'self'">

<!-- Name of web application (only should be used if the website is used as an app) -->
<meta name="application-name" content="Application Name">

<!-- Theme Color for Chrome, Firefox OS and Opera -->
<meta name="theme-color" content="#4285f4">

<!-- Control the behavior of search engine crawling and indexing -->
<meta name="robots" content="index,follow"><!-- All Search Engines -->
<meta name="googlebot" content="index,follow"><!-- Google Specific -->

<!-- Tells Google not to show the sitelinks search box -->
<meta name="google" content="nositelinkssearchbox">

<!-- Tells Google not to provide a translation for this document -->
<meta name="google" content="notranslate">

<!-- Identify the software used to build the document (i.e. - WordPress, Dreamweaver) -->
<meta name="generator" content="program">

<!-- Short description of your document's subject -->
<meta name="subject" content="your document's subject">

<!-- Gives a general age rating based on the document's content -->
<meta name="rating" content="General">

<!-- Allows control over how referrer information is passed -->
<meta name="referrer" content="no-referrer">

<!-- Disable automatic detection and formatting of possible phone numbers -->
<meta name="format-detection" content="telephone=no">

<!-- Completely opt out of DNS prefetching by setting to "off" -->
<meta http-equiv="x-dns-prefetch-control" content="off">

<!-- Stores a cookie on the client web browser for identification purposes -->
<meta http-equiv="set-cookie" content="name=value; expires=date; path=url">

<!-- Specifies the document to appear in a specific frame -->
<meta http-equiv="Window-Target" content="_value">

<!-- Geo tags -->
<meta name="ICBM" content="latitude, longitude">
<meta name="geo.position" content="latitude;longitude">
<meta name="geo.region" content="country[-state]"><!-- Country code (ISO 3166-1): mandatory, state code (ISO 3166-2): optional; eg. content="US" / content="US-NY" -->
<meta name="geo.placename" content="city/town"><!-- eg. content="New York City" -->
```

---

## Facebook Open Graph

```html
<meta property="fb:app_id" content="123456789">
<meta property="og:url" content="https://example.com/page.html">
<meta property="og:type" content="website">
<meta property="og:title" content="Content Title">
<meta property="og:image" content="https://example.com/image.jpg">
<meta property="og:description" content="Description Here">
<meta property="og:site_name" content="Site Name">
<meta property="og:locale" content="en_US">
<meta property="article:author" content="">
```

- [The Open Graph protocol](http://ogp.me/)
- [Facebook Open Graph Markup](https://developers.facebook.com/docs/sharing/webmasters#markup)
- [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/)

---

## Twitter Card

```html
<meta name="twitter:card" content="summary">
<meta name="twitter:site" content="@site_account">
<meta name="twitter:creator" content="@individual_account">
<meta name="twitter:url" content="https://example.com/page.html">
<meta name="twitter:title" content="Content Title">
<meta name="twitter:description" content="Content description less than 200 characters">
<meta name="twitter:image" content="https://example.com/image.jpg">
```

- [Optimize Tweets with Cards - Twitter Developers](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/guides/getting-started)
