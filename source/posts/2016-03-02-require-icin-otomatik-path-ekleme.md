---
title: require için otomatik path ekleme
date: Mar 02, 2016 16:10
tags: $LOAD_PATH
---

`/path/to/folder/code.rb` dosyasını kolay `require` edebilmek için;

```ruby
$:.push("/path/to/folder/")
require 'code'
```