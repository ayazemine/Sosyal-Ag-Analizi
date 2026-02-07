# Hafta 11: Sosyal Ağ Analizi Yazılımları (Pajek, UciNet, Netdraw)

## 📌 1. Ders Hakkında ve Giriş
Şimdiye kadar tahtada (matematik) veya zihinde (teori) yaptığımız her şeyi, şimdi bilgisayar ekranında yapma zamanı. Sosyal Ağ Analizi için geliştirilmiş yüzlerce araç vardır. Bazıları kodlama bilgisi gerektirir (Python/R), bazıları ise "Tıkla ve Çalıştır" (Point-and-Click) mantığıyla çalışan paket programlardır.

Bu dersin amacı, sizi kod yazmak zorunda bırakmadan, akademik ve profesyonel dünyada en çok kabul gören SAA yazılımları ile tanıştırmaktır. Bir programlama dili bilmek (Python gibi) büyük avantajdır, ancak SAA'nın köklü yazılımları (Pajek, UciNet) hala birçok konuda koddan daha hızlı ve pratiktir. Bu hafta üç efsanevi aracı inceleyeceğiz:
1.  **UciNet:** Sosyal bilimcilerin İsviçre çakısı. Matris matematiğinde çok güçlüdür.
2.  **Netdraw:** UciNet'in görselleştirme ortağı. Hızlı ve analitik çizimler için idealdir.
3.  **Pajek:** "Örümcek" (Slovence). Çok büyük ağları (milyonlarca düğüm) analiz etmek için yaratılmış bir matematik canavarıdır.

Bu yazılımlar arayüz olarak "eski moda" (Windows 95 stili) görünebilirler. Ancak sakın görünüşe aldanmayın; arka planda koşan algoritmaları son derece güçlü, akademik olarak doğrulanmış (bug-free) ve bilimsel makalelerde standart kabul edilen araçlardır.

## 📚 2. Konu Başlıkları ve Haftalık Akış
1.  **Yazılım Ekosistemi: Hangi Araç Ne İçin?**
    *   GUI (Arayüzlü) Araçlar vs. Scripting (Kodlama).
    *   Veri formatları karmaşası: `.dl`, `.net`, `.gephi`, `.csv`, `.gml`.
    *   Dönüştürücüler (Converters).
2.  **UciNet'e Derin Dalış**
    *   Matris editörü (Spreadsheet) kullanımı.
    *   Veri dönüştürme (Transformations): Simetrize etme, Binarize etme (0/1), Transpoz alma.
    *   Temel Analizler: Merkezilik, Yoğunluk, Klikler, K-Cores.
3.  **Netdraw ile Görselleştirme**
    *   Nitelik (Attribute) tabanlı görselleştirme (Cinsiyete göre renk, yaşa göre boyut).
    *   Filtreleme (Ego network analizi).
    *   Görseli dışarı aktarma (Metafile/JPEG).
4.  **Pajek: Büyük Ağların Efendisi**
    *   Ağ (Network), Bölüntü (Partition) ve Vektör (Vector) dosyaları mantığı.
    *   Pajek ile "Ada" (Island) analizi ve büyük ağların indirgenmesi.

## 📝 3. Detaylı İçerik

### 3.1. Veri Formatları ve Hazırlık
Her yazılımın kendi dili vardır. Analistin en çok zaman harcadığı iş, veriyi bir formattan diğerine çevirmektir.
*   **Excel / CSV:** Ham veri genelde buradadır. İki sütun (Kaynak, Hedef) şeklindedir.
*   **DL (Data Language):** UciNet'in formatıdır. Metin tabanlıdır, matrisi tanımlar (`N=5 FORMAT=FULLMATRIX DATA:`).
*   **NET:** Pajek'in formatıdır. `*Vertices` (Düğümler) ve `*Edges` (Kenarlar) başlıkları ile listelerden oluşur. Oldukça yalındır.
*   **GML / GraphML:** XML tabanlı modern formatlar (Gephi sever).

**İpucu:** UciNet, Excel verisini (Edge List) `.dl` formatına çeviren çok iyi bir "Import" aracına sahiptir. Ayrıca `Statnet` (R) ve `NetworkX` (Python) arasında köprü görevi görür.

