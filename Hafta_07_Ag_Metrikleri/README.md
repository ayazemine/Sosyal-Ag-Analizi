# Hafta 7: Ağ Değerlendirme Metrikleri ve Makro Analiz

## 📌 1. Ders Hakkında ve Giriş
Şimdiye kadar tek tek düğümlere (Merkezilik ölçüleri) veya teorik modellere (Rastsal, Ölçeksiz ağlar) odaklandık. Bu hafta ise elimize gerçek bir ağ verisi aldığımızda (örneğin bir şirketin e-posta trafiği veya bir sınıfın arkadaşlık ağı), bu ağın "Genel Sağlık Raporunu" nasıl çıkaracağımızı öğreneceğiz. Buna **Makro Analiz** diyoruz.

Bir doktorun hastayı muayene ederken önce tansiyon, nabız ve ateșine bakması gibi, bir ağ analisti de ağın **Yoğunluğuna (Density)**, **Çapına (Diameter)** ve **Karışımına (Assortativity)** bakar. Bu metrikler, ağın topolojisini özetler ve farklı ağları birbiriyle karşılaştırmamıza olanak tanır.
*   Bu ağ sıkı fıkı mı yoksa kopuk mu?
*   İnsanlar kendilerine benzeyenlerle mi (Homofili) yoksa benzemeyenlerle mi bağ kuruyor?
*   Ağ tek bir parça mı yoksa adacıklara mı bölünmüş?
*   Ağdaki bilgi ne kadar hızlı dolaşabilir?

Bu hafta ayrıca Ronald Burt'un sosyolojiye kattığı en önemli kavramlardan biri olan **Yapısal Boşluklar (Structural Holes)** teorisini inceleyecek ve ağdaki "boşlukların" aslında nasıl birer "fırsat" olduğunu göreceğiz.

## 📚 2. Konu Başlıkları ve Haftalık Akış
1.  **Ağın Sıklığı ve Mesafesi**
    *   **Yoğunluk (Density):** Gerçekleşen bağların potansiyele oranı.
    *   **Çap (Diameter) ve Yarıçap (Radius):** Ağın fiziksel boyutu.
    *   **Ortalama Yol Uzunluğu:** İletişim verimliliği.
2.  **Karışım Modelleri (Assortativity & Mixing Patterns)**
    *   **Homofili:** "Tencere yuvarlanıp kapağını bulur".
    *   **Assortative Mixing:** Derece korelasyonu (Popülerler popülerlerle).
    *   **Disassortative Mixing:** Yıldız yapılar (Hublar kenardakilerle).
3.  **Bileşen Analizi (Component Analysis)**
    *   Bağlılık (Connectivity).
    *   Güçlü (Strongly) ve Zayıf (Weakly) Bağlı Bileşenler.
    *   **Bow-Tie (Papyon) Yapısı:** Web'in makro yapısı.
4.  **Yapısal Boşluklar (Structural Holes)**
    *   Redundancy (Gereksiz tekrar) vs. Verimlilik.
    *   Social Capital (Sosyal Sermaye).
    *   Broker (Aracı) avantajı.

## 📝 3. Detaylı İçerik

### 3.1. Ağ Ne Kadar "Dolu"? (Yoğunluk)
Bir ağın yoğunluğu ($D$), mevcut kenar sayısının ($L$), o ağda olabilecek maksimum kenar sayısına ($L_{max}$) oranıdır.
*   **Yönsüz Ağ:** $L_{max} = N(N-1)/2$
*   **Yönlü Ağ:** $L_{max} = N(N-1)$
    $$ D = \frac{L}{L_{max}} $$
Yoğunluk 0 ile 1 arasında değişir.
*   **Tam Graf (Clique):** Herkes herkesi tanır ($D=1$). Küçük gruplarda (aile, küçük timler) görülür.
*   **Seyrek Ağ (Sparse):** $D$ değeri 0'a yakındır. Büyük sosyal ağların (Facebook) yoğunluğu son derece düşüktür ($10^{-5}$ civarı). Çünkü $N$ arttıkça, olası bağlantı sayısı karesel artar ($N^2$), ama insanların arkadaş sayısı doğrusal artar. Bu matematiksel bir zorunluluktur; beynimiz (Dunbar Sayısı) herkesi tanımaya yetmez.
*   **Yorum:** Yüksek yoğunluk, sosyal desteğin ve güvenin yüksek olduğunu, normların katı olduğunu gösterir (kapalı köy toplumu). Bilgi çok hızlı yayılır ama yenilik zordur. Düşük yoğunluk, çeşitliliğe ve yeniliğe açıklığı işaret edebilir ama koordinasyon zordur.

