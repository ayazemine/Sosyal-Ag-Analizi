# Hafta 2: Ağ Matematiği ve Graf Teorisi

## 📌 1. Ders Hakkında ve Giriş
Geçen hafta sosyal ağ analizinin kavramsal çerçevesini ve tarihçesini inceledik. Bu hafta ise işin "mutfağına", yani matematiğine giriyoruz. Sosyal, biyolojik veya teknolojik herhangi bir ağı analiz edebilmek için ortak bir dile ihtiyacımız vardır. Bu dil, **Graf Teorisi (Graph Theory)**'dir. Bir sosyolog "A, B'nin arkadaşıdır" derken, bir matematikçi veya bilgisayar bilimci bunu "$G=(V, E)$ grafında $A$ ve $B$ düğümleri arasında bir kenar vardır ($e_{AB} \in E$)" şeklinde ifade eder. Bu formalizasyon, milyonlarca düğümden oluşan karmaşık sistemleri bilgisayarlarla analiz etmemizi, ölçmemizi ve karşılaştırmamızı sağlar.

Bu derste matris cebirinin temel kavramlarını hatırlayacak, ağları dijital ortamda nasıl temsil ettiğimizi (Komşuluk Matrisi, Kenar Listesi vb.) öğrenecek ve ağların en temel istatistiksel özelliği olan "Derece" (Degree) kavramını derinlemesine inceleyeceğiz.

## 📚 2. Konu Başlıkları ve Haftalık Akış
1.  **Ağın Temel Yapıtaşları: Graf Teorisine Giriş**
    *   Graf ($G$), Düğüm ($V$), Kenar ($E$) tanımları.
    *   Sonlu ve sonsuz graflar.
    *   Ağ büyüklüğü ($N$) ve bağlantı sayısı ($L$).
2.  **Ağ Sınıflandırmaları ve Türleri**
    *   **Yönlülük:** Yönlü (Directed/Digraph) ve Yönsüz (Undirected) Ağlar.
    *   **Ağırlık:** Ağırlıklı (Weighted) ve Ağırlıksız (Unweighted) Ağlar.
    *   **İşaret:** İşaretli (Signed) Ağlar (Dost/Düşman ilişkisi).
    *   **Bağlantı Türü:** Basit Graf (Simple Graph) vs. Multigraph (Çoklu Kenar).
    *   **Bipartite (İki Parçalı) Ağlar:** Aktörler ve Olaylar.
3.  **Ağların Matematiksel ve Dijital Temsili**
    *   Komşuluk Matrisi (Adjacency Matrix).
    *   Kenar Listesi (Edge List).
    *   Komşuluk Listesi (Adjacency List).
    *   Seyrek (Sparse) ve Yoğun (Dense) Matrisler.
4.  **Temel Ağ Metrikleri: Derece (Degree)**
    *   Düğüm Derecesi ($k_i$).
    *   Ortalama Derece ($\langle k \rangle$).
    *   Gelen Derece (In-degree) ve Giden Derece (Out-degree).
    *   Derece Dağılımı (Degree Distribution, $P(k)$).

## 📝 3. Detaylı İçerik

### 3.1. Ağın Anatomisi: $G = (V, E)$
Graf teorisinde bir ağ (graf), iki temel kümeden oluşur:
1.  **Düğümler Kümesi ($V$ - Vertices):** Ağdaki nesneleri temsil eder. Örneğin $V = \{Ali, Ayşe, Mehmet\}$. Ağın büyüklüğü genellikle düğüm sayısı ile ifade edilir ve $N = |V|$ şeklinde gösterilir.
2.  **Kenarlar Kümesi ($E$ - Edges):** Düğümleri birbirine bağlayan çizgilerdir. Örneğin $E = \{(Ali, Ayşe), (Ayşe, Mehmet)\}$. Kenar sayısı $L = |E|$ şeklinde gösterilir.

