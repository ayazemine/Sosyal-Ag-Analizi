# Hafta 9: Bilgi Yayılımı, Görüş Dinamikleri ve Yankı Odaları

## 📌 1. Ders Hakkında ve Giriş
Ağların yapısını (Statik Analiz) anlamak önemlidir, ancak ağların asıl işlevi "taşıyıcı" olmalarıdır. Yollar (kenarlar) üzerinden araçlar (bilgi packetleri) akar. Sosyal ağlar üzerinden fikirler, dedikodular, moda, yenilikler, virüsler ve davranışlar yayılır.

*   Neden bazı YouTube videoları viral olurken diğerleri izlenmez?
*   Neden insanlar bilimsel gerçekler yerine sahte haberlere (Fake News) inanma eğilimindedir?
*   Toplum neden politik olarak kutuplaşır ve uzlaşamaz?
*   "Arkadaşlarınız ne yaparsa siz de onu yaparsınız" sözü ne kadar doğrudur?

Bu hafta, **Ağ Dinamikleri (Network Dynamics)** konusuna giriyoruz. Yayılım (Diffusion) ve Bulaşma (Contagion) modellerini inceleyeceğiz. Biyolojik virüslerin yayılımı (Basit Bulaşma) ile sosyal davranışların yayılımı (Karmaşık Bulaşma) arasındaki kritik farkı göreceğiz. Ayrıca "Eşik Modelleri" ile kitlesel davranışların (ayaklanmalar, moda akımları) nasıl tetiklendiğini anlayacağız.

## 📚 2. Konu Başlıkları ve Haftalık Akış
1.  **Yayılımın Doğası: Biyolojik vs. Sosyal**
    *   Epidemiyolojik Modeller: SI, SIS, SIR modelleri.
    *   Temel Üreme Sayısı ($R_0$) ve ağ yapısının etkisi.
2.  **Yeniliklerin Yayılımı (Diffusion of Innovations)**
    *   Everett Rogers'ın Yayılım Eğrisi (S-Curve).
    *   Yenilikçiler, Erken benimseyenler, Erken/Geç Çoğunluk ve Geride kalanlar (Laggards).
3.  **Sosyal Bulaşma (Social Contagion)**
    *   Basit Bulaşma (Tek temas yeterli).
    *   **Karmaşık Bulaşma (Complex Contagion):** Sosyal kanıt (Social Proof) ve takviye (Reinforcement) gerekliliği.
    *   Zayıf bağların karmaşık bulaşmadaki başarısızlığı.
4.  **Eşik Modelleri ve Kaskadlar (Cascades)**
    *   Granovetter'in Eşik Modeli (Threshold Model).
    *   Bilgi Kaskadları (Information Cascades) ve sürü psikolojisi.
5.  **Görüş Dinamikleri ve Kutuplaşma**
    *   Homofili + Sosyal Etki = Yankı Odaları (Echo Chambers).
    *   Filtre Baloncukları (Filter Bubbles).

## 📝 3. Detaylı İçerik

### 3.1. Virüsler Nasıl Yayılır? (SIR Modeli)
Klasik epidemiyolojide nüfus üç kompartmana ayrılır ve diferansiyel denklemlerle modellenir:
1.  **S (Susceptible):** Duyarlı, henüz hasta olmamış.
2.  **I (Infected):** Hasta ve bulaştırıcı.
3.  **R (Recovered):** İyileşmiş ve bağışıklık kazanmış (veya ölmüş).

