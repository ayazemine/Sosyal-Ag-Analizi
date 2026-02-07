# Hafta 1: Sosyal Medya ve Bilgi Ağlarına Giriş

![SosyalAgAnalizi](https://mustafapala.blog/wp-content/uploads/2021/05/sosyal-ag-koyu.jpg)

## 📌 1. Ders Hakkında ve Giriş
Sosyal Ağ Analizi (SAA), modern dünyanın karmaşık yapısını anlamak için geliştirilmiş en güçlü disiplinlerarası araçlardan biridir. Bu ilk dersimiz, bir döneme yayılacak olan yolculuğumuzun temelini oluşturmaktadır. Sadece bir metadoloji öğrenmeyecek, aynı zamanda dünyaya bakış açımızı değiştirecek yeni bir "mercek" kazanacağız. Geleneksel sosyal bilimler genellikle bireylerin özelliklerine (yaş, cinsiyet, gelir durumu vb.) odaklanırken, Sosyal Ağ Analizi, bireyler arasındaki **ilişkilere** ve bu ilişkilerin oluşturduğu **yapılara** odaklanır. "Kimin ne bildiği değil, kimin kimi tanıdığı önemlidir" sözü, bu dersin en basit özetidir, ancak buzdağının sadece görünen kısmıdır. Bu hafta, ağ biliminin tarihsel köklerine inecek, temel tanımlarını yapacak ve neden 21. yüzyılın "Ağlar Yüzyılı" olarak adlandırıldığını derinlemesine irdeleyeceğiz.

Ağ bilimi, sadece matematikçilerin veya bilgisayar mühendislerinin oyun alanı değildir. Sosyologlar toplumun çöküşünü, biyologlar proteinlerin etkileşimini, ekonomistler finansal krizlerin yayılımını anlamak için bu bilimi kullanır. Bu derste, disiplinlerarası bir yaklaşım benimseyeceğiz.

## 📚 2. Konu Başlıkları ve Haftalık Akış
Bu hafta boyunca aşağıdaki ana başlıklar altında konuları detaylandıracağız:
1.  **Sosyal Ağ Analizi (SAA) Nedir?**
    *   Temel tanımlar ve kavramsal çerçeve.
    *   Sosyal ağlar ile diğer ağ türleri (biyolojik, teknolojik) arasındaki farklar ve benzerlikler.
    *   "Sosyal Medya Ağı" ve "Bilgi Ağı" kavramlarının ayrımı.
2.  **Ağ Bilimi Neden Önemlidir?**
    *   Karmaşıklık (Complexity) teorisi ile ilişkisi.
    *   Birbirine bağlılığın (Connectedeness) getirdiği riskler ve fırsatlar.
    *   Büyük Veri (Big Data) çağında ağ analizinin rolü.
3.  **Tarihsel Gelişim ve Köşe Taşları**
    *   1736: Leonhard Euler ve Königsberg Köprüleri Problemi.
    *   1930'lar: Jacob Moreno ve Sosyometri'nin doğuşu.
    *   1950'ler: Rastsal Ağlar (Erdős ve Rényi).
    *   1960'lar: Stanley Milgram ve "Küçük Dünya" deneyi.
    *   1990'lar ve sonrası: Mark Granovetter, Duncan Watts, Steven Strogatz ve Albert-László Barabási ile modern ağ bilimi.
4.  **Uygulama Alanları: Ağlar Her Yerde**
    *   **Epidemiyoloji:** Hastalıkların yayılımı ve temas ağları.
    *   **Pazarlama:** Ağızdan ağıza pazarlama (Word-of-Mouth) ve viral etki.
    *   **Organizasyon Teorisi:** Resmi olmayan (informal) iletişim ağları ve kurumsal verimlilik.
    *   **Güvenlik:** Suç örgütlerinin ve terör ağlarının tespiti.

## 📝 3. Detaylı İçerik

### 3.1. Sosyal Ağ Analizinin Doğası ve Felsefesi
Sosyal Ağ Analizi, sosyal yapıları "ağlar" ve "grafikler" teorisi üzerinden inceleyen bir yaklaşımdır. Buradaki temel varsayım, sosyal olguların bireylerin tekil özelliklerinden ziyade, bireylerin birbirleriyle kurdukları ilişkilerin yapısı tarafından şekillendirildiğidir.

Geleneksel bir anket çalışmasında, bir araştırmacı insanlara "Mutlu musunuz?" diye sorabilir ve mutluluğu gelir düzeyiyle ilişkilendirmeye çalışabilir. Ancak bir ağ bilimci, "Arkadaşlarınız mutlu mu?" diye sorar. Çünkü Nicholas Christakis ve James Fowler'ın ünlü araştırmalarının gösterdiği gibi, mutluluk, obezite veya sigara içme alışkanlığı gibi durumlar sosyal ağlar üzerinden "bulaşıcıdır". Eğer yakın arkadaşlarınız mutluysa, sizin de mutlu olma ihtimaliniz %15 artmaktadır. Hatta arkadaşınızın arkadaşı mutluysa bu oran %10, onun da arkadaşı mutluysa %6 artmaktadır (Üç Derece Etki Kuralı). İşte SAA, bu görünmez bağların haritasını çıkarır ve etkilerini ölçer.

Bir sosyal ağ, en temel haliyle **düğümler (nodes/vertices)** ve bu düğümleri birbirine bağlayan **kenarlar (edges/links)** topluluğudur.
*   **Düğümler:** Analiz ettiğimiz aktörlerdir. Bunlar bireyler, şirketler, ülkeler, web siteleri, proteinler veya kelimeler olabilir. Düğümlerin nitelikleri (attribute) olabilir; örneğin bir insanın yaşı, cinsiyeti veya bir şirketin cirosu.
*   **Kenarlar:** Bu aktörler arasındaki ilişkilerdir. Arkadaşlık, para transferi, atıf yapma, fiziksel temas, hyperlinks veya semantik benzerlikler birer kenar olabilir. Kenarların yönü (Ali Ayşe'yi seviyor ama Ayşe Ali'yi sevmiyor) veya ağırlığı (Ali ile Ayşe haftada 5 kez görüşüyor) olabilir.

### 3.2. Ağ Bilimi Neden Şimdi Bu Kadar Önemli?
İnsanlık tarihi boyunca her zaman ağlar içinde yaşadık ve hayatta kaldık (kabileler, ticaret yolları, imparatorluklar). Ancak son 30-40 yılda iki temel değişiklik oldu:
1.  **Ağların Görünürlüğü ve Veri:** İnternet ve dijitalleşme sayesinde, daha önce görünmez olan sosyal bağlar (kiminle konuştuğumuz, kimi takip ettiğimiz, nereye gittiğimiz) "dijital ayak izlerine" dönüştü. Artık milyarlarca düğüm ve trilyonlarca kenardan oluşan ağları analiz edebilecek veriye sahibiz. Eskiden bir sosyologun bir köydeki ilişkileri haritalaması aylar sürerken, bugün bir API sorgusu ile milyonlarca tweet'in etkileşim haritasını çıkarabiliyoruz.
2.  **Hesaplama Gücü:** Bu devasa veriyi işleyebilecek bilgisayar gücüne ve algoritmalara sahibiz. 50 yıl önce bir sosyolog en fazla bir sınıftaki 30 öğrencinin arkadaşlık ilişkilerini eliyle çizerken, bugün Facebook'taki 3 milyar kullanıcının etkileşim ağını analiz edebiliyoruz.

Ayrıca dünya hiç olmadığı kadar "bağlantılı" (interconnected) hale geldi. Çin'in Wuhan kentinde başlayan bir virüsün haftalar içinde tüm dünyayı durdurabilmesi (COVID-19), 2008'de ABD konut piyasasındaki bir krizin İzlanda ekonomisini batırabilmesi veya Süveyş Kanalı'nda karaya oturan bir geminin küresel ticareti kilitlemesi, ağların gücünü ve kırılganlığını göstermektedir. Bu karmaşık sistemleri yönetebilmek için ağ bilimine mecburuz. **Kelebek Etkisi** artık sadece bir metafor değil, ağlar üzerinde gözlemlenebilir bir gerçektir.

### 3.3. Tarihsel Yolculuk: Köprülerden Facebook'a

#### Königsberg Köprüleri (1736)
Ağ teorisinin (Graf teorisi) miladı, matematikçi Leonhard Euler'in Prusya'nın Königsberg kentindeki (bugünkü Kaliningrad) yedi köprü problemini çözmeye çalışmasıyla başlar. Soru şuydu: "Şehirdeki yedi köprünün hepsinden tam olarak bir kez geçerek şehri dolaşmak mümkün mü?"
Euler, haritadaki kara parçalarını "düğüm", köprüleri ise "kenar" olarak temsil ederek problemi soyutladı. Bu, tarihteki ilk graf (graph) çizimiydi. Euler, bunun imkansız olduğunu matematiksel olarak kanıtladı: Bir grafı kalemi kaldırmadan ve aynı çizgiden geçmeden çizebilmek için, tek sayıda bağlantıya sahip düğüm sayısının 0 veya 2 olması gerekir.

#### Moreno ve Sosyometri (1930'lar)
Jacob Moreno, bir kız okulundaki kaçış olaylarını incelerken, öğrencilerin kime yakın hissettiğini sordu ve bunları çizdi. Ortaya çıkan çizimlere **"Sosyogram"** adını verdi. Moreno, bazı öğrencilerin "yıldız" gibi parladığını ve herkesin onlarla arkadaş olmak istediğini, bazı öğrencilerin ise izole kaldığını görselleştirdi. Bu, modern SAA'nın atasıdır. Moreno ayrıca New York Times'ta "Psikolojik Coğrafya" haritaları yayınlayarak ağ analizini popülerleştirdi.

#### Milgram ve Küçük Dünya (1967)
Hafta 5'te detaylıca göreceğimiz bu deneyde, sosyal psikolog Stanley Milgram, dünyanın ne kadar "küçük" olduğunu test etti. İnsanların birbirine tanıdıkları üzerinden ulaşması ortalama 6 adım sürüyordu. Bu deney, ağların "Small World" (Küçük Dünya) özelliğini ortaya koydu. "Altı Derece" (Six Degrees of Separation) kavramı buradan doğdu.

#### Granovetter ve Zayıf Bağların Gücü (1973)
Sosyolog Mark Granovetter, insanların nasıl iş bulduğunu araştırdı. Şaşırtıcı bir sonuçla karşılaştı: İnsanlar yeni işlerini genellikle en yakın arkadaşlarından (güçlü bağlar) değil, az tanıdıkları, yılda bir gördükleri kişilerden (zayıf bağlar) buluyorlardı. Çünkü yakın arkadaşlarınız zaten sizin bildiğiniz şeyleri bilir; aynı çevredesinizdir. Ancak "zayıf bağlarınız" farklı sosyal çevrelere açılan pencerelerdir ve yeni bilgiyi (örneğin iş fırsatını) onlar getirir. Bu makale, tüm sosyal bilimlerin en çok atıf alan makalelerinden biri oldu ve "networking" kavramının bilimsel tabanını oluşturdu.

### 3.4. Sosyal Ağların ve Bilgi Ağlarının Farklılaşması
Her ne kadar matematiksel temelleri aynı olsa da, sosyal ağlar ve bilgi ağları farklı dinamiklere sahiptir.
*   **Sosyal Ağlar:** İnsanlar veya organizasyonlar arasındaki ilişkilerdir. Duygusal, profesyonel veya fiziksel olabilir. Genellikle "kümeleşme" (clustering) yüksektir. "Dostumun dostu dostumdur" kuralı işler. Güven ve normlar bu ağlarda akar.
*   **Bilgi Ağları:** Bilgi birimlerinin birbirine bağlanmasıdır. En büyük örneği World Wide Web (WWW)'dir. Web sayfaları (düğüm) birbirine link (kenar) verir. Bilimsel makalelerin birbirine atıf vermesi (atıf ağları) de bir bilgi ağıdır. Google'ın PageRank algoritması, aslında bir atıf ağı analizidir. Bir patentin başka patente atıf yapması inovasyon tarihini izlememizi sağlar.

### 3.5. Uygulama Alanlarından Örnekler

#### Sağlık ve Epidemiyoloji
Cinsel yolla bulaşan hastalıkların yayılımını engellemek için sadece virüsü tanımak yetmez, cinsel temas ağının (sexual contact network) yapısını bilmek gerekir. Bazı ağlarda, sadece birkaç "süper yayıcı" (super-spreader) kişiyi tedavi etmek tüm salgını durdurabilirken, bazı ağ yapılarında herkese aşı yapmak gerekebilir. SAA, bu "hub" (merkez) kişileri tespit etmeyi sağlar. HIV virüsünün Amerika'ya "Hasta Sıfır" (Patient Zero) olarak bilinen bir havayolu görevlisi üzerinden yayıldığı iddiası (sonradan çürütülse de) bu analizlerin popüler kültürdeki yerini gösterir.

#### Terörle Mücadele ve İstihbarat
11 Eylül saldırılarından sonra analistler, teröristlerin iletişim ağlarını çıkardı. Bu ağlar genellikle "hücresel" yapıdadır; yani küçük gruplar birbirinden bağımsızdır ancak tepedeki bir lidere bağlıdır. Ağın merkezindeki kişiyi (lideri) yakalamak bazen ağı yok etmez, aksine ağı parçalayıp kontrolsüz hale getirebilir. SAA, ağın en kritik "köprü" (broker) elemanlarını bulup iletişimi kesmeyi hedefler. Saddam Hüseyin'in yakalanması sürecinde de, onun en yakın korumalarının aile ve aşiret ağları analiz edilmiştir.

#### Kurumsal İletişim
Bir şirketin resmi organizasyon şeması (kim kimin müdürü) ile gerçek iletişim ağı (kim kahve molasında kiminle konuşuyor) asla aynı değildir. Genellikle işleri yürüten, resmi şemada görünmeyen ama herkesin güvendiği "gizli liderler" vardır. Yöneticiler, bu gayri resmi ağları analiz ederek değişimi yönetebilir, inovasyonu artırabilir veya bilgi tıkanıklıklarını çözebilir. Enron skandalı sonrası ortaya çıkan e-posta ağları, kurumsal çürumanın en net haritasını sunmuştur.

## 🔑 4. Anahtar Kavramlar Sözlüğü
*   **Sosyal Ağ Analizi (SAA):** Sosyal ilişkilerin ağ teorisi kullanılarak incelenmesi.
*   **Düğüm (Node/Vertex):** Ağın temel birimi; aktör, kişi, nesne.
*   **Kenar (Edge/Link):** Düğümler arasındaki bağlantı.
*   **Sosyogram:** Sosyal ilişkilerin görsel haritası.
*   **Yol (Path):** Bir düğümden diğerine gitmek için izlenen kenarlar dizisi.
*   **Küçük Dünya Fenomeni:** Büyük ağlarda herhangi iki düğümün birbirine çok az sayıda adımda bağlı olması durumu.
*   **Zayıf Bağların Gücü (Strength of Weak Ties):** Farklı ve yeni bilgiye ulaşmada zayıf ilişkilerin, güçlü dostluklardan daha etkili olması prensibi.

## 🛠 5. Kaynaklar ve İleri Okuma Önerileri
### Temel Kitaplar
1.  **"Linked: The New Science of Networks"** - Albert-László Barabási: Konuyu hiç bilmeyenler için mükemmel bir popüler bilim giriş kitabıdır. Ağların tarihçesini ve önemini hikayelerle anlatır.
2.  **"Six Degrees: The Science of a Connected Age"** - Duncan Watts: Küçük dünya teorisi ve ağ dinamiği üzerine odaklanır.
3.  **"Networks, Crowds, and Markets"** - David Easley & Jon Kleinberg: Üniversite seviyesinde, hem sosyal hem ekonomik yönleri ele alan, matematiği de içeren temel ders kitabıdır.

### Akademik Makaleler
*   *Borgatti, S. P., Mehra, A., Brass, D. J., & Labianca, G. (2009).* "Network Analysis in the Social Sciences". *Science*, 323(5916), 892-895. (SAA'nın sosyal bilimlerdeki yerini özetleyen temel bir makale).
*   *Travers, J., & Milgram, S. (1969).* "An Experimental Study of the Small World Problem". *Sociometry*.

### Çevrimiçi Kaynaklar
*   **Coursera / edX:** "Social Network Analysis" (University of Michigan veya Stanford dersleri).
*   **NetLogo Models Library:** Ağ oluşum simülasyonlarını tarayıcıda izlemek için interaktif araçlar.

## 🎯 6. Haftanın Özeti ve Gelecek Haftaya Bakış
Bu hafta, sosyal ağ analizinin sadece bir "Facebook analizi" olmadığını, matematikten biyolojiye, sosyolojiden fiziğe uzanan devasa bir bilimsel alan olduğunu gördük. Ağların temel yapıtaşlarını ve tarihsel gelişimini inceledik. Önümüzdeki hafta, bu sözel kavramları matematiksel dile dökmeye başlayacağız. "Düğüm", "Kenar" ve "Matris" kavramlarını kullanarak ağları formüle edecek, Graf Teorisi'nin (Graph Theory) temel kurallarını öğreneceğiz. Bilgisayarların bu sosyal ağları nasıl "anladığını" ve işlediğini keşfetmeye hazır olun.
