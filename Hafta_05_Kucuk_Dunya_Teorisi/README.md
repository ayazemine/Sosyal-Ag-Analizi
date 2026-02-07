# Hafta 5: Küçük Dünya Teorisi (Small World Theory)

## 📌 1. Ders Hakkında ve Giriş
"Dünya ne kadar küçük!" Bu cümleyi hayatımızda en az bir kez, hiç beklemediğimiz bir yerde ortak bir tanıdıkla karşılaştığımızda kurmuşuzdur. Bir tatilde, uçakta veya yeni başladığınız bir iş yerinde, eski ilkokul arkadaşınızın kuzeniyle karşılaşırsınız. Peki bu sadece ilginç bir tesadüf mü, yoksa sosyal ağların temel matematiksel bir özelliği mi?

Geçen hafta Erdős-Rényi rastsal ağ modelini inceledik ve iki önemli sonuç bulduk:
1.  Rastsal ağlar "küçük dünya" özelliğine sahiptir (ortalama yol uzunluğu kısadır).
2.  Ancak rastsal ağlar "kümeleme" (clustering) özelliğine sahip **değildir**.

Oysa gerçek hayata baktığımızda bir paradoks görürüz:
*   Arkadaşlarımız genellikle birbirini tanır (Yüksek Kümeleme - Düzenli ağ özelliği). İnsanlar "klikler" halinde yaşar.
*   Buna rağmen, dünyanın öbür ucundaki birine ulaşmak şaşırtıcı derecede kısa sürer (Kısa Yol Uzunluğu - Rastsal ağ özelliği).

Bu hafta, 1998 yılında Duncan Watts ve Steven Strogatz'ın bu paradoksu nasıl çözdüğünü ve modern ağ bilimini başlatan **Watts-Strogatz (WS) Modeli**ni inceleyeceğiz. Ayrıca Stanley Milgram'ın meşhur mektup deneyine, "Kevin Bacon Sayısı" oyununa ve bu teorinin salgın hastalıkların yayılımını nasıl açıkladığına değineceğiz.

## 📚 2. Konu Başlıkları ve Haftalık Akış
1.  **Small World (Küçük Dünya) Fenomeni**
    *   Tarihsel Köken: Karinthy'nin "Zincirler" öyküsü (1929).
    *   Stanley Milgram'ın Mektup Deneyi (1967).
    *   Six Degrees of Separataion (Altı Derece Ayrım) kavramı.
2.  **Watts-Strogatz Modeli (1998)**
    *   Düzenli Ağlar (Regular Lattices) ve özellikleri.
    *   Yeniden Kablolama (Rewiring) süreci ($p$ parametresi).
    *   Düzen ve kargaşanın arasındaki hassas denge.
3.  **Matematiksel Özellikler**
    *   Ortalama Yol Uzunluğu ($L(p)$) değişimi.
    *   Kümeleme Katsayısı ($C(p)$) değişimi.
    *   Small-World Bölgesi: Yüksek $C$, Düşük $L$.
4.  **Gerçek Hayattan Örnekler**
    *   C. Elegans sinir sistemi ağı.
    *   ABD Elektrik Şebekesi (Power Grid).
    *   Film Oyuncuları Ağı (Hollywood).

## 📝 3. Detaylı İçerik

### 3.1. Deneyler ve Popüler Kültür

#### Milgram'ın Deneyi (1967)
Harvard'lı sosyal psikolog Stanley Milgram, Nebraska ve Kansas'ta yaşayan rastgele insanlara birer mektup ve Boston'da yaşayan bir borsacının bilgilerini verdi. Katılımcılara şu talimat verildi: "Bu kişiyi tanıyorsan mektubu ona gönder. Tanımıyorsan, onu tanıması en muhtemel olan tanıdığına gönder."
Beklenti, mektupların yüzlerce el değiştireceği veya kaybolacağıydı. Ancak hedefe ulaşan mektuplar ortalama **5.5 - 6 adımda** yerine varmıştı. Bu sonuç şok ediciydi: Devasa ABD nüfusu içinde herhangi iki kişi arasında sadece 6 kişi vardı. Milgram buna "Küçük Dünya Problemi" adını verdi. Daha sonra "Altı Derece" (Six Degrees) kavramı popüler kültüre yerleşti. 2000'lerde Microsoft Messenger verileriyle yapılan devasa deney de bu sayıyı 6.6 olarak doğruladı.

