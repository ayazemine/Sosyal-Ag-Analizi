# Hafta 12: Gerçek Dünya Verisi Toplama ve İşleme (Data Mining & Preprocessing)

## 📌 1. Ders Hakkında ve Giriş
Sosyal Ağ Analizi projelerinin %80'i veri toplama, temizleme ve formata sokma (Data Munging / Data Wrangling) ile geçer. Geriye kalan %20 analizdir. Gerçek dünya verisi kitaplardaki veya Gephi örneklerindeki gibi temiz değildir; eksiktir, hatalıdır, gürültülüdür ve karmaşıktır.
*   İsimler farklı yazılır (Ali Yilmaz vs. Ali Yılmaz, Dr. Ali Yılmaz).
*   Mükerrer kayıtlar vardır (Duplicate nodes).
*   Bot hesaplar veri setini kirletir.
*   Veri seti çok büyüktür, bilgisayarı kilitler.

Bu hafta, bir "Veri Dedektifi" gibi çalışacağız. Dijital dünyadaki izleri (Digital Footprints) nasıl toplayacağımızı öğreneceğiz. Twitter (X) gibi platformların API'larını, web scraping tekniklerini ve hazır veri setlerini kullanacağız. En önemlisi, ham veriden (örneğin Tweet metinleri) nasıl anlamlı bir ağ yapısı (Kim kime mention attı?) kurgulayacağımızı, yani **Veri Modelleme**yi öğreneceğiz.

## 📚 2. Konu Başlıkları ve Haftalık Akış
1.  **Veri Kaynakları**
    *   **API (Application Programming Interface):** Twitter, YouTube, Reddit, Spotify API'ları.
    *   **Web Scraping:** HTML parselleme (BeautifulSoup, Selenium).
    *   **Anketler:** Geleneksel veri toplama ve matrise dökme.
    *   **Hazır Arşivler:** SNAP (Stanford), Kaggle, UCI Repository.
2.  **Veri Modelleri: İlişkiyi Tanımlamak**
    *   **Etkileşim Ağları:** Mention, Reply, Retweet (Yönlü, Ağırlıklı).
    *   **İlgi Ağları (Bipartite):** Kullanıcı-Hashtag, Kullanıcı-Beğeni.
    *   **Benzerlik Ağları:** Metin benzerliği, Ortak takipçi (Co-follower).
3.  **Veri Temizleme ve Ön İşleme (Preprocessing)**
    *   Tekilleştirme (De-duplication).
    *   Varlık İsmi Tanıma (Named Entity Recognition - NLP).
    *   Anonimleştirme (Privacy & Ethics - GDPR/KVKK).
4.  **Format Dönüşümü**
    *   JSON'dan Edge List (CSV) oluşturma.
    *   Excel'den matris türetme.

## 📝 3. Detaylı İçerik

### 3.1. API Dünyası: Twitter Örneği
Twitter (X), SAA için altın madenidir. API, yazılımların birbiriyle konuşmasını sağlar. Python'da `Tweepy` gibi kütüphanelerle veri çekebiliriz (API erişimi son yıllarda zorlaşsa da mantık aynıdır).
Süreç şöyledir:
1.  **Developer Hesabı:** Platformdan izin alırsınız ve size `API Key` verirler.
2.  **Sorgu (Query):** Bir anahtar kelime (Hashtag) belirlersiniz (#Seçim2024) veya spesifik bir kullanıcıyı seçersiniz.
3.  **Veri Çekme:** Son 7 gündeki tweetleri çekersiniz. Her tweet bir JSON (JavaScript Object Notation) objesidir. İçinde "user" (gönderen) ve "entities/user_mentions" (bahsedilenler) alanları vardır.
4.  **Parse Etme:** Döngü kurarak kimin kime bahsettiğini çıkarırsınız: `Gönderen (Source) -> Bahsedilen (Target)`.

**Rate Limits:** Platformlar veri çekmeye sınır koyar. 15 dakikada en fazla 180 istek gibi. Yazılımınızın hata verip durmaması için `time.sleep()` komutlarıyla beklemeyi öğrenmelisiniz.

### 3.2. İlişkiyi Tanımlamak: "Kenar" Nedir?
Veri aynıdır ama kuracağınız ağ farklı olabilir. Analiz amacınıza göre kenarı doğru tanımlamalısınız:
*   **Retweet Ağı:** Fikir yayılımını gösterir (Genelde politik analizlerde). Yönü tartışmalıdır: A, B'yi Retweet ederse bilgi B'den A'ya akar (B->A), ama ilgi/saygı A'dan B'ye akar (A->B, Prestige). Genelde A->B olarak modellenir (A, B'yi onaylıyor).
*   **Mention Ağı:** Sohbet ve tartışmayı gösterir. Daha yataydır. Kavga edenler de birbirini mentionlar. Duygu analizi (Sentiment Analysis) ile birleştirilmelidir.
*   **Follower Ağı:** Statik ve uzun vadelidir. Potansiyel erişimi gösterir. Çekmesi çok zordur (Milyonlarca takipçi verisi).