Bir ağda "kendine dönen kenar" (self-loop) olabilir (örneğin bir kişinin kendi kendine konuşması veya bir makalenin kendine atıf yapması). Ayrıca iki düğüm arasında birden fazla kenar (multigraph) olabilir (örneğin Ali ve Ayşe hem Facebook arkadaşı hem de iş arkadaşı olabilir). Ancak çoğu temel SAA çalışmasında, self-loop ve çoklu kenarların olmadığı **"Basit Graf" (Simple Graph)** yapısı kullanılır.

### 3.2. Ağ Türleri ve Gerçek Hayattaki Karşılıkları

#### Yönlü ve Yönsüz Ağlar
*   **Yönsüz Ağ (Undirected Graph):** İlişkiler karşılıklıdır. Kenarların ok ucu yoktur. $(i, j)$ çifti ile $(j, i)$ çifti aynı şeyi ifade eder.
    *   *Örnek:* Facebook arkadaşlığı, fiziksel tokalaşma, aynı sokakta oturma. Eğer Ali, Veli'nin arkadaşıysa; Veli de Ali'nin arkadaşıdır. Komşuluk matrisi simetriktir ($A_{ij} = A_{ji}$).
*   **Yönlü Ağ (Directed Graph / Digraph):** İlişkilerin bir yönü vardır. Kenarlar ok ucuyla gösterilir. $(i, j)$ kenarı, $i$'den $j$'ye giden bir bağı temsil eder ve $(j, i)$'den farklıdır.
    *   *Örnek:* Twitter takibi, telefon araması, borç para verme, web sitesi linki. Ali, Madonna'yı takip edebilir ama Madonna Ali'yi takip etmeyebilir. Asimetri, güç ilişkisini gösterir.

#### Ağırlıklı Ağlar (Weighted Networks)
Çoğu zaman ilişkiler sadece "var" veya "yok" demek yetersizdir. İlişkinin şiddeti, sıklığı veya kapasitesi önemlidir.
*   *Örnek:* Hava yolu ağlarında iki şehir arasındaki uçuş sayısı, bilimsel işbirliği ağlarında ortak yazılan makale sayısı, iletişim ağlarında konuşma süresi. Kenarlara $w_{ij}$ değeri atanır. Ağırlık bazen maliyeti (mesafe), bazen kapasiteyi (bant genişliği) ifade eder. En kısa yol algoritmaları ağırlığın anlamına göre değişir.

#### Bipartite (İki Parçalı) Ağlar
Bazı ağlarda iki farklı tür düğüm vardır ve bağlar sadece farklı türler arasında olabilir. $V$ kümesi $U$ ve $W$ olarak ikiye ayrılır.
*   *Örnek:* Aktörler ve Filmler ağı. Aktörler birbirine bağlanmaz, filmler de birbirine bağlanmaz. Aktör filme bağlanır ("oynadı" ilişkisi). Veya Müşteriler ve Ürünler (Amazon).
*   **Projeksiyon:** Bu ağları tek parçalı (one-mode) ağlara dönüştürebiliriz. "Aynı filmde oynayan aktörler ağı" oluşturursak, düğümler sadece aktörler olur ve iki aktör aynı filmde oynadıysa aralarında bağ kurulur.

### 3.3. Matematiksel Temsil: Bilgisayar Ağı Nasıl Görür?

Bir ağı çizmek (görselleştirme) insanlar için iyidir ama bilgisayarlar resimlere bakarak analiz yapmaz. Ağları sayısal veri yapılarına dönüştürmemiz gerekir. En yaygın üç yöntem şunlardır:

#### Komşuluk Matrisi (Adjacency Matrix)
$N$ adet düğümü olan bir ağ için, $N \times N$ boyutunda bir $A$ matrisi oluşturulur.
*   Eğer $i$ ve $j$ düğümleri arasında bağ varsa, $A_{ij} = 1$.
*   Bağ yoksa, $A_{ij} = 0$.
*   Ağırlıklı ağlarda $1$ yerine ağırlık değeri ($w_{ij}$) yazılır.

