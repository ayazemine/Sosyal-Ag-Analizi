# Hafta 13: Vaka Analizi ve Sonuçların Yorumlanması (Case Study & Storytelling)

## 📌 1. Ders Hakkında ve Giriş
Bütün dönem boyunca parça parça öğrendiğimiz araçları (Merkezilik ölçüleri, Topluluk tespiti, Görselleştirme, Veri işleme) artık birleştirme zamanı geldi. Sosyal Ağ Analizi, sadece hesaplama yapmak değildir; hesaplama sonuçlarından anlamlı bir **hikaye** ve **içgörü (insight)** çıkarmaktır. Veri analisti ile veri bilimci arasındaki fark, hikaye anlatabilme yeteneğidir.

Bir yöneticiye veya halka sunum yaparken "Düğüm 45'in arasındalık değeri 0.12'dir" derseniz kimse bir şey anlamaz ve kimsenin umurunda olmaz. "Mehmet Bey, şirketteki departmanlar arasındaki iletişimi sağlayan tek kişidir, o hastalanırsa işler durur (Bus Factor risk)" demeniz gerekir. Bu derste, ham veriden yola çıkıp, analiz adımlarını tamamlayıp, sonunda eyleme dönüştürülebilir sonuçlar (Actionable Insights) üretmeyi ve bunları etkili bir şekilde sunmayı öğreneceğiz.

Bu hafta, gerçek veya gerçeğe yakın senaryolar (örneğin "Game of Thrones karakter ağı" veya "Enron Şirketi E-posta Skandalı") üzerinden adım adım giderek tam kapsamlı bir analiz yürüteceğiz.

## 📚 2. Konu Başlıkları ve Haftalık Akış
1.  **Analiz Boru Hattı (Pipeline)**
    *   Soru Sorma -> Veri Toplama -> Modelleme -> Hesaplama -> Görselleştirme -> Yorumlama.
    *   Keşifsel Veri Analizi (EDA) ile veriyi tanıma.
    2.  **Vaka Çalışması 1: Politik Kutuplaşma (Twitter)**
    *   Bir seçim dönemindeki hashtag analizi.
    *   Yankı odalarının tespiti (Modülerlik skoru ile).
    *   Kanaat önderlerinin rolü (Sayfa vs. Arasındalık farkı).
3.  **Vaka Çalışması 2: Örgütsel Ağ Analizi (ONA - Organizational Network Analysis)**
    *   Bir şirketin e-posta trafiği.
    *   Resmi hiyerarşi vs. İnformal ağ.
    *   Siloların tespiti ve iletişim kopuklukları.
4.  **Veri Hikayeleştirme (Data Storytelling)**
    *   Grafiği temizlemek (Gürültüyü atmak).
    *   Doğru metriği seçmek.
    *   "So what?" (Ee, ne olmuş?) sorusuna cevap vermek.

## 📝 3. Detaylı İçerik

### 3.1. Analiz Sorusu (Research Question)
Her analiz bir soruyla başlar. Soru olmadan veriye dalmak, okyanusta pusulasız yüzmektir.
*   "Şirketimizde inovasyon neden yavaş?"
*   "Hangi influencer markamız için en etkili olur?"
*   "Terör örgütünün lideri kim?"
*   "Bu hastalığın yayılmasını nasıl durdururuz?"

Soruyu doğru sormak, hangi metriği kullanacağınızı belirler. (Gizli lideri arıyorsanız Merkezilik, inovasyon arıyorsanız Yapısal Boşluklar/Arasındalık, kutuplaşma/ayrışma arıyorsanız Modülerlik bakmalısınız).

