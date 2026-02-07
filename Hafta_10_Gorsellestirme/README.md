# Hafta 10: Ağ Görselleştirme Prensipleri (Network Visualization)

## 📌 1. Ders Hakkında ve Giriş
Veri analitiğinde sıkça söylenen bir söz vardır: "Veriye kendi gözlerinizle bakana kadar, ona inanmayın." Anscombe'un Dörtlüsü gibi istatistiksel örnekler, aynı ortalamaya ve varyansa sahip veri setlerinin görselleştirildiğinde tamamen farklı görünebileceğini kanıtlar. Sosyal Ağ Analizinde bu durum daha da kritiktir. Milyonlarca satırlık bir "Kenar Listesi" Excel dosyasına bakarak ağın yapısını (merkezleri, kümeleri, kopuklukları) anlamak imkansızdır. Görselleştirme (Visualization), insan beyninin pattern (örüntü) tanıma yeteneğini kullanarak içgörü elde etmenin en hızlı yoludur.

Ancak ağ görselleştirme, basit bir "çizim yapma" işi değildir. Zorlu bir matematiksel optimizasyon ve tasarım problemidir. 1000 düğümlü bir ağda, düğümleri ekrana nasıl yerleştireceksiniz ki çizgiler birbirine karışmasın, gruplar belli olsun ve sonuç estetik görünsün? Buna **"Graph Drawing"** problemi denir.

Bu hafta, estetiği matematikle birleştireceğiz. **Force-Directed (Kuvvet Yönelimli)** algoritmaların fiziği nasıl taklit ederek ağları düzenlediğini, "Hairball" (Tüy Yumağı) sorununu nasıl çözeceğimizi ve renk/boyut/şekil gibi görsel değişkenleri (Visual Encodings) kullanarak veriyi nasıl "konuşturacağımızı" öğreneceğiz.

## 📚 2. Konu Başlıkları ve Haftalık Akış
1.  **Görselleştirmenin Amacı**
    *   Keşifsel (Exploratory) vs. Açıklayıcı (Explanatory) görselleştirme.
    *   İnsan algısı ve Gestalt prensipleri (Yakınlık yasası).
2.  **Düzen (Layout) Algoritmaları**
    *   Rastgele Düzen (Random Layout) - Neden işe yaramaz?
    *   **Force-Directed Algoritmalar:** Fruchterman-Reingold, ForceAtlas2, Yifan Hu. (Yaylar ve Elektronlar analojisi).
    *   Diğer Düzenler: Çembersel (Circular), Radyal, Hiyerarşik (Tree), Coğrafi (GeoLayout).
3.  **Görsel Kodlama (Visual Encoding)**
    *   Retinal Değişkenler: Boyut, Renk, Şekil, Opaklık.
    *   Hangi veriye hangisi atanmalı? (Skaler değer -> Boyut, Kategorik değer -> Renk).
4.  **Yaygın Sorunlar ve Çözümler**
    *   "Hairball" (Karmaşık Yumak) Etkisi.
    *   Filtreleme, Gruplama (Sparsification), Kenar Demetleme (Edge Bundling).
5.  **İnteraktif Görselleştirme**
    *   Pan, Zoom, Tooltip, Filter.

## 📝 3. Detaylı İçerik

### 3.1. Neden Görselleştiriyoruz?
İnsan beyni, patern (örüntü) tanıma konusunda süper bilgisayarlardan bile üstündür. İyi bir ağ haritası (Sosyogram), karmaşık ilişkileri saniyeler içinde anlatabilir.
1.  **Dışlananları Bulmak:** Gruptan kopuk düğümleri (İzoleler) görmek.
2.  **Kümeleri Görmek:** Renklendirme yapmadan bile topolojik yakınlığı görmek.
3.  **Köprüleri Fark Etmek:** İki yoğun küme arasındaki ince bağlantıyı (zayıf bağları) tespit etmek.
4.  **Hataları Bulmak:** Veri setinde olmaması gereken garip bağlantıları (artefaktları) yakalamak.

### 3.2. Fizik Simülasyonu Olarak Ağlar: Force-Directed Layouts
Ağı kağıda çizmek için düğümlerin $(x, y)$ koordinatlarına ihtiyacımız vardır. Peki bu koordinatları neye göre belirleyeceğiz? En popüler ve doğal görünen yöntem, ağı fiziksel bir sistem gibi simüle etmektir.
*   **Coulomb Yasası (İtme):** Tüm düğümler, elektrik yüklü parçaçıklar (örneğin elektronlar) gibi davranır ve birbirini iter. Bu, düğümlerin üst üste binmesini engeller ve ağı uzaya yayar. Düğümler arası mesafe ne kadar azsa, itme kuvveti o kadar artar.
*   **Hooke Yasası (Çekme):** Sadece birbirine bağlı olan düğümler (kenarlar), aralarında yay (spring) varmış gibi birbirini çeker. Bu, ilişkili kişileri birbirine yaklaştırır. Yay ne kadar gerilirse, çekme kuvveti o kadar artar.

Bilgisayar bu simülasyonu iteratif olarak (döngülerle) çalıştırır. Başlangıçta kaos vardır, ama zamanla sistem enerjisini minimize eder ve **denge (equilibrium)** durumuna gelir. Sonuç: Kümeler bir arada durur, alakasızlar uzaklaşır.
*   **Fruchterman-Reingold:** Küçük ağlar için klasik ve dengeli. Ağı bir daire içine sığdırmaya çalışır.
*   **ForceAtlas2 (Gephi):** Büyük ağlar (10.000+ düğüm) için optimize edilmiş, kümeleri (Community) çok iyi ayıran modern algoritma. Yerçekimi (Gravity) ayarı ile dağınık parçaları merkeze çeker.
*   **Yifan Hu:** Çok büyük ağları hızla kabaca şekillendirmek için kullanılır (Multilevel).
*   **OpenOrd:** Çok çok büyük (100.000+) ağlarda kümeleri keskin şekilde ayırmak için kullanılır (Estetikten ziyade analitik).