**Özellikleri:**
*   Yönsüz ağlarda $A_{ij} = A_{ji}$ olduğu için matris köşegene göre simetriktir.
*   Yönlü ağlarda simetrik olmak zorunda değildir.
*   **Dezavantaj:** Sosyal ağlar genellikle çok "seyrek"tir (Sparse). Milyonlarca insan vardır ama herkesin ortalama 100-200 arkadaşı vardır (milyonlarca değil). Bu nedenle matrisin %99.99'u "0" ile doludur. Bu, bilgisayar hafızasında aşırı yer kaplar ($O(N^2)$).

#### Kenar Listesi (Edge List)
Sadece var olan bağlantıların listesidir. Bilgisayar hafızası için çok daha verimlidir.
```text
Ali, Ayşe
Ayşe, Mehmet
Mehmet, Can
```
Büyük veri analizlerinde (Twitter datası vb.) genellikle bu format (.csv veya .txt) kullanılır.

#### Komşuluk Listesi (Adjacency List)
Her düğüm için, o düğüme komşu olanların listesi dinamik dizilerde (linked list) tutulur.
*   Ali: [Ayşe]
*   Ayşe: [Ali, Mehmet]
*   Mehmet: [Ayşe, Can]
Ağ üzerinde "gezinme" (traversal) algoritmaları için en performanslı yapıdır çünkü 0'ları kontrol etmekle zaman kaybetmezsiniz.

### 3.4. Temel İstatistik: Derece (Degree)

Bir düğümün **derecesi ($k$)**, o düğüme bağlı olan kenar sayısıdır. Ağdaki en temel "önem" ölçütüdür.

#### Yönsüz Ağlarda Derece
$i$ düğümünün derecesi $k_i$, komşuluk matrisindeki $i$. satırın (veya sütunun) toplamıdır:
$$k_i = \sum_{j=1}^{N} A_{ij}$$
Ağdaki toplam kenar sayısı $L$ ile toplam derece arasında şu ilişki vardır:
$$2L = \sum_{i=1}^{N} k_i$$
(Her kenar iki uca sahip olduğu için toplam dereceye 2 kez katkıda bulunur. Buna **El Sıkışma Teoremi** denir: Bir partideki toplam el sıkışma sayısı çift sayı olmak zorundadır).

#### Yönlü Ağlarda Derece
İki farklı derece vardır:
1.  **Gelen Derece (In-degree, $k_{i}^{in}$):** Düğüme gelen bağlantı sayısı (Örn: Takipçi sayısı). Matriste sütun toplamıdır.
    $$k_i^{in} = \sum_{j=1}^{N} A_{ji}$$
2.  **Giden Derece (Out-degree, $k_{i}^{out}$):** Düğümden çıkan bağlantı sayısı (Örn: Takip edilen sayısı). Matriste satır toplamıdır.
    $$k_i^{out} = \sum_{j=1}^{N} A_{ij}$$

#### Ortalama Derece ($\langle k \rangle$)
Ağın genel yoğunluğu hakkında bilgi verir. "Ortalama bir insanın kaç arkadaşı vardır?" sorusunun cevabıdır.
Yönsüz ağda:
$$ \langle k \rangle = \frac{1}{N} \sum_{i=1}^{N} k_i = \frac{2L}{N} $$
Yönlü ağda:
$$ \langle k^{in} \rangle = \langle k^{out} \rangle = \frac{L}{N} $$

