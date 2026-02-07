# Hafta 3: Merkezilik ve Prestij Ölçüleri: Ağın Liderlerini Bulmak

## 📌 1. Ders Hakkında ve Giriş
Bir sosyal ağ haritasına baktığınızda, bazı düğümlerin diğerlerinden daha "merkezi" bir konumda olduğunu sezgisel olarak fark edersiniz. Kimi düğümler tam ortadadır, kimi düğümler çok fazla bağlantıya sahiptir, kimileri ise farklı grupları birbirine bağlayan kilit noktalardadır. Sosyal Ağ Analizi'nin en popüler ve en çok kullanılan araçları, bu sezgisel "önem" kavramını, sayısal ve karşılaştırılabilir metriklere dönüştüren **Merkezilik (Centrality)** ölçüleridir.

"Önemli olmak" ne demektir? Bu sorunun tek bir cevabı yoktur. Bağlam, önemin tanımını değiştirir.
*   Bir partideki en popüler kişi (en çok arkadaşı olan) önemlidir.
*   Bir dedikoduyu en hızlı yayan kişi (herkese mesafesi kısa olan) önemlidir.
*   İki düşman aile arasında barışı sağlayabilecek tek kişi (arabulucu/köprü) önemlidir.
*   Başbakanın danışmanı, kendi başına çok tanınmasa bile, çok güçlü birine bağlı olduğu için önemlidir.

Bu hafta, bu farklı "önem" tanımlarını matematiksel olarak formüle eden dört temel merkezilik ölçüsünü (Derece, Yakınlık, Arasındalık, Özvektör) inceleyeceğiz. Ayrıca Larry Page ve Sergey Brin'in bu kavramları kullanarak nasıl Google'ı kurduğunu (PageRank algoritması) ve web'i bir "prestij ağı" olarak nasıl modellediklerini göreceğiz. Sadece formülleri değil, bu formüllerin arkasındaki sosyolojik anlamı (Güç, Otorite, Bağımsızlık) kavrayacağız.

## 📚 2. Konu Başlıkları ve Haftalık Akış

![merkezilik](/gorseller/sosyalag-merkezilik.png/)

1.  **Merkezilik Kavramının Felsefesi**
    *   Yapısal önem vs. Özelliksel önem.
    *   Linton Freeman'ın 1978 makalesi ve üç temel kavram.
    *   Yıldız (Star) ve Çember (Circle) topolojilerinde merkezilik.
2.  **Temel Merkezilik Ölçüleri (Centrality Measures)**
    *   **Derece Merkezliği (Degree Centrality):** Yerel popülerlik ve iletişim potansiyeli.
    *   **Yakınlık Merkezliği (Closeness Centrality):** Erişim hızı ve verimlilik.
    *   **Arasındalık Merkezliği (Betweenness Centrality):** Kontrol gücü, köprüler ve aracılık.
    *   **Özvektör Merkezliği (Eigenvector Centrality):** "Kimi tanıdığın önemlidir".
3.  **Modern ve İleri Algoritmalar**
    *   **Katz Merkezliği:** Uzak komşuların etkisi ve zayıflama faktörü.
    *   **PageRank:** Yönlü ağlarda prestij ve Google'ın sırrı.
    *   **HITS Algoritması (Hubs & Authorities):** Otoriteler ve Dağıtıcılar.
4.  **Prestij (Prestige)**
    *   Yönlü ağlarda statü.
    *   Seçilme vs. Seçme.

## 📝 3. Detaylı İçerik

### 3.1. Derece Merkezliği (Degree Centrality)
En basit ve en temel ölçüdür. Bir düğümün doğrudan bağlı olduğu komşu sayısını ifade eder. Sadece "yerel" çevreyi dikkate alır.
*   **Tanım:** $C_D(i) = k_i = \sum_{j} A_{ij}$
*   **Normalizasyon:** Ağlar arası karşılaştırma yapabilmek için, bu değer teorik olarak mümkün olan maksimum bağlantı sayısına ($N-1$) bölünür. Aksi halde 10 kişilik ağdaki 5 bağlantı ile 1000 kişilik ağdaki 5 bağlantı aynı sanılabilir.
    $$C'_D(i) = \frac{k_i}{N-1}$$
*   **Anlamı:** "Yerel" bir popülerlik ölçüsüdür. Sadece doğrudan temasları sayar. İletişim yeteneğini ve maruz kalma (exposure) riskini gösterir.
*   **Örnek:** Bir sınıfta en çok arkadaşı olan öğrenci. Bir Twitter ağında en çok takipçisi olan hesap. Bir salgında hastalığı kapma riski en yüksek olan kişi.
*   **Sınırlılığı:** Derecesi yüksek olan biri, ağın çeperinde (kenarında) kendi içine kapalı bir grubun lideri olabilir, ancak ana bilgi akışından kopuk olabilir.