### 3.2. Ağ Otoyolları (Mesafe ve Çap)
Ağ üzerinde bilgi ne kadar hızlı akar?
*   **Geodezik Mesafe ($d_{ij}$):** İki düğüm arasındaki en kısa yolun (adım sayısı) uzunluğu.
*   **Çap (Diameter):** Ağdaki "en uzun" en kısa yol. En kötü senaryoda bir mesajın bir uçtan diğerine gitmesi kaç adım sürer? Ağın boyutunu gösterir.
*   **Ortalama Yol Uzunluğu:** Tüm çiftler arasındaki mesafelerin ortalamasıdır. Ağın verimliliğini gösterir.

Örneğin internet, milyarlarca düğümden oluşmasına rağmen çapı çok küçüktür. Veya insan beyni. Bu "Small World" etkisidir.

### 3.3. Kim Kiminle Bağlanır? (Assortativity)
Ağdaki bağlar rastgele atılmamıştır. İnsanlar belirli özelliklere göre eşleşir.
**Newman'ın Assortativity Katsayısı ($r$):** -1 ile +1 arasındadır (Pearson korelasyonu).

1.  **Assortative Ağ ($r > 0$):** Yüksek dereceli düğümler, diğer yüksek dereceli düğümlere bağlanır.
    *   *Örnek:* Sosyal ağlar. Popüler insanlar diğer popülerleri tanır. Ünlüler birbirini takip eder. Zenginler zenginlerle evlenir.
    *   *Sonuç:* Ağda dayanıklı bir "çekirdek" (core) oluşur. Hub'ları yok etmek zordur çünkü birbirlerini yedeklerler. Bilgi çekirdekte hapsolabilir.