#### Derece Dağılımı (Degree Distribution) - $P(k)$
Belki de ağ biliminin en kritik kavramıdır. Ağdan rastgele seçilen bir düğümün derecesinin $k$ olma ihtimalidir.
*   **Histogram:** Düğümlerin derecelerini sayarız. Kaç kişi 1 arkadaşa sahip? Kaç kişi 100 arkadaşa sahip?
*   Bir sınıftaki öğrencilerin arkadaş sayısına bakarsak, çoğu kişinin 3-5 arkadaşı vardır, kimsenin 100 arkadaşı yoktur. Bu **Normal Dağılım (Çan Eğrisi)**'dır. Erdős-Rényi rastsal ağlarında bu görülür.
*   Twitter'a bakarsak, çoğu kişinin 10-20 takipçisi varken, bazılarının (müzisyenler, politikacılar) milyonlarca takipçisi vardır. Bu **Kuvvet Yasası (Power Law)** dağılımıdır.
Bu iki dağılım arasındaki fark, ağın "Ölçeksiz" (Scale-free) olup olmadığını belirler ve önümüzdeki haftalarda bunun ne kadar hayati sonuçları olduğunu göreceğiz.

## 🔑 4. Anahtar Kavramlar Sözlüğü
*   **Simple Graph:** Çoklu kenar ve kendisiyle bağlantının (self-loop) olmadığı basit ağ.
*   **Adjacency Matrix:** Düğümler arası bağlantıları 0 ve 1'lerle gösteren kare matris.
*   **Sparse Network:** Olası bağlantıların çok azının gerçekleştiği ağ (Gerçek sosyal ağların çoğu seyrektir).
*   **Degree (Derece):** Düğümün bağlantı sayısı.
*   **Hub:** Derecesi ortalamadan çok çok yüksek olan düğüm.
*   **Bipartite Graph:** İki farklı düğüm kümesine sahip olan ve sadece kümeler arası bağa izin veren ağ.

## 🛠 5. Kaynaklar ve İleri Okuma Önerileri
### Temel Kitaplar
1.  **"Network Science"** - Albert-László Barabási: Bölüm 2 (Graph Theory). Bu bölüm, konunun matematiksel incili gibidir. (http://networksciencebook.com/chapter/2)
2.  **"Social Network Analysis: Methods and Applications"** - Wasserman & Faust: Bu alandaki en kapsamlı referans kitabıdır (Matematiksel notasyonlar için).

### Uygulama (Python & NetworkX)
Bu hafta teorik olsa da, Python biliyorsanız `NetworkX` kütüphanesi ile denemeler yapabilirsiniz:
```python
import networkx as nx
import matplotlib.pyplot as plt

# Basit bir ağ oluştur
G = nx.Graph() 
G.add_edge('Ali', 'Ayşe') # Bağlantı ekle
G.add_edge('Ayşe', 'Mehmet')

# Matrisini çıkar
A = nx.adjacency_matrix(G) 
print(A.todense())

# Dereceleri gör
print(G.degree['Ali']) # 1
print(G.degree['Ayşe']) # 2
```

## 🎯 6. Haftanın Özeti ve Gelecek Haftaya Bakış
Bu hafta, sosyal ilişkileri matematiksel nesnelere ($G, V, E, A_{ij}$) dönüştürmeyi öğrendik. Artık bir ağın resmine bakıp "ne kadar karışık" demek yerine, "bu ağın ortalama derecesi 4.5, yoğunluğu 0.02" gibi kesin ifadeler kullanabiliyoruz. Derece kavramını öğrendik ama "Derecesi yüksek olan en önemlidir" demek her zaman doğru mudur? Bir casusluk ağında en çok kişiyi tanıyan (yüksek derece) kişi mi, yoksa iki hücre arasındaki tek bağlantı olan (düşük derece ama köprü) kişi mi daha önemlidir? Gelecek hafta, bu sorunun yanıtını arayacak ve **Merkezilik (Centrality)** ölçülerini (Arasındalık, Yakınlık, Özvektör) detaylıca inceleyeceğiz. Google'ın nasıl Google olduğunu (PageRank) ve liderlik ile popülerlik arasındaki matematiksel farkı keşfedeceğiz.
