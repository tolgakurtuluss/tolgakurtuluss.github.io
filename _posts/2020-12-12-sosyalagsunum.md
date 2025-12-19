---
layout: post
title: Sosyal Ağ Analizi - "Amazon Veriseti"
subtitle: R ile birlikte alınan ürünlerin ağ yapısı üzerine bir inceleme
gh-repo: tolgakurtuluss/tolgakurtuluss.github.io
gh-badge: [star, fork, follow]
tags: [R, Sosyal Ağ Analizi, Veri Görselleştirme, Amazon]
comments: true
author: Tolga
---

Bu yazıda, Amazon.com'daki alışveriş verileri kullanılarak birlikte satın alınan ürünler arasındaki ilişkileri inceleyen bir sosyal ağ analizi projesinin özeti sunulmaktadır. Analiz, `R` programlama dili ve `igraph`, `visNetwork` gibi popüler kütüphaneler kullanılarak gerçekleştirilmiştir.

### Projenin Amacı

Projenin temel amacı, müşterilerin hangi ürünleri birlikte satın aldığını bir ağ yapısı olarak modellemek ve bu ağın temel özelliklerini ortaya çıkarmaktır. Bu sayede, ürün öneri sistemleri veya sepet analizleri için değerli içgörüler elde edilebilir.

### Analiz Adımları

Analiz genel olarak aşağıdaki adımları içermektedir:

1.  **Veri Hazırlığı:** Amazon alışveriş veriseti yüklenmiş ve `from` (kaynak ürün) ve `to` (hedef ürün) sütunları kullanılarak bağlantılar oluşturulmuştur. Aynı ürün çiftlerinin birden fazla kez satın alınması durumu, bağlantılara `ağırlık` (weight) olarak eklenmiştir.

    ```r
    library(igraph)
    library(visNetwork)
    library(dplyr)

    # Veriyi gruplayarak bağlantı ağırlıklarını hesaplama
    amazon_data <- amazon %>%
      group_by(from, to) %>%
      summarise(wgt = n())
    ```

2.  **Ağ İstatistiklerinin Hesaplanması:** Oluşturulan ağın yapısal özelliklerini anlamak için çeşitli metrikler hesaplanmıştır:
    *   **Yoğunluk (Density):** Ağdaki mevcut bağlantıların, olası tüm bağlantılara oranı.
    *   **Ortalama Uzaklık (Mean Distance):** Ağdaki herhangi iki düğüm arasındaki ortalama en kısa yol uzunluğu.
    *   **Çap (Diameter):** Ağdaki en uzun en kısa yol.
    *   **Karşılıklılık (Reciprocity):** Yönlü bir ağda, iki düğüm arasındaki bağlantının ne ölçüde çift yönlü olduğu.
    *   **Geçişlilik (Transitivity / Clustering Coefficient):** Bir düğümün komşularının da birbirine ne kadar bağlı olduğunu gösteren bir ölçüt.

3.  **Görselleştirme:** Ağ yapısı, `igraph` ve `visNetwork` kütüphaneleri kullanılarak hem statik hem de interaktif olarak görselleştirilmiştir. Bu görseller, ağdaki kümeleri ve merkezi düğümleri hızlıca tespit etmeyi sağlar.

### Sonuç

Bu analiz, ürünler arasındaki gizli ilişkileri ve müşteri satın alma davranışlarını ortaya çıkarmak için sosyal ağ analizinin ne kadar güçlü bir araç olabileceğini göstermektedir. Özellikle `visNetwork` ile oluşturulan interaktif grafikler, veri üzerinde sezgisel keşifler yapma imkanı tanımıştır.

{: .box-note}
**Not:** Analizin tamamını, R kodlarını ve tüm interaktif görselleri içeren orijinal sunum dosyasına aşağıdan erişebilirsiniz.

[Orijinal Sunumu Görüntüle](_posts/html/sosyalagsunum.html)
