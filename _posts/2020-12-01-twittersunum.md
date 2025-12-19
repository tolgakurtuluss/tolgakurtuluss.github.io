---
layout: post
title: "Twitter Ağ Analizi (Pt-1): Kişisel Ağ"
subtitle: "R, igraph ve visNetwork Kullanarak Etkileşim Haritası"
gh-repo: tolgakurtuluss/tolgakurtuluss.github.io
gh-badge: [star, fork, follow]
tags: [R, Sosyal Ağ Analizi, Twitter, Veri Görselleştirme, igraph]
comments: true
author: Tolga
---

Bu blog yazısında, kişisel bir Twitter hesabının etkileşim verileri üzerinden gerçekleştirilen sosyal ağ analizi çalışması özetlenmektedir. Çalışmada, kullanıcılar arasındaki `mention` ve `reply` gibi etkileşimler bir ağ yapısı olarak ele alınmış ve `R` programlama dili ile analiz edilmiştir.

### Analizin Kapsamı

Analiz, belirli bir kullanıcı grubunun ve onların etkileşimde bulunduğu diğer hesapların oluşturduğu ağı incelemektedir. Amaç, ağdaki merkezi aktörleri belirlemek, etkileşim yoğunluğunu ölçmek ve genel ağ yapısını anlamaktır.

Bu çalışma kapsamında aşağıdaki adımlar uygulanmıştır:

1.  **Veri Setinin Oluşturulması:** Twitter API'si aracılığıyla toplanan etkileşim verileri (`from`, `to` şeklinde) bir CSV dosyasından okunmuştur.

2.  **Ağ Grafiğinin Yaratılması:** `igraph` kütüphanesi kullanılarak yönlü bir etkileşim grafiği oluşturulmuştur.

3.  **Merkeziyet ve Önem Metriklerinin Hesaplanması:** Ağdaki en etkili veya merkezi kullanıcıları tespit etmek için çeşitli metrikler hesaplanmıştır:
    *   **Derece Merkeziyeti (Degree):** Bir kullanıcının ne kadar çok kişiyle doğrudan etkileşimde olduğunu gösterir.
    *   **Arasındalık Merkeziyeti (Betweenness):** Bir kullanıcının, ağdaki diğer kullanıcılar arasındaki en kısa yollar üzerinde ne sıklıkla yer aldığını ölçer. İletişim akışındaki kilit rolü gösterir.
    *   **PageRank:** Bir kullanıcının önemini, kendisine gelen bağlantıların (mention/reply) önemine göre hesaplar.

    ```r
    library(igraph)
    library(DT)

    # Grafiği oluşturma
    plot2 <- graph_from_data_frame(d=twitterdata, directed=T)

    # Metrikleri hesaplama
    derece <- degree(plot2)
    arasindamerkez <- betweenness(plot2, normalized=TRUE)
    pagerankmerkez <- page_rank(plot2)$vector

    # Sonuçları bir tabloda gösterme
    datatable(data.frame(derece, arasindamerkez, pagerankmerkez))
    ```

4.  **Ağ Yapısının İncelenmesi:** `edge_density` (yoğunluk) ve `transitivity` (geçişlilik/kümelenme) gibi metriklerle ağın genel yapısı hakkında bilgi edinilmiştir.

5.  **Etkileşimli Görselleştirme:** `visNetwork` kütüphanesi ile kullanıcıların ağı interaktif olarak keşfetmesine olanak tanıyan bir görselleştirme hazırlanmıştır.

### Öne Çıkan Bulgular

Analiz sonucunda, kendi hesabım olan `tolgaakurtuluss`'un hem en çok etkileşim alan hem de ağ içindeki bilgi akışında en merkezi rolde olan hesap olduğu görülmüştür. Bu durum, PageRank ve Arasındalık Merkeziyeti değerlerinin yüksekliği ile doğrulanmıştır.

{: .box-note}
**Not:** Analizin tüm detaylarını, R kodlarını ve interaktif grafikleri içeren orijinal sunum dosyalarına aşağıdaki bağlantılardan erişebilirsiniz.

- [Ana Sunumu Görüntüle](/assets/html/twittersunum.html)
- [Takipçilere Göre Ağ Yapısı Analizi](/assets/html/twittersunum1.html)
- [Takip Edilenlere Göre Ağ Yapısı Analizi](/assets/html/twittersunum2.html)
