# Hafta 4: Ağ Modelleri ve Rastsal Ağlar (Random Networks)

## 📌 1. Ders Hakkında ve Giriş
Şimdiye kadar var olan ağları analiz ettik: Düğümler kimler, hangisi önemli, ağın yoğunluğu ne? Ancak bilimsel düşüncenin en temel sorusu "Nasıl?" ve "Neden?"dir. Bu sosyal ağlar nasıl oluştu? Neden arkadaşlarınızın sayısı normal dağılım göstermiyor? Neden dünyadaki herhangi birine ulaşmak bu kadar kolay?

Bu soruları cevaplamak için **Ağ Modelleri** (Network Models) oluştururuz. Bir model, karmaşık gerçeğin basitleştirilmiş bir simülasyonudur. Bilim insanları, "Eğer insanlar rastgele tanışsaydı dünya nasıl görünürdü?" sorusunu sormuşlar ve ilk ağ modelini geliştirmişlerdir: **Erdős-Rényi Rastsal Ağ Modeli**.

Bu hafta, 1959 yılında iki Macar matematikçi Paul Erdős ve Alfréd Rényi tarafından ortaya atılan bu teoriyi inceleyeceğiz. Rastsal ağlar, gerçek sosyal ağları (Facebook, Twitter vb.) açıklamakta başarısız olsa da, **referans modeli** (null model) olarak hayati bir öneme sahiptir. Bir ağın "özel" bir yapısı olup olmadığını anlamak için, onu rastsal bir ağla kıyaslarız. Eğer gerçek ağımız rastsal ağdan çok farklıysa, orada incelemeye değer bir sosyal mekanizma var demektir.

## 📚 2. Konu Başlıkları ve Haftalık Akış
1.  **Dört Büyük Ağ Türü ve Özellikleri**
    *   Sosyal Ağlar (Arkadaşlık, İletişim, İşbirliği).
    *   Bilgi Ağları (Atıf ağları, WWW, Patent ağları).
    *   Teknolojik Ağlar (İnternet altyapısı, Elektrik şebekesi, Ulaşım).
    *   Biyolojik Ağlar (Protein etkileşimleri, Metabolik ağlar, Nöron ağları).
2.  **Rastsal Ağlar (Random Networks) Teorisi**
    *   Erdős-Rényi (ER) Modeli tanımları: $G(N, L)$ ve $G(N, p)$.
    *   Rastsal bir grafiğin oluşum süreci.
    *   Binom dağılımından Poisson dağılımına geçiş.
3.  **Rastsal Ağların Özellikleri**
    *   Derece Dağılımı: Çan eğrisi (Bell Curve) ve homojenlik.
    *   Ortalama Yol Uzunluğu: $L \approx \ln N / \ln \langle k \rangle$ (Small World özelliği).
    *   Kümeleme Katsayısı: $C \approx \langle k \rangle / N$ (Sıfıra yakınsama).
4.  **Faz Geçişleri ve Dev Bileşen (Giant Component)**
    *   Bağlantı olasılığı ($p$) arttıkça ağın evrimi.
    *   $\langle k \rangle = 1$ kritik eşiği.
5.  **Gerçek vs. Model**
    *   Gerçek ağlar rastsal mıdır? Karşılaştırmalı analiz.

## 📝 3. Detaylı İçerik

### 3.1. Erdős-Rényi (ER) Modeli Nedir?
Paul Erdős, 20. yüzyılın en üretken matematikçilerinden biridir. Yersiz yurtsuz yaşamış, arkadaşlarının evinde kalarak matematik yapmıştır. Meslektaşı Alfréd Rényi ile birlikte, bir partideki konukların birbirini rastgele tanıdığını varsayarak bir model geliştirdiler. İki farklı matematiksel tanımı vardır:
1.  **$G(N, L)$ Modeli:** $N$ adet düğüm alınır ve bunların arasına rastgele seçilen tam olarak $L$ adet kenar atılır.
2.  **$G(N, p)$ Modeli:** $N$ adet düğüm alınır. Her olası düğüm çifti $(i, j)$ için bir yazı tura atılır. $p$ olasılığı ile aralarına bir kenar konur, $1-p$ olasılığı ile konmaz.

