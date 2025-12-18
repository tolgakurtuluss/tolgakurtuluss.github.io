---
layout: post
title: "Twitter Ağ Analizi: Takip Edilenlerle Etkileşimler"
subtitle: "Çekirdek Kullanıcı Grubunun Başlattığı Etkileşimlerin İncelenmesi"
gh-repo: tolgakurtuluss/tolgakurtuluss.github.io
gh-badge: [star, fork, follow]
tags: [R, Sosyal Ağ Analizi, Twitter, Etkileşim Analizi]
comments: true
author: Tolga Kurtuluş
---

Bu blog yazısı, [ana Twitter ağ analizi](./html/twittersunum.md) çalışmasının ikinci alt bölümü olarak, çekirdek kullanıcı grubunun kimlerle etkileşime girdiğini incelemektedir. [Bir önceki analizde](./html/twittersunum1.md) takipçilerden gelen etkileşimler incelenirken, bu çalışmada ise çekirdek grubun başlattığı (giden) etkileşimler mercek altına alınmıştır.

### Analizin Amacı

Bu analizin temel amacı, çekirdek kullanıcı grubunun ilgi alanlarını ve en çok kimleri "konuştuğunu" bir ağ yapısı üzerinden ortaya çıkarmaktır. Veri seti, `from` (gönderen) sütununda sadece çekirdek kullanıcıların yer alacağı şekilde filtrelenerek, bu grubun etkileşimde bulunduğu "takip edilenler ağı" oluşturulmuştur.

### Yöntem

Analiz için orijinal veri seti, `dplyr` paketi ve `%in%` operatörü kullanılarak filtrelenmiştir.

```r
# Çekirdek kullanıcı listesi
names <- c("alperumuttosun", "eaylnk", "gizemzzengin", "canaltundaloglu", "palairemm", 
           "senatosko", "86alkin", "alishanozturk", "tolgaakurtuluss", 
           "nurdanayozturk", "mrv2712")

# Veriyi sadece çekirdek kullanıcıların başlattığı etkileşimleri içerecek şekilde filtreleme
following_data <- twitterdata %>%
  filter(from %in% names)
```

Bu yeni ve odaklanmış veri seti üzerinden, ağ analizi metrikleri yeniden hesaplanmış ve `visNetwork` kullanılarak interaktif bir ağ grafiği oluşturulmuştur. Bu sayede, çekirdek grubun en çok hangi hesaplarla konuştuğu ve bu etkileşim ağının yapısı incelenmiştir.

### Bulgular

Yapılan analiz, çekirdek grubun kendi içinde yoğun bir etkileşime sahip olduğunu, ancak aynı zamanda belirli haber kaynakları, ünlüler veya diğer sosyal çevrelerle de güçlü bağları olduğunu göstermiştir. Özellikle `PageRank` ve `Derece Merkeziyeti` (degree) metrikleri, grubun en çok referans verdiği veya konuştuğu hesapları belirlemede kilit rol oynamıştır.

{: .box-note}
**Not:** Sadece takip edilenlerle olan etkileşimleri içeren bu özel analizin interaktif grafiğine ve detaylı metrik tablolarına aşağıdaki bağlantıdan ulaşabilirsiniz.

[Takip Edilenler Ağı Sunumunu Görüntüle](./html/twittersunum2.html)
