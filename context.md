# Sosyal Ağ Analizi Dersi - Ders İçeriği Bağlamı

## Genel Bilgiler
- **Ders Adı:** Sosyal Ağ Analizi
- **Seviye:** Lisans
- **Süre:** 14 Hafta
- **Haftalık Ders Saati:** 3 Saat (Teorik)
- **Dil:** Türkçe

## Dersin Amacı
Sosyal Medya Ağları üzerindeki insan, bilgi, olay ve yer gibi olgular arasındaki ilişkileri inceleyerek, bu ilişkiler topluluğunu ağ olarak analiz edip faydalı bilgileri bulup çıkartmak ve bu bilgilere dayalı olarak sosyal ağlar üzerinde gerçekleşen durumları açıklamaya yardımcı olmak. Ders, hem teorik temelleri hem de hesaplama araçlarını kullanarak günümüzde internet üzerinden ulaşılabilen sosyal medya ve bilgi ağları ile ilgili anlamlı bilgilerin çıkartılabilmesini sağlayacaktır.

## Dersin Kapsamı
Ders, sosyal ağ analizinin temel kavramlarından başlayarak ileri düzey uygulamalara kadar geniş bir yelpaze sunmaktadır:
- Sosyal ağ analizi temel kavramları (düğümler, ilişkiler, komşuluk matrisleri, düğüm dereceleri)
- Matematiksel ve istatistiksel ağ modelleri
- Ağ merkezliği ve prestij ölçümleri
- Rastsal ve küçük dünya ağ modelleri
- Sanal topluluk yapıları ve kümeleme teknikleri
- Sosyal medyada görüş oluşumu, koordinasyon ve işbirliği dinamikleri
- Ağ görselleştirme teknikleri
- Uzman yazılımlarla pratik uygulamalar (Pajek, Netdraw, UciNet)
- Gerçek dünya sosyal medya ağlarının analizi

## Haftalık İçerik Yapısı

### Temel Kavramlar ve Giriş (Hafta 1-3)
- **Hafta 1:** Sosyal medya ve bilgi ağlarının tanımı; ağ bilimi neden önemli; tarihsel gelişim; uygulama alanları (epidemiyoloji, pazarlama, organizasyon teorisi, sosyoloji)
- **Hafta 2:** Düğüm (node/vertex) ve kenar (edge/link) kavramları; yönlü ve yönsüz ağlar; ağırlıklı ağlar; komşuluk matrisi (adjacency matrix); derece dağılımı (degree distribution)
- **Hafta 3:** Merkezilik ölçüleri: derece merkezliği, arasındalık (betweenness), yakınlık (closeness), özvektor merkezliği (eigenvector centrality); PageRank algoritması; prestij kavramı

### Ağ Modelleri ve Teorisi (Hafta 4-6)
- **Hafta 4:** Ağ türleri (sosyal, bilgi, biyolojik, teknolojik); Erdős-Rényi rastsal ağ modeli; ağ oluşum süreçleri
- **Hafta 5:** Milgram'ın altı adım teorisi; Watts-Strogatz küçük dünya modeli; kümeleme katsayısı; ortalama yol uzunluğu; stratejik ağ formasyonu
- **Hafta 6:** Barabási-Albert tercihli bağlanma modeli (preferential attachment); ölçeksiz ağlar (scale-free networks); ağ optimizasyonu; gürbüzlük (robustness) ve kırılganlık (vulnerability)

### Ağ Değerlendirme ve Topluluk Analizi (Hafta 7-9)
- **Hafta 7:** Ağ yoğunluğu (density); çap (diameter); bileşen analizi; modülerlik (modularity); assortativity; geçişlilik (transitivity)
- **Hafta 8:** Sanal topluluk tanımı; topluluk tespit algoritmaları; Girvan-Newman algoritması; modülerlik maksimizasyonu; hiyerarşik kümeleme; k-clique percolation
- **Hafta 9:** Görüş dinamikleri modelleri; fikir birliği oluşumu; polarizasyon; koordinasyon oyunları; işbirliği ağları; bilgi yayılımı ve kaskadlar

### Görselleştirme ve Pratik Uygulamalar (Hafta 10-14)
- **Hafta 10:** Ağ görselleştirme prensipleri; düzen algoritmaları (force-directed, hierarchical, circular); görsel kodlama; interaktif görselleştirme
- **Hafta 11:** Pajek yazılımının kurulumu ve arayüz tanıtımı; Netdraw özellikleri; UciNet'in temel fonksiyonları; veri formatları (.net, .paj, .dl)
- **Hafta 12:** Gerçek veri seti üzerinde uygulama (örnek: Twitter etkileşim ağı, Facebook arkadaşlık ağı); veri toplama ve ön işleme; ağ oluşturma
- **Hafta 13:** Vaka çalışması devamı; merkezilik analizi; topluluk tespiti; görselleştirme; sonuçların yorumlanması
- **Hafta 14:** Öğrenci proje sunumları; dönem boyunca geliştirilen sosyal ağ analizi projelerinin değerlendirilmesi

