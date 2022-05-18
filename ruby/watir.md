---
layout: default
title: Watir
parent: Ruby
---

# Watir Cheatsheet

---

## Download with headless Chrome

```rb
prefs = {
  :download => {
    :prompt_for_download => false,
    :default_directory => download_dir
  }
}

args = %w[headless disable-gpu disable-dev-shm-usage no-sandbox]
browser = Watir::Browser.new :chrome, args: args

params = {'behavior': 'allow', 'downloadPath': download_dir}
browser.driver.execute_cdp 'Page.setDownloadBehavior', params
```

Reference: [https://github.com/SeleniumHQ/selenium/issues/5159](https://github.com/SeleniumHQ/selenium/issues/5159)
