---
layout: post
title: "Twitter Ağ Analizi: Takipçi Etkileşimleri"
subtitle: "Çekirdek Kullanıcı Grubuna Yönelik Etkileşimlerin İncelenmesi"
gh-repo: tolgakurtuluss/tolgakurtuluss.github.io
gh-badge: [star, fork, follow]
tags: [R, Sosyal Ağ Analizi, Twitter, igraph, Takipçi Analizi]
comments: true
author: Tolga Kurtuluş
---

Bu yazı, daha önce [ana Twitter ağ analizi](./html/twittersunum.md) çalışmasında incelenen veri setinin bir alt kümesine odaklanmaktadır. Bu özel analizde, yalnızca belirlenen çekirdek kullanıcı grubuna yönelik olarak dışarıdan gelen etkileşimler (mention'lar ve reply'lar) ele alınmıştır. Bu, bir nevi "takipçi ağı"nın yapısını ve dinamiklerini ortaya koymaktadır.

### Analizin Amacı

Bu alt çalışmanın amacı, ana ağ yapısından farklı olarak, çekirdek grubun ne kadar ve kimler tarafından "konuşulduğunu" anlamaktır. Analiz, etkileşimin yönünü dikkate alarak, takipçilerden gelen bağlantıları süzerek oluşturulmuş bir ağ üzerinde gerçekleştirilmiştir.

### Yöntem

Orijinal veri seti, `dplyr` paketi kullanılarak filtrelenmiştir. Sadece `to` sütununda çekirdek kullanıcıların yer aldığı satırlar analize dahil edilmiştir.

```r
# Çekirdek kullanıcı listesi
names <- c("alperumuttosun", "eaylnk", "gizemzzengin", "canaltundaloglu", "palairemm", 
           "senatosko", "86alkin", "alishanozturk", "tolgaakurtuluss", 
           "nurdanayozturk", "mrv2712")

# Veriyi sadece çekirdek kullanıcılara gelen etkileşimleri içerecek şekilde filtreleme
followers_data <- twitterdata %>%
  filter(to %in% names)
```

Bu filtrelenmiş veri üzerinden, ana analizdeki adımlar tekrarlanmıştır:

*   `igraph` ile yeni bir yönlü graf (`plot_followers`) oluşturulmuştur.
*   Bu yeni ağ için derece, arasındalık, yakınlık ve PageRank gibi merkeziyet metrikleri yeniden hesaplanmıştır.
*   Ağın yoğunluk, ortalama uzaklık ve geçişlilik gibi genel yapısal istatistikleri çıkarılmıştır.
*   Sonuçlar, `visNetwork` ile interaktif bir grafikte ve `DT` ile aranabilir bir tabloda sunulmuştur.

### Bulgular

Bu odaklanmış analiz, çekirdek kullanıcı grubunun en çok hangi takipçilerden etkileşim aldığını ve bu takipçi ağındaki en merkezi kişilerin kimler olduğunu göstermiştir. Ana ağa kıyasla daha düşük yoğunluklu ancak belirli kümeler etrafında toplanmış bir yapı gözlemlenmiştir.

{: .box-note}
**Not:** Sadece takipçi etkileşimlerini içeren bu özel analizin interaktif grafiğine ve detaylı metrik tablolarına aşağıdaki bağlantıdan ulaşabilirsiniz.

[Takipçi Ağı Sunumunu Görüntüle](./html/twittersunum1.html)