### 3.2. UciNet: Analiz Motoru
Steve Borgatti, Martin Everett ve Linton Freeman (SAA'nın babaları) tarafından geliştirilmiştir.
*   **Matris Cebiri:** UciNet, ağları matris olarak görür. $A \times A$ (Matris çarpımı) yaparak "iki adımlı yolları" bulabilirsiniz. Transpozunu alarak ($A^T$) yönleri ters çevirebilirsiniz. Matrisleri toplayarak farklı ağları (örneğin Arkadaşlık + İş Ortaklığı) tek bir "İlişki" matrisinde birleştirebilirsiniz.
*   **İstatistiksel Testler:** UciNet'in en büyük gücü **QAP (Quadratic Assignment Procedure)** Korelasyonudur. "Arkadaşlık ağı ile Borç verme ağı arasında ilişki var mı?" sorusunu klasik Pearson korelasyonu ile çözemezsiniz çünkü ağ verisi bağımsız değildir (Independence assumption ihlali). UciNet'teki QAP testi, binlerce permütasyon (rastgele karıştırma) yaparak doğru istatistiksel sonucu (p-value) verir. Bu özellik, onu akademik yayınlar için vazgeçilmez kılar.
*   **Ego Network:** Seçilen kişinin 1. derece ve 2. derece komşularını analiz eder.

### 3.3. Netdraw: UciNet'in Gözü
UciNet hesap yapar, sonucu sayısal tablo olarak verir. "Bunu çiz" dediğinizde Netdraw açılır.
Netdraw'ın en güçlü yanı, **Nitelik (Attribute)** verilerini görselleştirmeye entegre etmesidir. VDL (Visual Data Language) dosya yapısını kullanır.
*   Bir Excel dosyasından "Cinsiyet, Yaş, Departman" verilerini yükleyebilirsiniz.
*   "Nodes -> Color by Attribute -> Department" diyerek anında departmanları renklendirebilirsiniz.
*   "Nodes -> Size by Attribute -> Centrality" diyerek önemli kişileri büyütebilirsiniz.
*   **Ego Network:** Özelliği ile, seçtiğiniz bir kişinin (örneğin Ahmet) sadece kendi yakın çevresini (1 adım komşuları) izole edip inceleyebilirsiniz. Ahmet'i ortadan kaldırırsanız bu çevre dağılır mı? (Structural Hole testi).

### 3.4. Pajek: Verimlilik ve Ölçek
Vladimir Batagelj (matematikçi) tarafından geliştirilmiştir. UciNet'in zorlandığı (hafıza hatası verdiği) yüz binlerce düğümlü ağlarda Pajek "bana mısın" demez. Felsefesi "Nesne tabanlı"dır ve dosyaları ayırır:
1.  **Network (.net):** Ağın kendisi (Çizgiler).
2.  **Partition (.clu):** Kategorik veri (Sınıflar, Topluluklar). (Her düğüm için bir tamsayı: 1, 2, 1, 3...).
3.  **Vector (.vec):** Sayısal veri (Merkezilik skorları). (Her düğüm için bir ondalıklı sayı: 0.12, 0.45...).

Pajek'te işlemler bu nesneler arasında yapılır: "Network" ile "Vector"ü kullanarak "Cores" (Çekirdek) analizi yap, sonucu yeni bir "Partition" olarak kaydet. Sonra "Draw-Partition" diyerek çiz. Bu modüler yapı, karmaşık analiz zincirleri kurmayı sağlar.
*   **Island (Ada) Analizi:** Ağırlıklı ağlarda (örneğin ticaret), sadece belirli bir tutarın üzerindeki bağları bırakıp "adaları" ortaya çıkarma tekniği.

## 🔑 4. Anahtar Kavramlar Sözlüğü
*   **GUI (Graphical User Interface):** Grafik arayüz. Kod yazmadan butonlarla işlem yapma.
*   **QAP (Quadratic Assignment Procedure):** Ağ verileri arasındaki korelasyonu test etmek için kullanılan özel istatistiksel yöntem (Permütasyon testi).
*   **Ego Network:** Odaklanılan bir düğüm (Ego) ve onun doğrudan bağlantıları (Alters) ile oluşan alt ağ.
*   **2-Mode Network (Bipartite):** UciNet'te satır ve sütunların farklı varlıklar olduğu (Kişi x Etkinlik gibi) dikdörtgen matrisler.
*   **Partition:** Düğümleri sınıflara ayıran (kümeleyen) veri yapısı.

## 🛠 5. Kaynaklar ve İleri Okuma Önerileri
### İndirme Linkleri
*   **UciNet:** (30/90 gün deneme sürümü mevcuttur). Windows tabanlıdır (Mac için emülatör/Parallels gerekir).
*   **Pajek:** Tamamen ücretsizdir (Windows).
*   **Gephi:** Modern alternatif (Java tabanlı, Mac/Windows/Linux).

### Kılavuzlar
*   **"Exploratory Social Network Analysis with Pajek"** - Nooy, Mrvar, Batagelj: Pajek'i öğrenmek için yazılmış en iyi "yemek kitabı" (cookbook) tarzı eserdir. Adım adım uygulatır.
*   **Hanneman & Riddle's "Introduction to Social Network Analysis":** UciNet ekran görüntüleriyle anlatılan ücretsiz online ders notları. SAA öğrenen herkesin başucu kaynağıdır.

## 🎯 6. Haftanın Özeti ve Gelecek Haftaya Bakış
Bu hafta, alet çantamızı doldurduk. Artık bir ağ verisi geldiğinde hangi programı açacağımızı, veriyi nasıl formatlayacağımızı ve temel düğmelere nerede basacağımızı biliyoruz. Teori ve aracı birleştirdik.
Peki bu veri nereden gelecek? Gökten zembille inmeyecek. Gelecek hafta, sahaya ineceğiz. Twitter'dan tweet çekeceğiz, web sitelerini kazıyacağız (Scraping) veya anket yapacağız. "Kirli" veriyi toplayıp, temizleyip, analize hazır hale getirme süreci (**Veri Toplama ve Ön İşleme**) bizi bekliyor.
