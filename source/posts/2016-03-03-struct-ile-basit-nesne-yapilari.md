---
title: Struct ile basit nesne yapıları
date: Mar 03, 2016 16:49
tags: object
subtitle: Veri yapısı
---

Basit nesne yapıları gerektiğinde;

```ruby
Person = Struct.new(:name, :gender, :age)
user = Person.new('Ahmet', 'erkek', 43)
user.name    # => "Ahmet"
user.gender  # => "erkek"
user.age     # => 43
```

şeklinde kullanabilir. Daha gelişmiş kullanım için [OpenStruct][01]
önerilir.

[01]: http://ruby-doc.org/stdlib-2.3.0/libdoc/ostruct/rdoc/OpenStruct.html