### 3.2. Adım Adım Analiz: Enron E-Posta Ağı Örneği
2001'de batan ABD enerji devi Enron'un halka açılan 500.000 e-postalık veri seti, SAA'nın "meyve sineği"dir (standart laboratuvar deneyi). Gelin bu şirketin röntgenini çekelim.
1.  **Makro Bakış (Sağlık Kontrolü):** Ağın yoğunluğu ne? (Çok düşük, bu normal). Dev bileşen var mı? (Evet, çalışanların %90'ı birbirine bağlı). Çap ne?
2.  **Merkezilik Analizi:**
    *   *Derece:* En çok e-posta atan/alanlar. (Genellikle sekreterler, operasyonel müdürler ve toplu mail atan IK çıkar). Bu bize lideri vermez.
    *   *Arasındalık:* Departmanlar arası köprüler. (Burada ilginç isimler çıkar; kriz anında bilgiyi yönetenler, "Fixer"lar).
    *   *Karşılaştırma:* Resmi org şeması ile bu ağ uyuşuyor mu? Üst yönetim izole mi? Enron örneğinde üst yönetimin "Clique" (kapalı grup) olduğu ve alt taraftan koptuğu görülmüştür.
3.  **Topluluk Analizi:**
    *   Louvain algoritmasını çalıştır.
    *   Gruplar departmanlara (Hukuk, Finans, Ticaret) denk geliyor mu?
    *   **Silo Analizi:** Finans ekibi ile Ticaret ekibi konuşuyor mu? (Modülerlik matrisine bak). Eğer konuşmuyorlarsa (ki Enron'da öyleydi - bilançolarla oynayanlar ile satış yapanlar kopuktu), denetim eksikliği ve dolandırıcılık riski vardır.
4.  **Zaman Analizi (Temporal):**
    *   Krizin başladığı, hisselerin düştüğü haftalarda ağ nasıl değişti? İletişim arttı mı (panik) yoksa azaldı mı (sessizlik)? Genellikle kriz anında iletişim merkezileşir ve gruplaşma artar.

### 3.3. Yorumlama Sanatı: Rakamlardan Stratejiye
Bulgu: "Pazarlama ekibi ile AR-GE ekibi arasında sadece 1 tane bağlantı var (Ahmet)."
*   **Yorum (Risk):** Şirket büyük risk altında. Ahmet işten ayrılırsa veya hastalanırsa, AR-GE ne ürettiğini satıcıya anlatamaz, Pazarlama müşterinin ne istediğini mühendise söyleyemez.
*   **Öneri (Aksiyon):**
    1.  Ahmet'i yedekleyin veya ödüllendirin.
    2.  Bu iki ekip arasında "zorunlu" ortak projeler veya sosyal etkinlikler düzenleyerek yeni köprüler oluşturun.

Bulgu: "X Politikacısının takipçileri, Y Politikacısının takipçileriyle hiç etkileşime girmiyor (Modülerlik Skoru 0.65)."
*   **Yorum:** Ciddi bir kutuplaşma ve yankı odası var. Y tarafına yönelik yapılacak bir propaganda/ikna çalışması tamamen boşa gider çünkü mesaj o ağa giremez.
*   **Strateji:** İki grubun da güvendiği tarafsız (köprü) aktörler veya ortak konular (ekonomi, spor) üzerinden yumuşak geçiş sağlanmalıdır.

### 3.4. Raporlama ve Görselleştirme İpuçları
Raporunuzda karmaşık "Tüy Yumakları" (Hairballs) kullanmayın. Yönetim kurulu karmaşık çizgilere bakmaz.
*   **Az Çoktur:** Sadece anlatmak istediğiniz hikayeyi destekleyen düğümleri gösterin (Filtreleme). Gerekirse binlerce düğümü gizleyin.
*   **Etiketleme:** Önemli düğümlerin ismini yazın.
*   **Renk:** Renkleri bir anlam ifade edecek şekilde (Departman, Duygu durumu) kullanın ve mutlaka bir lejand (legend) ekleyin.
*   **Özet:** En önemli 3 sonucu ("Key Findings") madde madde ve en başa yazın.

## 🔑 4. Anahtar Kavramlar Sözlüğü
*   **Exploratory Data Analysis (EDA):** Veriyi anlamak, hataları görmek için yapılan ilk istatistiksel ve görsel keşif turları.
*   **Organizational Network Analysis (ONA):** SAA yöntemlerinin şirket yönetimine, İK süreçlerine ve verimlilik analizine uygulanması.
*   **Silo Effect:** Bir organizasyonun alt birimlerinin kendi içine kapanıp diğerleriyle iletişim kurmaması durumu.
*   **Actionable Insight (Eyleme Dönüştürülebilir İçgörü):** Sadece "durum böyle" diyen değil, "şunu yapmalısın" dedirten bilgi. Bus Factor buna örnektir.

## 🛠 5. Kaynaklar ve İleri Okuma Önerileri
### Vaka Örnekleri
*   **"Enron Email Dataset Analysis":** İnternette bu başlıkla aratıldığında yüzlerce Jupyter Notebook, makale ve görselleştirme bulunur. İncelemesi çok öğreticidir.
*   **"Game of Thrones Network Analysis":** Karakterlerin birlikte sahnede görünme sıklığına göre matematiksel analiz yapan çalışmalar. (Örn: Andrew Beveridge'in "Network of Thrones" çalışması).

### Kitap
*   **"Storytelling with Data"** - Cole Nussbaumer Knaflic: Analiz sonuçlarını etkili sunmak, doğru grafiği seçmek için başucu kitabı.

## 🎯 6. Haftanın Özeti ve Gelecek Haftaya Bakış
Bu hafta, bir SAA projesinin başından sonuna nasıl yürütüldüğünü, verinin nasıl stratejiye ve hikayeye dönüştüğünü simüle ettik. Teknik becerilerimizi (Hard Skills - Python, Gephi) yorumlama becerilerimizle (Soft Skills - İletişim, Strateji) birleştirdik.
Gelecek hafta, dönemin finali. Sizin sıranız. **Proje Sunumları** haftasında, kendi seçtiğiniz bir ağ üzerinde yaptığınız analizi dinleyeceğiz. Sadece doğru analizi değil, iyi hikayeyi de ödüllendireceğiz. Ve son olarak ağ biliminin geleceğini (Yapay Zeka, GNN) konuşup vedalaşacağız.