Bir virüsün yayılıp salgına dönüşmesi $R_0$ (Basic Reproduction Number) değerine bağlıdır. $R_0$, bir hastanın ortalama kaç kişiye bulaştırdığını gösterir. $R_0 > 1$ ise salgın büyür.
*   **Hub'ların Rolü:** Klasik modeller herkesin herkese eşit bağlı olduğunu varsayar. Ancak Ağ Bilimi şunu gösterir: Ölçeksiz ağlarda (Scale-Free), salgın eşiği yotur (veya 0'a çok yakındır). Yani $R_0$ çok küçük olsa bile, virüs bir Hub'a bulaşırsa (Havalimanı gibi), anında tüm dünyaya yayılır. Bu yüzden aşılamada rastgele seçim yerine, en çok merkezi olan kişileri (Öğretmenler, doktorlar, kasiyerler) aşılamak çok daha etkilidir.

### 3.2. Sosyal Davranışlar Virüs Gibi midir? (Karmaşık Bulaşma)
Damon Centola'nın çığır açan çalışmaları, sosyal davranışların (sigarayı bırakmak, Facebook hesabı açmak, sokağa dökülmek) virüs gibi yayılmadığını gösterdi.
*   **Basit Bulaşma:** Grip virüsü için otobüste yanınızdaki kişinin hapşırması yeterlidir (Tek kaynak). Haberdeki dedikodu da böyledir.
*   **Karmaşık Bulaşma:** Bir arkadaşınızın "Bu film çok güzel" demesi sizi sinemaya götürmeye yetmeyebilir (Maliyet/Risk vardır). Ancak 3 farklı arkadaş grubunuzdan aynı şeyi duyarsanız (Çoklu kaynak / Sosyal Pekiştirme), o zaman ikna olursunuz.

**Paradoks:** Granovetter'in "Zayıf Bağlar"ı bilgi (basit) yayılımı için harikadır; uzağa gider. Ancak davranış (karmaşık) yayılımı için "Güçlü Bağlar" (Geniş köprüler) gerekir. Çünkü güven, inandırıcılık ve sosyal baskı, sadece sıkı örülmüş, kümeleme katsayısı yüksek gruplarda oluşur. Bir politik hareketin başlaması için zayıf bağlar yetmez, güçlü bağlar gerekir.

### 3.3. Granovetter'in Eşik Modeli (Threshold Model)
Neden sessiz bir kalabalık aniden bir isyana dönüşür? Veya neden herkes bir anda aynı model ayakkabıyı giymeye başlar?
Her bireyin bir **Eşik Değeri ($\tau$)** vardır: "Kabul etmeden önce arkadaşlarımın yüzde kaçının yapması gerekiyor?"
*   **Radikaller ($\tau=0$):** Kimse yapmasa da yapar (Eylemi başlatır).
*   **Erken Katılanlar ($\tau=20\%$):** Az bir grup yapınca katılır.
*   **Muhafazakarlar ($\tau=80\%$):** Neredeyse herkes yapmadan katılmaz (Sosyal baskı).

**Domino Etkisi (Cascade):** Ağ yapısı çok kritiktir. Eğer $\tau=0$ olan kişi, $\tau=10\%$ olan kişiye bağlıysa, o da $\tau=20\%$ olana bağlıysa... bir domino etkisi başlar ve tüm ağa yayılır (Global Cascade). Ancak arada bir "tıkanıklık" (yüksek eşikli/inatçı biri) varsa, yayılım durur.

### 3.4. Yankı Odaları ve Kutuplaşma
İnternet bize tüm bilgilere erişim imkanı sunsa da, insanlar neden giderek daha bağnaz hale geliyor?
1.  **Homofili:** Kendimiz gibi düşünenlerle bağ kurarız (Selection).
2.  **Sosyal Etki (Social Influence):** Bağlı olduğumuz kişilere benzemeye başlarız (Influence).

Bu iki mekanizma birleştiğinde **Yankı Odaları (Echo Chambers)** oluşur. Bir grubun içinde herkes aynı şeyi söyler ve birbirini onaylar (Confirmation Bias). Dışarıdan gelen zıt bilgiler ya hiç giremez (Giriş engeli) ya da grup tarafından hemen reddedilir (Backfire Effect).
Fizikçilerin simülasyonları (örneğin Ising Modeli veya DeGroot Modeli), belirli şartlar altında toplumun iki zıt kutba (Polarizasyon) ayrılmasının kaçınılmaz olduğunu matematiksel olarak gösterir. Algoritmaların (Facebook/Twitter feedleri) bu süreci hızlandırdığı ("Bunu beğenen, şunu da beğendi") kanıtlanmıştır.