Günümüzde analizlerde daha çok $G(N, p)$ modeli kullanılır çünkü analitik hesabı daha kolaydır. Bu modelde beklenen toplam kenar sayısı:
$$ \langle L \rangle = p \frac{N(N-1)}{2} $$
Ortalama derece ise:
$$ \langle k \rangle = p (N-1) \approx pN $$

### 3.2. Derece Dağılımı: Herkes Eşittir
ER modelinde bir düğümün derecesi, diğer $N-1$ düğümle kurduğu bağlantı denemelerinin sonucudur. Bu klasik bir **Binom Dağılımı** (Binomial Distribution) sürecidir. Ancak $N$ çok büyük, $p$ çok küçük olduğunda bu dağılım matematiksel olarak **Poisson Dağılımı**na yakınsar.

**Bunun Anlamı Nedir?**
Poisson dağılımının (tıpkı Normal dağılım gibi) belirgin bir tepesi (modu) vardır ve bu tepe ortalama derece $\langle k \rangle$ etrafındadır. Kuyrukları ise hızla (üstel olarak) yok olur.
*   **Sonuç 1:** Rastsal bir ağda, düğümlerin çok büyük bir kısmı ortalama dereceye sahiptir.
*   **Sonuç 2:** Ortalamadan çok sapan (aşırı yüksek veya aşırı düşük dereceli) düğüm bulmak imkansıza yakındır.
*   **Sosyal Yorum:** Rastsal bir ağda, herkesin "üç aşağı beş yukarı" aynı sayıda arkadaşı vardır. "Süper star"lar (Hub'lar) veya "Münzevi"ler yoktur. Toplum son derece **Eşitlikçi (Egalitarian)** ve **Homojen (Homogeneous)**dir.
*   Bu durum gerçek hayatla çelişir. Gerçekte bazılarımızın 1000 arkadaşı varken bazılarımızın 5 arkadaşı vardır. Yani ER modeli, sosyal ağların derecelenme yapısını açıklamakta ÇUVALLAR.

### 3.3. Faz Geçişleri ve Dev Bileşen (Giant Component)
Ağa yavaş yavaş kenar eklediğimizi düşünelim ($p$ olasılığını 0'dan 1'e doğru artırıyoruz).
*   **$\langle k \rangle < 1$:** Ağ, birbirinden kopuk küçük adacıklardan (izole bileşenler) oluşur. En büyük bileşen çok küçüktür (logaritmik büyüklükte).
*   **$\langle k \rangle = 1$ (Kritik Eşik):** Sihirli bir an yaşanır. Küçük adacıklar birleşmeye başlar ve ağın yapısı aniden değişir. Buna fizikte **Perkolasyon** (Percolation) veya **Faz Geçişi** (suyun buza dönüşmesi gibi) denir. Ağın geneli "bağlantılı" hale gelmeye başlar.
*   **$\langle k \rangle > 1$:** **Dev Bileşen (Giant Component)** ortaya çıkar. Bu bileşen, ağdaki düğümlerin sabit bir yüzdesini (örneğin %50, %80) kapsar ve tek parça halindedir. Ağın geri kalanı küçük adacıklar halinde kalsa da, dev bir "kıta" oluşmuştur.

Gerçek dünyadaki iletişim ağlarının (İnternet, Telefon şebekesi) işlevsel olması için $\langle k \rangle > 1$ koşulunu sağlaması ve dev bir bileşene sahip olması şarttır (Aksi halde ben sizi arayamazdım).

### 3.4. Rastsal Ağların Başarısı ve Başarısızlığı

#### Başarısı: Küçük Dünya Özelliği
ER modeli, ağın çapının (diameter) ve ortalama yol uzunluğunun ($L$), düğüm sayısı ($N$) ile logaritmik olarak arttığını öngörür:
$$ L \approx \frac{\ln N}{\ln \langle k \rangle} $$
Bu formül doğru çıkmıştır! Milyarlarca web sayfası ($N$ çok büyük) olsa bile, ortalama derece ($\langle k \rangle$) makul bir seviyedeyse, çap çok küçüktür. Yani rastsal ağlar, "dünyanın küçüklüğünü" açıklar. Rastgele atılan bağlar, mesafeleri inanılmaz kısaltır.

#### Başarısızlığı: Kümeleme (Clustering)
Gerçek sosyal ağlarda, "arkadaşımın arkadaşı benim de arkadaşımdır" kuralı işler. Yani oluşan üçgen sayısı yüksektir, kümeleme katsayısı ($C$) büyüktür.
Ancak ER modelinde bağlantılar rastgeledir. Benim Ali ile ve Ayşe ile arkadaş olmam, Ali ile Ayşe'nin tanışma olasılığını etkilemez. Olasılık hala $p$'dir.
$$ C_{rand} = p = \frac{\langle k \rangle}{N} $$
Büyük ağlarda $N$ çok büyük olduğu için ($10^9$ gibi), bu değer sıfıra çok yakındır.
*   **Gerçek:** Sosyal ağlarda $C$ değerleri 0.1 - 0.7 seviyelerindedir.
*   **Model:** Rastsal ağda $C$ değeri $10^{-6}$ seviyesindedir.
**HATA!** ER modeli, sosyal ağlardaki "yerel topaklanmayı" (community structure) asla açıklayamaz. İnsanlar rastgele tanışmaz, sosyal çevrelerinde tanışır.

### 3.5. Sonuç: Neden İhtiyacımız Var?
Erdős-Rényi modeli, gerçek dünyayı temsil etmez. Ancak bir **kıyaslama noktasıdır (Benchmark)**. Bir ağın kümeleme katsayısını hesapladığınızda 0.5 buldunuz. Bu yüksek mi düşük mü? Bunu anlamak için, "Aynı sayıda düğüm ve kenara sahip rastsal bir ağ olsaydı, kümelemesi kaç olurdu?" diye bakarız. Eğer rastsal ağın kümelemesi 0.001 ise, sizin 0.5 değeriniz muazzam bir sosyal yapının (toplulukların) varlığını kanıtlar. Ağ motifi (motif) analizlerinde de "şans eseri oluşma" ihtimalini hesaplamak için ER modeli kullanılır.

## 🔑 4. Anahtar Kavramlar Sözlüğü
*   **Random Network (Rastsal Ağ):** Bağlantıların belirli bir olasılıkla ($p$) rastgele kurulduğu teorik model.
*   **Poisson Distribution:** Rastsal ağların derece dağılımı. Ortalama etrafında toplanma.
*   **Connected Component (Bağlı Bileşen):** İçindeki her düğümden diğerine ulaşılabilen alt küme.
*   **Giant Component (Dev Bileşen):** Ağdaki düğümlerin büyük kısmını ($O(N)$) içine alan en büyük bileşen.
*   **Phase Transition (Faz Geçişi):** Sistemin parametresindeki ($p$) küçük bir değişikliğin, sistemin makro yapısında ani ve büyük bir değişikliğe yol açması.
*   **Percolation Theory:** Bir kafes yapısı üzerinde sıvının süzülüp süzülmeyeceğini (bağlantı olup olmadığını) inceleyen fizik teorisi.

## 🛠 5. Kaynaklar ve İleri Okuma Önerileri
### Kitaplar
1.  **"Network Science"** - Barabási - Bölüm 3 (Random Networks): Konunun en anlaşılır anlatımı. Grafikler ve matematiksel ispatlar içerir.
2.  **"Introduction to Graph Theory"** - Douglas West: Daha matematiksel bir yaklaşım için.

### Simülasyonlar
*   NetLogo'daki "Giant Component" modeli: Kaydırıcıyı (slider) kullanarak kenar sayısını artırın ve dev bileşenin nasıl aniden ortaya çıktığını (kırmızıya boyanan düğümlerle) canlı izleyin. $p$ değerini çok yavaşça artırarak $\langle k \rangle = 1$ olduğu andaki değişimi gözlemleyin.

## 🎯 6. Haftanın Özeti ve Gelecek Haftaya Bakış
Bu hafta, ağların rastgele oluşması durumunda neye benzeyeceğini (Poisson dağılımlı, düşük kümelemeli, küçük çaplı) gördük. Ancak gerçek ağlar böyle değildir; gerçek ağlarda kümeler, gruplar ve klikler vardır. Peki hem rastsal ağlar kadar "küçük" (kısa yollu) hem de sosyal ağlar kadar "kümelenmiş" bir model mümkün müdür? Gelecek hafta, Duncan Watts ve Steven Strogatz'ın 1998'de Nature dergisinde yayınlanan ve bir devrim yaratan **"Küçük Dünya" (Small World)** modelini inceleyeceğiz. Düzenli yapının içine katılan bir tutam rastgeleliğin dünyayı nasıl küçülttüğünü keşfedeceğiz.