## Öğrenme Hedefleri
Öğrenciler bu ders sonunda:
1. Sosyal ağ analizinin temel kavramlarını ve terminolojisini kavrayacak
2. Ağ yapılarını matematiksel olarak temsil edebilecek (matrisler, grafikler)
3. Farklı merkezilik ve prestij ölçümlerini hesaplayabilecek ve yorumlayabilecek
4. Rastsal ağ modellerini ve küçük dünya fenomenini anlayacak
5. Sanal topluluklarını tespit edebilecek ve analiz edebilecek
6. Sosyal ağlarda bilgi yayılımı ve görüş oluşumu süreçlerini modelleyebilecek
7. Ağ görselleştirme tekniklerini uygulayabilecek
8. Pajek, Netdraw ve UciNet gibi uzman yazılımları kullanabilecek
9. Gerçek dünya sosyal medya verilerini toplayıp analiz edebilecek
10. Ağ analizi sonuçlarını yorumlayarak anlamlı çıkarımlar yapabilecek

## Kullanılacak Araçlar ve Teknolojiler

### Uzman Sosyal Ağ Analizi Yazılımları
- **Pajek:** Büyük ağların analizi ve görselleştirmesi için ücretsiz program
- **Netdraw:** Ağ görselleştirme ve düzenleme yazılımı
- **UciNet:** Kapsamlı sosyal ağ analizi paketi

### Programlama ve Veri Analizi
- **Python:** NetworkX, igraph, graph-tool kütüphaneleri
- **R:** igraph, sna, statnet paketleri
- **Gephi:** Açık kaynak ağ görselleştirme platformu
- **Cytoscape:** Biyolojik ve sosyal ağ analizi

### Veri Toplama Araçları
- Twitter API
- Facebook Graph API
- Reddit API
- Web scraping araçları (BeautifulSoup, Scrapy)

## Temel Kavramlar Sözlüğü

### Ağ Yapısı
- **Düğüm (Node/Vertex):** Ağdaki birey, kurum veya varlık
- **Kenar (Edge/Link):** Düğümler arasındaki ilişki veya bağlantı
- **Komşuluk Matrisi (Adjacency Matrix):** Ağın matematiksel temsili
- **Derece (Degree):** Bir düğüme bağlı kenar sayısı

### Merkezilik Ölçüleri
- **Derece Merkezliği:** Doğrudan bağlantı sayısı
- **Arasındalık (Betweenness):** Kısa yollar üzerinde köprü olma
- **Yakınlık (Closeness):** Diğer düğümlere ortalama uzaklık
- **Özvektor Merkezliği:** Önemli düğümlere bağlı olma

### Ağ Özellikleri
- **Kümeleme Katsayısı:** Komşuların birbirine bağlı olma eğilimi
- **Çap (Diameter):** Ağdaki en uzun en kısa yol
- **Modülerlik:** Topluluk yapısının gücü
- **Yoğunluk (Density):** Gerçekleşen bağlantıların olası bağlantılara oranı

## Uygulama Alanları
- **Pazarlama:** Influencer tespiti, viral pazarlama, müşteri segmentasyonu
- **Sağlık:** Hastalık yayılımı, sağlık davranışları, epidemiyoloji
- **Güvenlik:** Terör ağları, suç organizasyonları, siber güvenlik
- **Organizasyon:** Şirket içi iletişim, bilgi akışı, liderlik yapıları
- **Politik Bilim:** Oy verme davranışları, siyasi polarizasyon, kampanya stratejileri
- **Bilim:** İşbirliği ağları, atıf ağları, bilgi üretimi

## Örnek Vaka Çalışmaları
- **Twitter Hashtag Ağları:** Politik olaylar sırasında bilgi yayılımı
- **Facebook Arkadaşlık Ağları:** Topluluk yapıları ve homofilî
- **LinkedIn Profesyonel Ağlar:** Kariyer hareketliliği ve iş bulma
- **Instagram Etkileyici Ağları:** Marka işbirlikleri ve erişim
- **Reddit Tartışma Ağları:** Görüş kutuplaşması ve echo chambers
- **Akademik İşbirliği Ağları:** Bilimsel üretkenlik ve multidisipliner çalışma

## Değerlendirme Yaklaşımı
Ders, teorik bilgi ile pratik uygulamayı dengeli şekilde birleştirmektedir. Öğrencilerden hem matematiksel temelleri kavramaları hem de uzman yazılımları kullanarak gerçek veri setleri üzerinde analiz yapmaları beklenmektedir. 14. haftada gerçekleştirilecek ödev sunumlarında öğrenciler, kendi seçtikleri bir sosyal ağı analiz ederek dönem boyunca öğrendikleri yöntemleri uygulayacaklardır.

## Önerilen Okuma ve Kaynaklar
- **Kitaplar:**
  - "Networks, Crowds, and Markets" - David Easley & Jon Kleinberg
  - "Social Network Analysis: Methods and Applications" - Stanley Wasserman & Katherine Faust
  - "Network Science" - Albert-László Barabási
- **Online Kaynaklar:**
  - Network Science kitabı (ücretsiz online): http://networksciencebook.com/
  - Stanford Network Analysis Platform (SNAP) veri setleri
  - Pajek Wiki ve tutorial'lar
- **Akademik Dergiler:**
  - Social Networks
  - Network Science
  - Journal of Social Structure