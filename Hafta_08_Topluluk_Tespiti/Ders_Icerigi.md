# Hafta 8: Topluluk Tespiti ve Kümeleme (Community Detection)

## 📌 1. Ders Hakkında ve Giriş
Bir düğün davetiyesi hazırladığınızı düşünün. Davetlileri masalara yerleştirmeniz gerekir. Lise arkadaşlarınızı bir masaya, iş arkadaşlarınızı başka bir masaya, akrabalarınızı ise ayrı bir masaya oturtursunuz. Herkesin herkesi tanıdığı gruplar (masalar) vardır ve bu gruplar arasında çok az bağlantı (belki sadece siz) vardır. İşte bu masalar, sosyal ağ analizinde **"Topluluk" (Community)** veya **Modül** olarak adlandırılır.

Ağlar homojen değildir; pütürlüdür. İçlerinde yoğun etkileşimli alt yapılar barındırırlar. Bu yapıları (aileleri, politik fraksiyonları, bilimsel disiplinleri, protein komplekslerini) tespit etmek, ağın fonksiyonunu anlamak için hayati önem taşır. Ancak sorun şudur: Elimizde davetli listesi ve kimin masada olacağı etiketi yoktur. Elimizde sadece milyonlarca kenardan oluşan bir "yumak" vardır.

Bu hafta, denetimsiz öğrenme (unsupervised learning) yöntemlerini kullanarak, yani etiketlenmemiş veriden, ağın içindeki bu doğal grupları nasıl **algoritmik** olarak çıkarabileceğimizi öğreneceğiz. Girvan-Newman'ın "börekçiyi kesme" yönteminden, modern Louvain optimizasyonuna kadar farklı teknikleri inceleyeceğiz.

## 📚 2. Konu Başlıkları ve Haftalık Akış
1.  **Topluluk Yapısı Nedir?**
    *   Tanım: Grup içi yoğunluk > Grup dışı yoğunluk.
    *   Sosyolojik temeller (Granovetter, Simmel).
2.  **Hiyerarşik Kümeleme (Hierarchical Clustering)**
    *   Aglomeratif (Birleştirici) ve Divisive (Bölücü) yöntemler.
    *   Dendrogram (Soy ağacı) gösterimi.
3.  **Bölücü Yöntemler: Girvan-Newman Algoritması**
    *   Kenar Arasındalığı (Edge Betweenness) kavramı.
    *   Köprüleri yıkarak toplulukları ayırmak.
4.  **Modülerlik (Modularity) Optimizasyonu**
    *   $Q$ skoru nedir? İyi bir bölünme nasıl ölçülür?
    *   **Louvain Metodu:** Hız ve ölçeklenebilirlik.
5.  **Örtüşen Topluluklar (Overlapping Communities)**
    *   Gerçek hayatta bir kişi birden fazla gruba aittir.
    *   Clique Percolation Method (CPM / k-clique).

## 📝 3. Detaylı İçerik

### 3.1. Topluluk Nedir?
Sezgisel olarak topluluk, "birbirleriyle, dışarıdakilere kıyasla daha sıkı fıkı olan düğümler grubu"dur.
*   **İç Bağlantı (Intra-cluster density):** Yüksek olmalı.
*   **Dış Bağlantı (Inter-cluster density):** Düşük olmalı.

Bu yapıları bulmak neden önemli?
*   Amazon'da "bunu alan bunu da aldı" önerileri aslında ürünlerin oluşturduğu topluluklardır.
*   Kanser araştırmalarında, benzer genlerin oluşturduğu fonksiyonel modüller hastalığın sebebini açıklar.
*   Sosyal medyada politik yankı odalarını (echo chambers) tespit etmek için kullanılır.
*   Spotify'da müzik türlerini sınıflandırmak için kullanılır.

### 3.2. Girvan-Newman Algoritması: Köprüleri Yakmak
Michelle Girvan ve Mark Newman (2002), toplulukları bulmak için dahice bir ters mantık geliştirdiler: "Toplulukların merkezine (en yoğun yerine) değil, sınırlarına odaklan."
Toplulukları birbirine bağlayan kenarların (köprülerin) **arasındalık merkezliği (betweenness centrality)** çok yüksektir. Çünkü A grubundan B grubuna gitmek isteyen herkes bu köprüden geçmek zorundadır. Köprüdeki trafik sıkışıktır.

**Algoritma Adımları:**
1.  Ağdaki tüm kenarların arasındalık değerini hesapla.
2.  En yüksek arasındalığa sahip kenarı ağdan **sil** (Köprüyü yık).
3.  Arasındalık değerlerini **tekrar hesapla** (Çünkü bir köprü yıkılınca trafik başka yollara kayar, yeni köprüler oluşur).
4.  Ağ parçalanana (bileşenlere ayrılana) kadar 2. adıma dön.

Bu süreç sonucunda ağ yavaş yavaş parçalanır. İlk kopan parçalar en belirgin topluluklardır. Bu süreç bir **Dendrogram** (ağaç yapısı) ile görselleştirilir. Ağacı kökünden (herkes tek grup) yapraklarına (herkes ayrı) kadar inceleyebiliriz. Ağacı istediğimiz yerden keserek, ne kadar detaylı veya genel topluluklar istediğimize karar verebiliriz.
*   **Dezavantajı:** Ağır ve yavaştır ($O(N^3)$). Milyonluk ağlarda çalışmaz.