### 3.2. Yakınlık Merkezliği (Closeness Centrality)
Bir düğümün ağdaki **diğer tüm düğümlere** ne kadar yakın olduğunu ölçer. Bilginin yayılma hızıyla ilgilidir.
*   **Tanım:** Bir düğümün diğer tüm düğümlere olan en kısa yol uzunluklarının ($d_{ij}$) toplamının tersidir.
    $$C_C(i) = \frac{1}{\sum_{j \neq i} d_{ij}}$$
*   **Normalizasyon:** Genellikle $(N-1)$ ile çarpılarak normalize edilir.
    $$C'_C(i) = \frac{N-1}{\sum_{j \neq i} d_{ij}}$$
*   **Anlamı:** Yakınlık merkezliği yüksek olan kişi, bir mesajı ağdaki herkese **en az adımda** (en kısa sürede) ulaştırabilir. Veya ağda dolaşan bir dedikoduyu en erken duyan kişidir. Bu kişiler "Bağımsızdır", başkalarına ulaşmak için aracılara ihtiyaç duymazlar.
*   **Örnek:** Şirketin dedikodu kazanı. Lojistik merkezleri (Amazon depoları, herkese eşit mesafede olacak şekilde yerleştirilir).

### 3.3. Arasındalık Merkezliği (Betweenness Centrality)
Belki de en stratejik ölçüdür. Bir düğümün, ağdaki diğer düğüm çiftleri arasındaki **en kısa yolların** ne kadarı üzerinde yer aldığını ölçer.
*   **Tanım:** $i$ düğümünden geçen $s$ ve $t$ arasındaki en kısa yolların sayısı ($\sigma_{st}(i)$), $s$ ve $t$ arasındaki toplam en kısa yol sayısına ($\sigma_{st}$) bölünür.
    $$C_B(i) = \sum_{s \neq i \neq t} \frac{\sigma_{st}(i)}{\sigma_{st}}$$
*   **Anlamı:** Bu kişiler **"Köprü" (Bridge)** veya **"Kapı Bekçisi" (Gatekeeper)** rolü oynarlar. Bilgi akışını kontrol ederler, durdurabilirler, sansürleyebilirler veya değiştirebilirler. İki farklı grup arasındaki tek bağlantı noktası olabilirler.
*   **Örnek:** İki rakip departmanı birbirine bağlayan tek sekreter. Soğuk savaş döneminde hem ABD hem SSCB ile konuşabilen tarafsız ülke diplomatı. Bu kişinin derecesi (arkadaş sayısı) düşük olabilir (sadece 2 kişi), ama bu iki kişi devasa kitleleri temsil ediyorsa, arasındalık değeri çok yüksektir.
*   **Yapısal Boşluklar (Structural Holes):** Ronald Burt'un teorisine göre, bu boşlukları dolduran (bridging) kişiler "sosyal sermaye" ve yenilikçi fikirler açısından avantajlıdır.

### 3.4. Özvektör Merkezliği (Eigenvector Centrality)
"Önemli olan ne kadar arkadaşın olduğu değil, arkadaşların ne kadar önemli olduğudur." prensibine dayanır. Bir düğüme puan verirken, komşularının puanlarını da hesaba katar. Kendi puanınız, komşularınızın puanlarının toplamıyla orantılıdır.
*   **Tanım:** Matematiksel olarak, komşuluk matrisinin en büyük özdeğerine ($\lambda$) karşılık gelen özvektörüdür.
    $$\lambda x_i = \sum_{j} A_{ij} x_j$$
*   **Anlamı:** Eğer size bağlı olan kişiler de çok kişiye bağlıysa (yüksek skorluysa), sizin skorunuz artar. Önemsiz 100 kişiyle tanışmaktansa, çok önemli 1 kişiyle tanışmak daha değerlidir.
*   **Örnek:** Google'ın PageRank algoritmasının atasıdır. Sosyetede kimin nüfuzlu olduğunu anlamak için kullanılır. Mafya babasının sağ kolu.

### 3.5. PageRank Algoritması: Google'ın Sırrı
1998'de Google kurulduğunda, arama motorları web sayfalarını sadece içerdikleri kelimelere göre sıralıyordu. Page ve Brin, web'i bir atıf ağı olarak gördü. Bir sayfa, başka bir sayfaya link veriyorsa, bu ona "oy" vermektir.
Ancak her oy eşit değildir. New York Times'ın verdiği link, kişisel bir blogun verdiği linkten daha değerlidir.
*   **PageRank Modeli:** Özvektör merkezliğine çok benzer, ancak iki önemli fark vardır:
    1.  **Giden Bağlantıya Bölme:** Link veren sayfanın gücü, verdiği link sayısına bölünür. NY Times 100 yere link verdiyse, oylarının gücü 100'e bölünür.
    2.  **Rastgele Sörfçü (Random Surfer) ve Sönümleme (Damping):** Bir kullanıcı sonsuza kadar linklere tıklamaz. Bir noktada sıkılır ve rastgele başka bir sayfaya gider. Bu ihtimali modellemek için **Sönümleme Faktörü ($d \approx 0.85$)** eklenir.
    $$PR(A) = (1-d) + d \sum_{j \in In(A)} \frac{PR(j)}{k_j^{out}}$$