#### Kevin Bacon Oyunu
Hollywood filmlerindeki oyuncu ağında, herkesin ünlü aktör Kevin Bacon'a olan uzaklığı (birlikte film oynama bağı) hesaplanır. Çoğu oyuncunun "Bacon sayısı" 2 veya 3 çıkar. Bacon sayısı 4 olan birini bulmak zordur. Aslında bu sadece Bacon'a özgü değildir; herhangi bir "hub" (merkez) seçilseydi de sonuç değişmezdi, ancak oyun bu teoriyi halka anlatmak için harika bir araç olmuştur.

### 3.2. Watts-Strogatz Modelinin İnşası

Watts ve Strogatz, doktora çalışmaları sırasında cırcır böceklerinin senkronize ötmesini araştırırken bu ağ problemine daldılar. Kendi modellerini kurmak için iki uç durumu birleştirdiler:

1.  **Tam Düzenli Ağ (Regular Ring Lattice):** İnsanların bir çember etrafında el ele tutuştuğunu düşünün. Herkes sadece sağındaki ve solundaki 2 kişiyle (toplam $k$ komşu) bağlıdır.
    *   **Kümeleme:** Yüksektir. Komşumun komşusu benim de yakınımdır.
    *   **Yol Uzunluğu:** Çok uzundur. Çemberin bir ucundan diğerine gitmek için herkesin üzerinden tek tek geçmek gerekir ($N/2k$ adım).

2.  **Tam Rastsal Ağ (Random Graph):** Bağlar rastgeledir.
    *   **Kümeleme:** Düşüktür (Sıfıra yakındır).
    *   **Yol Uzunluğu:** Çok kısadır (Logaritmik).

**Soru:** Hem kümelemesi yüksek (düzenli gibi) hem de yol uzunluğu kısa (rastsal gibi) bir ağ mümkün mü?
**Çözüm (Rewiring):** Düzenli bir çember ağını alalım. Her kenarı $p$ olasılığı ile koparıp, rastgele uzak bir düğüme bağlayalım (Yeniden Kablolama).
*   $p = 0$: Düzenli ağ.
*   $p = 1$: Rastsal ağ.
*   **$0 < p < 1$ (Ara Bölge):** İşte sihir burada gerçekleşir!