2.  **Disassortative Ağ ($r < 0$):** Yüksek dereceli düğümler, düşük dereceli düğümlere bağlanır.
    *   *Örnek:* Teknolojik ve Biyolojik ağlar. İnternet (Büyük sunucular binlerce küçük PC'ye bağlanır), Protein ağları (Düzenleyici proteinler binlerce küçük proteine bağlanır).
    *   *Sonuç:* Yıldız benzeri yapılar oluşur. Hub'lar birbirine bağlı değildir, bu yüzden hedefli saldırılara karşı çok kırılgandır.

**Homofili (Niteliksel Karışım):**
Sadece derece değil, cinsiyet, ırk, yaş, politik görüş gibi özellikler de bağları belirler.
*   "Birds of a feather, flock together." (Tencere yuvarlanıp kapağını bulur).
*   Siyasi kutuplaşma (Echo Chambers) analizlerinde homofili oranına bakılır. Eğer oran çok yüksekse, gruplar arası diyalog kopmuş demektir.

### 3.4. Ağın İskeleti: Bileşen Analizi ve Web'in Papyonu
Yönlü ağlarda (Web gibi), herkes her yere gidemeyebilir.
*   **Zayıf Bağlı Bileşen (WCC):** Okların yönünü görmezden gelirseniz ağ tek parça mıdır? Genellikle evet.
*   **Güçlü Bağlı Bileşen (SCC):** Okları takip ederek, kümedeki her düğümden diğer her düğüme **gidip geri dönebilmek** mümkün müdür?

**Web'in Papyon Yapısı (Bow-Tie Structure):**
Araştırmacılar (Broder et al., 2000) WWW'yi analiz ettiklerinde devasa bir papyon şeması buldular:
1.  **SCC (Çekirdek - %28):** Web'in kalbi. Siteler birbirine yoğun link verir (Wikipedia, Google, CNN). Buradan her yere gidilir.
2.  **IN (Giriş - %21):** Sadece SCC'ye link veren ama geri link alamayanlar (Yeni siteler, küçük bloglar).
3.  **OUT (Çıkış - %21):** SCC'den link alan ama geri vermeyenler (Kurumsal siteler, PDF dosyaları). İçeri girebilirsiniz ama linkle çıkamazsınız.
4.  **Tendrils/Tubes:** Ana akışa hiç girmeyen izole adacıklar.

### 3.5. Yapısal Boşluklar (Structural Holes)
Sosyolog Ronald Burt'un teorisine göre, herkesin birbirini tanıdığı sıkı bir grupta (Clique) bilgi sürekli tekrar eder (Redundant). Çünkü A'nın bildiğini B de bilir, C de bilir. Bu grupta yeni fikir çıkmaz.
Ancak, birbirini hiç tanımayan iki farklı grup (örneğin Yazılım ekibi ile Pazarlama ekibi) arasında duran ve onları birbirine bağlayan kişi, bir **Yapısal Boşluğu** doldurur.
*   Bu kişi bir **Broker (Aracı)**dır.
*   **Avantajları:**
    1.  **Erken Erişim:** İki tarafın bilgisini de ilk o duyar.
    2.  **Sentez:** Yazılımdaki teknik bir çözümle pazarlamadaki bir ihtiyacı birleştirip inovasyon yapabilir.
    3.  **Kontrol:** İki tarafın birbirine ne söyleyeceğine o karar verir.
*   Burt şunu kanıtlamıştır: Şirketlerde terfi alma ve yüksek maaş alma olasılığı en yüksek kişiler, en çok arkadaşı olanlar (Degree) değil, ağdaki boşlukları dolduranlardır (Betweenness). "Sosyal Sermaye" (Social Capital) budur.

## 🔑 4. Anahtar Kavramlar Sözlüğü
*   **Assortativity:** Düğümlerin benzerleriyle bağlanma eğilimi (Genelde pozitif korelasyon).
*   **Diameter (Çap):** Ağın bir ucundan diğer ucuna en uzun mesafe.
*   **Homophily:** Benzerlik temelli çekim.
*   **Structural Hole:** Bağlantısız iki grup arasındaki boşluk. Bu boşluğu doldurmak güç kazandırır.
*   **Social Capital:** İlişkiler ağına gömülü olan ve bireye avantaj sağlayan kaynak.
*   **SCC (Strongly Connected Component):** Yönlü ağda karşılıklı erişimin mümkün olduğu en büyük alt küme.

## 🛠 5. Kaynaklar ve İleri Okuma Önerileri
### Makaleler
*   **Burt, R. S. (2004).** "Structural Holes and Good Ideas". *American Journal of Sociology*. (Fikri mülkiyetin ve iyi fikirlerin "boşlukları dolduran" kişilerden çıktığını data ile ispatlayan efsane makale).
*   **Newman, M. E. J. (2002).** "Assortative mixing in networks".

### Uygulama (NetworkX)
Bir ağın assortativity değerini hesaplayın:
```python
import networkx as nx
# G grafiği yüklenmiş olsun
r = nx.degree_assortativity_coefficient(G)
print(f"Assortativity: {r}")
```
Eğer pozitif çıkarsa sosyal bir ağ, negatif çıkarsa teknolojik bir ağ olma ihtimali yüksektir.

## 🎯 6. Haftanın Özeti ve Gelecek Haftaya Bakış
Bu hafta, ağların genel karakterini (kimyası) analiz ettik. Ağın yoğunluğu, çapı ve assortativity değeri bize o topluluğun sosyal yapısı hakkında (kutuplaşmış mı, hiyerarşik mi, dayanışmacı mı) derin ipuçları verdi. Yapısal boşluklar teorisi ile "bağlantı kurmanın" stratejik önemini anladık.
Ancak ağlar homojen değildir. İçinde yoğunlaşmış **Topluluklar (Communities)** barındırır. Birbiriyle sık görüşen alt gruplar, klikler, çeteler... Gelecek hafta, bir ağın içindeki bu gizli grupları algoritmaların yardımıyla nasıl dedektif gibi bulup çıkaracağımızı (**Topluluk Tespiti / Community Detection**) öğreneceğiz.
