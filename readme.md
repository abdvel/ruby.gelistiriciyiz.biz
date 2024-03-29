# ruby.gelistiriciyiz.biz

[http://ruby.gelistiriciyiz.biz][1] sitesinin
kaynak kodu. [webBox.io’nun][2] [Middleman][3] template / statik
sayfa üreticisi çatısı üzerine üzerine [jekyll-incorporated][4]
temasının modifiyesi ile yapılmıştır.


## Kurulum

* Ruby 2.2.2 (*En az 2 olsa yeterli*)

Repo’yu clone ettikten sonra;

```bash
bundle install --path=vendor/bundle --binstubs
rake          # ön izleme sunucusunu çalıştırır

rake -T       # Task’leri göster...

rake deploy   # Deploy
rake preview  # Ön izleme / geliştirme sunucusu
```

## Front-matter Değişkenleri

    title: Başlık
    subtitle: Alt Başlık (Opsiyonel)
    published: false (Opsiyonel)
    date: Tarih (YIL-AY-GÜN SAAT:DAKİKA)
    tags: etiket,etiket,etiket (Opsiyonel)
    cover: Fotoğraf (Opsiyonel)
    
    (Opsiyonel)
    author:
        name: "AD-SOYAD"
        email: "E-POSTA"
        link: "LİNK"
        bio: "1 SATIR BİO"

**published: false**

Bu **Draft** yani sadece kendi yerel bilgisayarınızda görünecek,
deploy edince görünmeyecek post şeklidir.

**tags:**

Etiketleri virgül ile ayırıyoruz. Türkçe karakter kullanmıyoruz.

**cover:**

Yazıya fotoğraf eklemek için. Eğer `cover: "resim.jpg"` gibi
kullanırsanız; resmin yeri `source/public/images/posts/resim.jpg`
olmalı. İsterseniz dış link de verebilirsiniz:
`cover: "http://example.com/resim.jpg"`


## HTML Yardımcılar

**READ_MORE**

Özet kısmı için kullanır. Örnek:

    ---
    title: "Daha detaylı `git-branch`"
    date: 2013-01-06 22:03
    tags: branch
    ---
    Local’deki ve Remote’daki yani varolan tüm **branch**'leri göstermek 
    için;
    READ_MORE
    

**zoom resim**

Eğer yazı içinde tıklayınca büyüyecek bir resim koymak isterseniz;

```html
<div class="full zoomable"><img src="resim.jpg" alt="resim"></div>
```

**video oynatıcı**

```html
<div class="flash-video">
    <div><iframe src="video.mp4" width="100%" height="100%" frameborder="0"></iframe></div>
</div>
```

şeklinde kullanabilirsiniz.


## Yeni Post

Yeni post yapmak için `rake post` yapmanız yeterli.

    rake post["Yeni yazı"] # ya da
    bundle exec rake post["Yeni yazı"]


## Deployment

[Middleman][3] pek çok farklı özellikle geliyor.
Ben `:rsync` yöntemini seçtim. Bu işi sağlıklı yapabilmek için, lütfen 
root’da `creds.rb` dosyasını oluşturun ve;

    DEPLOY_USER = "kullanıcı_adı"
    DEPLOY_HOST = "server"
    DEPLOY_PATH = "/path/to/site"

değişkenlerini tanımlayın. Daha sonra `rake deploy` ya da 
`bundle exec rake deploy` yaparak statik html’leri sunucuza 
gönderebilirsiniz.


## config.yaml

Site ile ilgili genel değişkenler. Eğer post içinde `author` tanımlaması
yoksa, bu dosyadı `main_author` ’da bulunan değerler kullanılır tüm
post’lar için.

    site:
      production_url: "http://domain"
      title: "Başlık"
      subtitle: "Alt Başlık"
      tag_line: "Mini slogan"
      description: "Açıklaması"
      logo: "minik logo"
      cover_image: "site ana fotoğraf"
      social:
        twitter: 
        facebook:
      company:
        name: "FİRMA_ADI"
        url: "http://firma_web_adresi"
      product:
        name: "ÜRÜN_ADI"
        url: "http://ürün_adresi"
      main_author:
        name: "AD-SOYAD"
        email: "E-POSTA"
        link: "LİNK"
        bio: "1 SATIR BİO"


## Güncellemeler

**2016-03-02**

* Heroku için deploy edebilme konfigürasyonu iptal edildi.

**2015-10-04**

* `rake post` ile otomatik olarak post oluşturma eklendi.

**2015-09-24**

* `logo.png` geldi.
* Örnek `nginx.conf` geldi.
* Front-matter değişlenleri açıklandı
* HTML yardımcıları açıklandı.
* Deployment açıklandı.
* `config.yaml` açıklandı.


## Katkı Yapın

1. `fork` yapın ( [tıkla](https://github.com/gelistiriciyiz-biz/ruby.gelistiriciyiz.biz/fork) )
2. Kendi `branch`’inizi yapın (`git checkout -b benim-makalem`)
3. Yaptıklarınızı `commit` edin (`git commit -am 'Yeni makale'`)
4. `branch`’i `push` edin (`git push origin benim-makalem`)
5. Yeni bir **Pull Request** oluşturun!


[1]: http://ruby.gelistiriciyiz.biz
[2]: https://github.com/webBoxio/middleman-boilerplate-template
[3]: https://middlemanapp.com/
[4]: https://github.com/kippt/jekyll-incorporated