### 3.3. Küçük Dünya 'nın Matematiği
$p$ değerini çok az artırdığımızda (örneğin $p=0.01$, yani bağların sadece %1'ini rastgele değiştirdiğimizde):
1.  **Yol Uzunluğu ($L$) ÇAKILIR:** Aniden düşer. Çünkü eklenen tek bir "uzun menzilli köprü" (shortcut), çemberin zıt uçlarını birbirine bağlar. Sadece o iki ucun değil, o uçlara yakın olan herkesin mesafesini kısaltır.
2.  **Kümeleme ($C$) DEĞİŞMEZ:** Hala yüksektir. Çünkü bağların %99'u hala yereldir, yani arkadaş grubu yapısı bozulmamıştır.

İşte bu aralığa **"Small-World Regime"** denir:
$$ L(p) \approx L_{random} $$
$$ C(p) \approx C_{regular} $$

Bu model, gerçek sosyal ağları mükemmel açıklar: Hepimiz yerel kümelerimizde (aile, iş, mahalle) yaşarız (Yüksek Kümeleme). Ancak aramızdan bazılarının farklı şehirden, farklı ülkeden bir arkadaşı vardır (Kestirme Yol). Bu az sayıdaki kestirme yol, tüm dünyayı birbirine bağlar.

### 3.4. Stratejik Ağ Oluşumu ve Zayıf Bağlar
Bu model, Granovetter'in "Zayıf Bağların Gücü" teorisiyle de matematiksel olarak uyumludur. Modeldeki "yeniden kablolanan" (rewired) uzun menzilli bağlar, sosyal hayattaki "zayıf bağlarımızı" temsil eder. Yakın çevremizle sıkı fıkı (güçlü) bağlarımız varken, uzaktaki tanıdıklarımız (zayıf bağlar) bizi dünyanın geri kalanına bağlar. Eğer zayıf bağlarınızı silerseniz, dünya aniden parçalanır ve "büyür".

### 3.5. Uygulamalar
*   **Beyin Ağları:** Nöronlar enerji tasarrufu için genellikle komşularıyla (yerel) bağlantı kurar. Ancak beynin farklı lobları arasında bilgi entegrasyonu için uzun menzilli aksonlara (kestirme yollara) ihtiyaç vardır. Beyin optimum bir "Small World"dür.
*   **Elektrik Şebekeleri:** Evler komşu trafolara bağlıdır (yerel), ama yüksek gerilim hatları uzak bölgeleri ve şehirleri bağlar (kestirme).
*   **Salgınlar:** Bir virüs yerel bir kümede başlar (yüksek kümeleme ile hızla yayılır), sonra bir kişi "kestirme yol" kullanarak uçağa biner ve virüsü başka bir kıtaya taşır (kısa yol uzunluğu). WS modeli, salgınların neden hem yerel patlamalar yaptığını hem de küresel yayıldığını açıklar. COVID-19'un yayılımı tam bir Small World örneğidir.

## 🔑 4. Anahtar Kavramlar Sözlüğü
*   **Small World Network (Küçük Dünya Ağı):** Hem yüksek kümeleme katsayısına hem de kısa ortalama yol uzunluğuna sahip ağ.
*   **Rewiring (Yeniden Kablolama):** Bir ağdaki bağın ucunun değiştirilerek başka bir düğüme bağlanması işlemi.
*   **Shortcut (Kestirme Yol):** Ağın topolojik olarak uzak iki bölgesini birbirine bağlayan kenar.
*   **Regular Lattice (Düzenli Kafes):** Her düğümün aynı sayıda komşuya sahip olduğu, son derece düzenli yapı.

## 🛠 5. Kaynaklar ve İleri Okuma Önerileri
### Makale
*   **Watts, D. J., & Strogatz, S. H. (1998).** "Collective dynamics of 'small-world' networks". *Nature*, 393(6684), 440-442. (Bu makale modern ağ biliminin en çok atıf alan makalelerinden biridir).

### Kitaplar
*   **"Six Degrees: The Science of a Connected Age"** - Duncan Watts: Yazarın kendi keşif sürecini anlattığı harika bir kitaptır.

### Araçlar
*   **NetLogo "Small World" Modeli:** $p$ değerini (rewiring probability) kaydırıcı ile 0'dan 1'e doğru yavaşça artırarak, grafikte kümelemenin sabit kalırken yol uzunluğunun nasıl düştüğünü mutlaka gözlemleyin.

## 🎯 6. Haftanın Özeti ve Gelecek Haftaya Bakış
Bu hafta, düzenli ve rastgele ağların özelliklerini birleştirerek gerçek dünyayı modelleyebileceğimizi gördük. WS modeli, "Kısa Yol" ve "Kümeleme" sorununu çözdü.
ANCAK, WS modelinin de çözemediği bir sorun var: **Derece Dağılımı**.
WS modelinde tüm düğümler hala yaklaşık olarak eşit derecelidir (Poisson dağılımı). Oysa biliyoruz ki gerçek dünyada "Hub"lar (milyonlarca bağlantısı olanlar) var. WS modeli, Google'ı, İnternet'in kendisini veya Hollywood yıldızlarını açıklayamaz. Çünkü WS modeli ağın "büyüdüğünü" hesaba katmaz, düğüm sayısı sabittir.
Gelecek hafta, "Zengin daha da zenginleşir" (Rich get richer) mekanizmasını ve Albert-László Barabási'nin **Ölçeksiz Ağlar (Scale-Free Networks)** modelini inceleyerek ağ modelleri serimizi tamamlayacağız.