### 3.3. Görsel Kodlama: Estetik Değil, Bilgi
Ağı çizdikten sonra, analitik sonuçları görsel özelliklere (Visual Attributes) haritalamamız gerekir. Bu bir tasarım tercihidir.
1.  **Boyut (Size) = Önem:** Düğümün boyutu, genellikle bir merkezilik ölçüsü (Derece veya Arasındalık) ile orantılı yapılır.
    *   *Kural:* Alan (Area) algısı ile Yarıçap (Radius) algısına dikkat edilmelidir. İnsanlar alanı algılar. Değeri 2 katına çıkarmak için yarıçapı $\sqrt{2}$ katına çıkarmak gerekir, 2 katına değil. Aksi halde devasa düğümler oluşur.
2.  **Renk (Color) = Gruplama:** Düğümün rengi, genellikle ait olduğu **Topluluk (Modularity Class)** veya bir kategori (Örn: Cinsiyet, Departman) ile belirlenir.
    *   *Kural:* Renk paleti seçimi önemlidir. Renk körleri için uygun paletler (ColorBrewer) kullanılmalıdır. Zıt renkler kümeleri ayırır.
3.  **Kenar Kalınlığı (Weight):** İlişkinin gücünü gösterir. Ancak çok kalın kenarlar görüntüyü bozar. Genellikle opaklık (transparency) ile birlikte kullanılır. Zayıf bağlar daha şeffaf çizilir.

### 3.4. Hairball (Tüy Yumağı) Sendromu ve Çözümü
Nod sayısı 1000'i geçtiğinde, Force-directed algoritmalar genellikle ekranın ortasında siyah, anlamsız bir düğüm/kenar yığını (Tüy yumağı) oluşturur. Hiçbir şey okunamaz.
**Çözüm Stratejileri:**
1.  **Filtreleme:** En önemli düğümleri (Giant Component) tut, tekil (degree=0 veya 1) düğümleri gizle. En güçlü kenarları tut, zayıf bağları gizle.
2.  **Omurga Çıkarma (Backbone Extraction):** İstatistiksel olarak anlamsız bağları sil (Disparity Filter).
3.  **Kenar Demetleme (Edge Bundling):** Aynı yöne giden otoban şeritlerini birleştirmek gibi, kenarları sanatsal bir şekilde birleştirerek (kavis vererek) görsel karmaşayı azaltma. Havayolu uçuş haritalarında sıkça kullanılır.

### 3.5. Diğer Layout Türleri
*   **Coğrafi (GeoLayout):** Eğer düğümlerin enlem/boylam bilgisi varsa, harita üzerine yerleştirilir. (Fizik motoru kullanılmaz).
*   **Circular (Çembersel):** Düğümler bir daireye dizilir. Bağlantılar içinden geçer. Hiyerarşiyi göstermez ama bağlantı yoğunluğunu gösterir.
*   **Hive Plot:** Düğümleri eksenlere dizerek rasyonel ve karşılaştırılabilir bir görselleştirme sunar. Hairball sorununa analitik bir çözümdür.

## 🔑 4. Anahtar Kavramlar Sözlüğü
*   **Layout (Düzen):** Düğümlerin uzaydaki konumunu $(x,y)$ belirleme algoritması.
*   **Force-Directed:** Fiziksel kuvvetlere (itme ve çekme) dayalı yerleşim.
*   **Visual Encoding:** Veriyi görsel değişkene (renk, boyut, şekil) dönüştürme kuralı.
*   **Hairball:** Aşırı kenar yoğunluğu nedeniyle okunamayan, karman çorman ağ görselleştirmesi.
*   **Edge Bundling:** Kenarları gruplayarak ve bükerek görsel sadelik sağlama tekniği.

## 🛠 5. Kaynaklar ve İleri Okuma Önerileri
### Araçlar
*   **Gephi:** Bu işin Photoshop'udur. Mutlaka öğrenilmesi gerekir. ForceAtlas2 algoritmasını deneyeceğiz.
*   **Cytoscape:** Biyolojik ağlar için standarttır.
*   **VOSviewer:** Bibliyometrik (akademik atıf) ağları için özelleşmiş harika bir araçtır.
*   **D3.js / Sigma.js:** Web tabanlı interaktif görselleştirmeler için JavaScript kütüphaneleri.

### Okumalar
*   **"Visualizing Data"** - William Cleveland.
*   **Tufte, E. R.** - "The Visual Display of Quantitative Information" (Veri görselleştirme felsefesi). Klasik bir eserdir; "Chartjunk" (Grafik çöplüğü) kavramını anlatır. Az mürekkeple çok bilgi vermeyi hedefler.

## 🎯 6. Haftanın Özeti ve Gelecek Haftaya Bakış
Bu hafta, ağları "görmeyi" öğrendik. İyi bir görselleştirmenin sadece "güzel" değil, aynı zamanda "doğru" ve "okunabilir" olması gerektiğini anladık. Layout algoritmalarının fiziğini keşfettik.
Artık teorik kısmın sonuna geldik ve pratik (tooling) kısmına güçlü bir giriş yapacağız. Gelecek hafta, bu derste öğrendiğimiz her şeyi uygulamak için kullanacağımız yazılımları (**Pajek, UciNet, Netdraw**) kuracak, arayüzlerini ve veri formatlarını öğreneceğiz. "Fareyi kullanarak" analiz yapmaya hazır olun.
