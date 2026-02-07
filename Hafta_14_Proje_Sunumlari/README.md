# Hafta 14: Proje Sunumları ve Sosyal Ağ Analizinin Geleceği

## 📌 1. Ders Hakkında ve Giriş
Ve geldik yolun sonuna. Veya Winston Churchill'in dediği gibi, "Bu bir son değil, belki de sonun başlangıcı." 13 hafta boyunca, Königsberg'in köprülerinden Google'ın sunucularına, Medici ailesinin entrikalarından Twitter'daki yankı odalarına kadar uzun bir yolculuk yaptık. Dünyaya artık sadece "insanlar" veya "nesneler" olarak değil, "bağlantılar" ve "sistemler" olarak bakıyorsunuz.

Bu son hafta, sahne sizindir. Öğrenciler (veya proje ekipleri), dönem boyunca üzerinde çalıştıkları sosyal ağ analizi projelerini sunacaklardır. Bu sunumlar, teorik bilginin pratik bir probleme nasıl uygulandığının birer kanıtı olacaktır.

Ayrıca dersin ikinci yarısında, **Ağ Biliminin Geleceği**ni tartışacağız. Yapay Zeka (AI) ve Derin Öğrenme (Deep Learning) ile ağ analizinin birleşimi (Graph Neural Networks), zamanla değişen dinamik ağlar ve büyük veri teknolojileri bizi nereye götürüyor?

## 📚 2. Proje Sunum Formatı ve Beklentiler
Her bir sunum 15-20 dakika sürecek ve profesyonel bir iş sunumu ciddiyetinde olacaktır. Şu akışı izlemeniz beklenir:

1.  **Problem Tanımı (The "Why"):**
    *   Neden bu ağı seçtiniz? Merakınızı cezbeden neydi? (Örn: "Türk dizilerindeki oyuncu kadrolarının kapalılığını -aynı yüzlerin dönüp dönmediğini- merak ettim" veya "Bitcoin işlem ağındaki kara para aklama desenlerini bulmak istedim").
    *   Hipoteziniz neydi?
2.  **Veri Hikayesi (The "How"):**
    *   Veriyi nereden ve nasıl buldunuz? (Scraping, API, Hazır veri).
    *   Karşılaştığınız zorluklar (Veri temizliği, eksik veri, Türkçe karakter sorunları) ve bunları nasıl aştınız?
    *   Ağın boyutları (N düğüm, E kenar) ve türü.
3.  **Metodoloji ve Analiz (The "What"):**
    *   Hangi metrikleri kullandınız? Neden o metriği seçtiniz? (Örn: "Lideri bulmak için PageRank kullandım çünkü bu ağda yönlendirme önemliydi...").
    *   Topluluk tespiti yaptınız mı? Çıkan gruplar gerçek hayatta neye karşılık geliyor?
4.  **Bulgular ve Görseller (The "Wow"):**
    *   Ağın görsel haritası (Hairball olmamalı, temiz, renkli ve etiketli olmalı).
    *   Sizi şaşırtan bir sonuç oldu mu? ("X kişisinin bu kadar önemli olduğunu hiç düşünmemiştik").
5.  **Sonuç ve Tartışma:**
    *   Bu analiz gerçek dünyada kime, ne fayda sağlar? (Bir pazarlamacıya mı, bir doktora mı, polise mi?).
    *   Gelecekte bu çalışma nasıl geliştirilebilir?

## 📝 3. Değerlendirme Kriterleri
Proje notlandırılırken aşağıdaki rubrik (dereceli puanlama anahtarı) kullanılacaktır:

1.  **Teknik Yetkinlik (%40):**
    *   Kavramların doğru kullanımı (Degree ile Betweenness'ı karıştırmamak).
    *   Analiz araçlarının (Gephi/Python/UciNet) etkin ve doğru kullanımı.
    *   Matematiksel doğruluk.
2.  **Yorumlama ve İçgörü (%30):**
    *   Sadece sayıları listelemek yerine ("Çap=4"), bunun ne anlama geldiğini açıklamak ("Bilgi çok hızlı yayılıyor").
    *   Gerçek dünya bağlamıyla ilişki kurmak.
3.  **Görselleştirme ve Sunum (%20):**
    *   Slaytların kalitesi ve düzeni.
    *   Ağ grafiklerinin okunabilirliği ve estetiği (Renk, boyut, yerleşim).
    *   Anlatım akıcılığı ve zaman yönetimi.
4.  **Yaratıcılık ve Zorluk (%10):**
    *   Orijinal bir veri seti mi toplandı yoksa çok bilinen (Karate Club vb.) bir veri mi kullanıldı?
    *   Sıradışı, cesur bir soru soruldu mu?

## 🚀 4. Ufuk Turu: SAA'nın Geleceği
Dersimizi bitirirken, bu alanın nereye gittiğine dair vizyoner bir bakış atalım.

### 4.1. Graph Neural Networks (GNN)
Klasik Makine Öğrenmesi (Machine Learning), veriyi tablolar (Excel gibi satır-sütun) halinde sever. Ancak ağlar tablo değildir; düzensizdir. Son yıllarda geliştirilen **Graph Neural Networks (GNN)** ve **Graph Embeddings (Node2Vec, GraphSAGE)** teknolojileri, ağ yapısını yapay zeka modellerine beslemeyi başarmıştır.
*   *Uygulama:* Pinterest'in öneri sistemi, Google Haritalar'ın tahmini ("Buradan gidersen 5 dk kazanırsın"), İlaç keşfi (Molekül ağlarını analiz ederek yeni antibiyotikler bulmak). SAA ile Deep Learningin evliliği, gelecek 10 yılın en büyük trendidir.

### 4.2. Dinamik Ağ Analizi (Dynamic/Temporal Networks)
Bu derste ağları hep "fotoğraf" (statik) gibi inceledik. Oysa ağlar "film" gibidir; sürekli yeni kenarlar oluşur ve kopar. Zaman boyutunun analize katılması (Temporal Networks), şu an akademinin en sıcak konusudur. "Zaman içinde topluluklar nasıl evrilir?" sorusu, statik analizden çok daha zordur ama daha gerçekçidir.

### 4.3. Çok Katmanlı Ağlar (Multiplex Networks)
İki insan arasında sadece bir tür bağ yoktur. Hem arkadaştırlar, hem iş arkadaşıdırlar, hem komşudurlar. Bu farklı katmanların üst üste binmesi (Multiplex), yayılım dinamiklerini tamamen değiştirir. Örneğin iş arkadaşınızdan hastalık kapabilirsiniz (fiziksel katman) ama ondan politik fikir kapmayabilirsiniz (sosyal katman). Bu katmanları ayrı ayrı modelleyip aralarındaki etkileşimi incelemek yeni bir sınırdır.

## 🔑 5. Dönem Sonu Özeti: Ne Kazandık?
Bu dersi başarıyla tamamlayan bir öğrenci:
1.  Dünyayı **sistemik** bir bakış açısıyla (bütünsel) görür.
2.  "Popülerlik" ile "Etki" arasındaki farkı matematiksel olarak bilir.
3.  Karmaşık bir veri yığınından anlamlı sosyal grupları çıkarabilir.
4.  Viral olayların, salgınların ve krizlerin arkasındaki mekanizmayı anlar.
5.  Veriye dayalı strateji geliştirebilir.

## 🛠 6. Mezuniyet Sonrası Kaynaklar
Öğrenme yolculuğunuz burada bitmiyor. İlerlemek isteyenler için:
*   **Konferanslar:** Sunbelt (INSNA Conference), NetSci (Network Science Society).
*   **Dergiler:** *Social Networks*, *Network Science*, *Nature Human Behaviour*.
*   **Topluluk:** INSNA (International Network for Social Network Analysis).

Hepinize katılımınız için teşekkür eder, "bağlantılı" bir hayat dilerim. Unutmayın, ağınız kaderinizdir (Your network is your net worth).