*   Bu algoritma, spam sitelerin (birbirine link veren sayfalar ağı) sistemi kandırmasını engellemiş ve Google'ı trilyon dolarlık bir şirket yapmıştır.

### 3.6. Karşılaştırmalı Senaryo: Floransa Aileleri (Medici Ailesi)
Tarihsel bir SAA klasiği olan **Padgett & Ansell (1993)** çalışması, 15. yüzyıl Floransa'sındaki güçlü ailelerin evlilik ve iş ortaklığı ağlarını inceler.
*   **Medici Ailesi:** Derece merkezliği açısından en yüksektir (en çok evlilik bağı).
*   Ancak asıl güçleri **Arasındalık** merkezliğinden gelir. Diğer güçlü aileler (Strozzi, Albizzi vb.) birbirleriyle düşmandır veya bağları yoktur. Hepsi Medici ailesi üzerinden dolaylı olarak bağlanır. Medici'ler ağın "yıldız" noktasında durarak tüm bilgi ve güç akışını kontrol etmiş, rakiplerini birbirine düşürmüş veya ittifaklar kurmuş, bu sayede Rönesans'ın en güçlü hanedanı olmuşlardır. Bu örnek, merkezilik ölçülerinin politik gücü açıklamada ne kadar başarılı olduğunu kanıtlar.

## 🔑 4. Anahtar Kavramlar Sözlüğü
*   **Centrality (Merkezilik):** Bir düğümün ağ içindeki yapısal önemi.
*   **Geodesic Distance (Geodezik Mesafe):** İki düğüm arasındaki en kısa yolun uzunluğu.
*   **Gatekeeper (Kapı Bekçisi):** Arasındalık merkezliği yüksek olan, bilgi akışını kontrol eden aktör.
*   **Prestige (Prestij):** Yönlü ağlarda (özellikle gelen bağlantılarda) statü göstergesi.
*   **Damping Factor:** PageRank'te sonsuz döngüleri engellemek ve sörfçünün sıkılıp rastgele başka bir sayfaya gitme ihtimalini modellemek için kullanılan katsayı.

## 🛠 5. Kaynaklar ve İleri Okuma Önerileri
### Makaleler
1.  **"Centrality in Social Networks: Conceptual Clarification"** - Linton C. Freeman (1979): Merkezilik ölçülerinin "kutsal kitabı" sayılan makaledir. Üç temel ölçüyü (Degree, Closeness, Betweenness) tanımlar.
2.  **"Robust Action and the Rise of the Medici"** - Padgett & Ansell (1993): Medici ailesi örneğini detaylandıran sosyolojik başyapıt.
3.  **"The Anatomy of a Large-Scale Hypertextual Web Search Engine"** - Brin & Page (1998): Google'ın orijinal makalesi.

### Araçlar ve Uygulama
*   Bu hafta **Gephi** veya **UciNet** kullanarak küçük bir ağ üzerinde (örneğin kendi arkadaş ağınız veya "Les Miserables" karakter ağı) bu 4 metriği hesaplayıp görselleştirmeniz önerilir.
*   Düğümlerin boyutunu (size) farklı merkezilik değerlerine göre ayarlayarak, hangi düğümlerin hangi metrikte öne çıktığını gözlemleyin. Genellikle "köprü" olan düğümlerin boyutu, Arasındalık seçildiğinde devasa büyürken, Derece seçildiğinde küçülebilir.

## 🎯 6. Haftanın Özeti ve Gelecek Haftaya Bakış
Bu hafta, bir ağdaki "güçlü" ve "önemli" aktörleri tespit etmenin tek bir yolu olmadığını öğrendik. Yerel popülerlik için *Derece*, iletişim hızı için *Yakınlık*, kontrol ve strateji için *Arasındalık*, itibar ve nüfuz için *Özvektör/PageRank* kullanmamız gerektiğini gördük.
Ancak şimdiye kadar incelediğimiz ağların "nereden geldiğini" sormadık. Bu ağlar nasıl oluştu? Rastgele mi? Yoksa bir kurala göre mi? Gelecek hafta, ağ biliminin teorik temellerine inerek **Ağ Modelleri**ni incelemeye başlayacağız. En basit model olan **Erdős-Rényi Rastsal Ağları** ile başlayıp, gerçek dünyanın neden hiç de rastgele olmadığını keşfedeceğiz.