### 3.3. Web Scraping: API Yoksa Ne Var?
Eğer bir sitenin API'sı yoksa (örneğin bir haber sitesi veya forum), sitenin kodunu (HTML) okuyarak veriyi "kazırız".
*   Tarayıcıda "İncele" (Inspect) diyerek sayfa kaynağını görüntüleriz.
*   Yazarın adının hangi etiket (`<span class="author">`) içinde olduğunu buluruz.
*   Python (BeautifulSoup veya Selenium) ile o etiketi bulup içindeki metni çekeriz.
**Uyarı:** `robots.txt` dosyasına ve sitenin kullanım koşullarına uymak etik ve yasal bir zorunluluktur. Kişisel verileri izinsiz kazımak suç olabilir.

### 3.4. Veri Temizliği ve NLP
İnsan isimleri baş belasıdır. "Ahmet K.", "Ahmet Kaya" ve "ahmet kaya" aynı kişi mi? Bilgisayar için bunlar 3 farklı düğümdür.
*   **String Matching:** Levenshtein mesafesi gibi algoritmalarla birbirine çok benzeyen (karakter hatası olan) isimleri tespit edip birleştiririz.
*   **Normalizasyon:** Her şeyi küçük harfe çevirme, Türkçe karakterleri düzeltme.
*   **Doğal Dil İşleme (NLP):** Bir gazete haberinden ağ çıkaracaksanız, metnin içindeki "Kişi" ve "Kurum" isimlerini otomatik tanıyan yapay zeka modelleri (Spacy, NLTK - Named Entity Recognition) kullanırsınız. Metinden: "Erdoğan, Putin ile görüştü." cümlesini alıp `Erdoğan --(görüştü)--> Putin` ağına dönüştürürsünüz.

### 3.5. Etik Sorumluluk
Sırf veri "açık" diye her şeyi yayınlayamazsınız. "Do no harm" (Zarar verme) ilkesi esastır.
*   Kişisel verilerin (telefon, adres) ifşası (Doxing).
*   Hassas konularda (sağlık, politika, cinsel yönelim) kullanıcıların fişlenmesi riski.
*   Bağlamdan koparma.
Araştırmacılar genellikle kullanıcı ID'lerini şifreleyerek (Hashing) veya isimleri gizleyerek (Node 1, Node 2...) çalışır ve sadece makro istatistikleri paylaşır.

## 🔑 4. Anahtar Kavramlar Sözlüğü
*   **API (Uygulama Programlama Arayüzü):** Veriye erişim kapısı.
*   **JSON (JavaScript Object Notation):** Modern verinin taşınma formatı (İç içe geçmiş sözlükler gibi). Okuması kolaydır.
*   **Rate Limiting:** API'ın aşırı kullanımını engellemek için koyduğu hız sınırı.
*   **Web Scraping:** Web sayfalarından otomatik veri çekme.
*   **Bipartite Projection:** İki modlu (Kullanıcı-Hashtag) ağı tek modlu (Hashtag-Hashtag veya Kullanıcı-Kullanıcı) ağa indirgeme işlemi. (Aynı hashtag'i kullanan kullanıcılar birbirine bağlanır).

## 🛠 5. Kaynaklar ve İleri Okuma Önerileri
### Veri Kaynakları
*   **SNAP (Stanford Network Analysis Platform):** Jure Leskovec tarafından yönetilen, devasa hazır ağ veri setleri (Facebook, Enron E-mail, Amazon co-purchase). İlk denemeler için mükemmeldir. (http://snap.stanford.edu)
*   **Kaggle:** Veri bilimi yarışma platformu. "Social Network" diye aratırsanız yüzlerce temiz veri seti bulursunuz.

### Araçlar (Python)
*   **Tweepy:** Twitter API için kütüphane.
*   **BeautifulSoup:** HTML parsing için.
*   **Pandas:** Veri çerçevesi (Dataframe) yönetimi için (Excel'in Python hali). Veriyi temizlemek için en iyi araçtır.

## 🎯 6. Haftanın Özeti ve Gelecek Haftaya Bakış
Bu hafta ellerimizi kirlettik. Veriyi kaynağından (madenden) çıkardık, işledik ve saf bir "Edge List" haline getirdik. Artık elimizde analiz edilmeye hazır, gerçek bir ağ var. Ama bu rakamlar ne anlatıyor?
Gelecek hafta, dönem boyunca öğrendiğimiz **tüm** teknikleri (Merkezilik, Topluluklar, Görselleştirme) bu veri üzerinde uçtan uca uygulayacağımız kapsamlı bir **Vaka Analizi (Case Study)** yapacağız. Sayıların içinden "hikayeyi" çıkaracağız. Dedektifliğin son aşaması: Çözüm.