### 3.3. Modülerlik (Modularity - $Q$)
Peki, ağacı nereden keseceğiz? Veya bulduğumuz topluluk yapısının "iyi" olup olmadığını nasıl bileceğiz?
Newman ve Girvan, **Modülerlik ($Q$)** adında bir kalite fonksiyonu geliştirdiler.
$$ Q = (\text{Grup içi kenar oranı}) - (\text{Rastgele ağda beklenen grup içi kenar oranı}) $$
*   $Q \approx 0$: Gruplaşma yok (Rastgele ağ). Grup içi bağ sayısı şans eseri beklenen kadar.
*   $Q > 0.3$: Belirgin bir topluluk yapısı var.
*   $Q \approx 1$: Mükemmel ayrışmış, birbirinden kopuk adalar.

Algoritmalardan beklenen, matematiksel olarak bu $Q$ değerini maksimize eden bölünmeyi (partition) bulmasıdır.

### 3.4. Louvain Metodu: Hızın Kralı
Büyük ağlar (Facebook, Twitter) için Girvan-Newman kullanılamaz. Louvain (Blondel et al., 2008) metodu, şu an endüstri standardıdır. Modülerlik optimizasyonunu "Açgözlü" (Greedy) ve hiyerarşik bir şekilde yapar.
1.  **Adım 1 (Yerel Taşıma):** Her düğümü kendi başına bir topluluk yap. Her düğüm için şunu dene: "Komşumun olduğu topluluğa geçersem $Q$ artar mı?" Artarsa geç, artmazsa kal. Bu işlem yerel maksimuma ulaşana kadar tekrar edilir.
2.  **Adım 2 (Agregasyon):** Oluşan toplulukları tek bir "süper düğüm" gibi düşün ve ağı küçült. Topluluk içi bağlar kendine dönen kenar (self-loop), topluluklar arası bağlar ise süper düğümler arası kenar olur.
3.  Tekrar Adım 1'e dön ve süper düğümleri birleştir.
Bu yöntemle milyarlarca kenarlı ağlar dakikalar içinde analiz edilebilir. Çok seviyeli (hiyerarşik) bir yapı ortaya çıkarır (Örn: Şehir -> Mahalle -> Sokak).

### 3.5. Örtüşen Topluluklar (Gerçek Hayatın Karmaşası)
Girvan-Newman veya Louvain, her düğümü **sadece bir** topluluğa atar (Hard Partitioning). Ali ya A grubundadır ya B grubunda.
Ama gerçek hayatta Ali hem "Lise Arkadaşları" grubunda, hem "İş Arkadaşları" grubunda hem de "Satranç Kulübü"ndedir. Topluluklar **örtüşür (overlap)**. Ali bu toplulukların kesişim kümesindedir.

**Clique Percolation Method (CPM):**
Palla et al. (2005) tarafından geliştirilmiştir. "Klikleri" (birbiriyle tam bağlı 3'lü üçgenler veya 4'lü tam graflar) birer yapı taşı olarak kullanır. Birbiriyle kenar paylaşarak "yuvarlanan" klikler bir topluluk oluşturur. Bir düğüm birden fazla klike ait olabileceği için, birden fazla topluluğa da ait olabilir. Yoğunluk (Density) temelli bir yaklaşımdır.

## 🔑 4. Anahtar Kavramlar Sözlüğü
*   **Community Detection:** Ağdaki yoğun alt grafikleri bulma işlemi (Cluster analysis).
*   **Edge Betweenness:** Bir kenarın üzerinden geçen en kısa yolların trafiği.
*   **Modularity ($Q$):** Bir bölümlemenin istatistiksel kalitesi. Toplulukların rastlantısal olup olmadığını ölçer.
*   **Dendrogram:** Hiyerarşik kümelemeyi gösteren ağaç diyagramı.
*   **Resolution Limit:** Modülerlik yönteminin çok küçük toplulukları görememe (ayırt edememe) sorunu.
*   **Overlapping Communities:** Kesişim kümeleri olan topluluklar (Soft Partitioning).

## 🛠 5. Kaynaklar ve İleri Okuma Önerileri
### Makaleler
*   **Girvan, M., & Newman, M. E. (2002).** "Community structure in social and biological networks". *PNAS*.
*   **Blondel, V. D., et al. (2008).** "Fast unfolding of communities in large networks" (Louvain metodunun orijinal makalesi).

### Araçlar
*   **Gephi:** Yan paneldeki "Statistics -> Modularity" butonuna basarak ağınızı renklendirin. Toplulukların görsel olarak nasıl ayrıştığını göreceksiniz. (Louvain kullanır).
*   **Python (Community kütüphanesi):**
    ```python
    import community as community_louvain
    import networkx as nx
    G = nx.karate_club_graph()
    partition = community_louvain.best_partition(G)
    # partition bir sözlüktür: {düğüm_id: topluluk_id}
    ```

## 🎯 6. Haftanın Özeti ve Gelecek Haftaya Bakış
Bu hafta, karmaşık bir ağ yumağını (Hairball) alıp, onu anlamlı sosyal gruplara ayırmayı öğrendik. Gördük ki, ağın topolojisi (yapısı) bize kimin kiminle dost olduğunu, etikete ihtiyaç duymadan söylüyor.
Peki bu gruplar ve bağlantılar üzerinde ne oluyor? Topluluklar statik midir? Hayır. Ağ üzerinde bilgi, para, virüs veya fikirler akar. Bir fikir (meme) nasıl viral olur? İnsanlar neden kendi gruplarının fikirlerine saplanıp kalır (Yankı Odaları)? Gelecek hafta, ağın "yapısından" ağın "dinamiğine" geçeceğiz ve **Bilgi Yayılımı (Information Diffusion)** konusunu işleyeceğiz.