### 3.5. Filtre Baloncukları (Filter Bubbles)
Eli Pariser'in kavramıdır. Google veya Facebook algoritmaları, sizin geçmiş tıklamalarınıza bakarak "neyi seveceğinizi" tahmin eder ve size sadece seveceğiniz şeyleri gösterir. Sonuçta, dünyayı objektif değil, sadece sizin önyargılarınızla filtrelenmiş ("baloncuk" içine alınmış) bir versiyonunu görürsünüz. Bu, ortak toplumsal zemini yok eder.

## 🔑 4. Anahtar Kavramlar Sözlüğü
*   **$R_0$ (Basic Reproduction Number):** Bir hastanın ortalama kaç kişiye hastalık bulaştırdığı.
*   **Complex Contagion (Karmaşık Bulaşma):** Yayılım için birden fazla kaynaktan doğrulama/baskı gerektiren süreç.
*   **Threshold (Eşik):** Bireyin bir davranışı benimsemesi için gereken sosyal kanıt oranı.
*   **Information Cascade (Bilgi Şelalesi):** Bireylerin kendi özel bilgilerini göz ardı edip, kendilerinden öncekilerin kararlarını taklit etmesi (Sürü psikolojisi). İki restoran yan yana, biri boş biri doluysa, dolu olana gitmek.
*   **Echo Chamber (Yankı Odası):** Sadece kendi görüşlerinin tekrarlandığı kapalı ağ yapısı.
*   **Filter Bubble:** Algoritmaların, kullanıcının hoşuna gitmeyecek içerikleri filtreleyerek oluşturduğu entelektüel izolasyon.

## 🛠 5. Kaynaklar ve İleri Okuma Önerileri
### Makale
*   **Granovetter, M. (1978).** "Threshold models of collective behavior". *American Journal of Sociology*. (Klasikleşmiş bir makale).
*   **Centola, D., & Macy, M. (2007).** "Complex contagions and the weakness of long ties". *American Journal of Sociology*. (Zayıf bağlar teorisine getirilen modern eleştiri).

### Kitaplar
*   **"The Tipping Point"** - Malcolm Gladwell: Sosyal salgınların nasıl başladığını anlatan popüler kültür klasiği.
*   **"Change: How to Make Big Things Happen"** - Damon Centola: Karmaşık bulaşma teorisini pratik değişime uyarlayan kitap.

### Simülasyon
*   **"The Parable of the Polygons"** (Vi Hart & Nicky Case): Ayrışma ve homofilinin nasıl istem dışı oluştuğunu gösteren harika bir interaktif oyun/simülasyon. (Mutlaka oynanmalı - https://ncase.me/polygons/).

## 🎯 6. Haftanın Özeti ve Gelecek Haftaya Bakış
Bu hafta, ağların statik çizgilerden ibaret olmadığını, üzerlerinde canlı, nefes alan dinamik süreçlerin aktığını gördük. Fikirlerin, virüslerin ve davranışların yayılım kurallarını öğrendik. Yankı odalarının neden oluştuğunu ve bunları kırmanın neden zor olduğunu anladık.
Şimdiye kadar analizlerimizi hep mental modeller veya matematiksel formüller üzerinden yaptık. Ancak "Bir resim bin kelimeye bedeldir". Gelecek hafta, bu karmaşık ağ verilerini nasıl insan gözünün anlayabileceği grafiklere dönüştüreceğimizi, yani **Ağ Görselleştirme (Network Visualization)** sanatını ve bilimini işleyeceğiz.
