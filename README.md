# Python-ile-Veri-Bilimi

Women’s Clothing E-Commerce Reviews: Müşteri Memnuniyet Analizi ve Stratejik Öneriler

Giriş
E-ticaret sektöründe müşteri memnuniyeti, markaların sürdürülebilir başarısı için kritik önemdedir. Bu proje kapsamında, kadın giyim e-ticaret sitesine ait müşteri yorumları analiz edilerek memnuniyetsizliğe neden olan temel faktörler ortaya çıkarılmıştır.
Python ile gerçekleştirilen metin madenciliği ve duygu analizi teknikleri kullanılarak hem negatif yorumlar sınıflandırılmış hem de bu yorumlardaki anahtar temalar belirlenmiştir. Amaç, müşteri deneyimini geliştirmeye yönelik somut ve uygulanabilir öneriler sunmaktır.
Veri madenciliği tekniği: Metin madenciliği ve sınıflandırma (duygu analizi).
Kısa yöntem özeti: Eksik veriler temizlenmiş, yorumlar ön işlemden geçmiş, TF-IDF uygulanmış, TextBlob ile duygu analizi yapılmıştır. Ayrıca konu modelleme(LDA) ile şikayet temaları tespit edilmiştir.

Veri Seti Tanıtımı
Kullanılan veri seti, Kaggle platformunda paylaşılan “Women’s Clothing E-Commerce Reviews veri setidir. E-ticaret, pazarlama alanında bir veri setidir ve 23486 satır ve 10 özellik değişkeni içerir. Toplamda 23.486 müşteri yorumu içermekte olup; ürün tipi, yaş, değerlendirme puanı, olumlu/olumsuz görüş ve yorum metinlerinden oluşmaktadır.
”(https://www.kaggle.com/datasets/nicapotato/womens-ecommerce-clothing-reviews)
Veri sütunları:
	Clothing ID: Ürün kimliği
	Age: Yorum yapan müşterinin yaşı
	Title: Başlık (isteğe bağlı)
	Review Text: Yorum metni
	Rating: 1-5 arası puan
	Recommended IND: Tavsiye edip etmediği
	Positive Feedback Count: Kaç kişi olumlu buldu
	Department Name : Ürün kategorileri

Veri Ön İşleme
	Eksik veriler çıkarıldı.
	Review Text sütunu ön işlemden geçirildi. (küçük harfe çevirme, noktalama temizliği, stopwords çıkarımı, kök alma)
	WordCloud, en sık geçen kelimeleri görselleştirmek için kullanıldı.
	TF-IDF ile yorumlardaki önemli kelimeler puanlandı.

Ön İşlemeden Geçmiş Yorum Örnekleri
![image](https://github.com/user-attachments/assets/ca6cd7c4-372c-41e9-ab44-0f480e46f0bf)

Yöntem ve Uygulama
Sınıflandırma (Classification)
Bu çalışmada, müşteri yorumlarının duygu durumunu belirlemek için metin sınıflandırması yapılmıştır. Yorumlar pozitif ve negatif olarak etiketlenmiş, ardından üç farklı sınıflandırma algoritması denenmiştir.
Kullanılan Algoritmalar: Naive Bayes, KNN, Decision Tree
Eğitim/Test Ayrımı: %80 eğitim ve %20 test olacak şekilde ayrılmıştır. 
![image](https://github.com/user-attachments/assets/c3b80ba8-f3f2-47d9-b1dd-8a331ed30f2b) 
![image](https://github.com/user-attachments/assets/79ed2d38-9cd0-4cf0-9022-306eb8142e92)

Bulgular
Naive Bayes, pozitif yorumları çok başarılı şekilde tahmin etmiş (%99 doğruluk), ancak tüm negatif yorumları pozitif olarak sınıflandırmıştır. (Negatif sınıf tanınmadı.)
Decision Tree, hem pozitif hem negatif sınıfı ayırt edebilmiş ve daha dengeli sonuçlar sunmuştur. Özellikle negatif sınıf için f1-score %36 olmasına rağmen, bu değer Naive Bayes’e göre çok daha iyidir.
Bu nedenle en iyi sonuç Decision Tree algoritmasıyla elde edilmiştir.
Karar Ağacı Konfüzyon Matrisi ve Karar Ağacı
![image](https://github.com/user-attachments/assets/e0809cf3-9904-4f63-8d20-00e69c8f34ee)

![image](https://github.com/user-attachments/assets/2e000a8d-9dc3-4461-88db-2456de868409)

Sonuç ve Eyleme Dönüştürülebilir Çözüm Önerileri

Elde Edilen Bulgular
1)	Ürün Beden ve Kalıp Uyuşmazlıklarına Yönelik Adımlar 
Beden Uyumsuzluğu → Müşterilerin %35'i "küçük geldi" veya "beden tablosu yanıltıcı" diyor.
Konu modellemede ve sık geçen kelime analizinde “size”, “fit”, “small”, “waist”, “petite” gibi kelimeler öne çıkıyor. Bu da kullanıcıların beden ve kalıp uyumsuzluğundan ciddi şekilde şikayetçi olduğunu gösteriyor.

Öneriler
	Akıllı Beden Öneri Sistemi geliştirilmeli (yaş, kilo, önceki alışveriş, kullanıcı geri bildirimine göre öneri).
	Kullanıcılardan alınan beden geri bildirimlerine göre ürün sayfasında “Bu ürün dar kalıptır” gibi uyarılar gösterilmeli.

2)	Ürün Görseli ile Gerçek Ürün Uyumsuzluğu Problemi
Kumaş Kalitesi → "Ucuz hissediliyor", "fotoğraftan farklı" şikayetleri yaygın.
Yorumlarda “look”, “color”, “fabric”, “soft” gibi ifadeler sıklıkla geçiyor. Bu da ürünün görseldeki gibi gelmediğini veya beklentiyi karşılamadığını gösteriyor.

Öneriler
	Gerçek müşterilerin ürün üzerindeki fotoğrafları siteye eklenmeli 
	Her ürün için farklı ışık ve açılardan çekilmiş yüksek çözünürlüklü fotoğraflar eklenmeli.
	Ürünün kumaşı ve doku hissi için videolu tanıtım eklenebilir.


3)	Negatif Yorumlara Yönelik Proaktif İletişim
İade Süreci → "Uzun sürüyor", "para iadesi gecikiyor" yorumları dikkat çekici.
Yorumlarda "disappointed", "return", "not as expected" gibi olumsuz ifadeler bulunuyor. Bu müşteriler kazanılabilecek ama ilgisizlik yüzünden kaybedilen bireyler.
Öneriler
	Olumsuz yorumlara otomatik yanıt sistemi kurulmalı. (Örn: "Yaşadığınız deneyim için üzgünüz, destek ekibimiz sizinle iletişime geçecek.")
	Negatif yorum bırakan müşterilere kişisel indirim kuponu, özür mesajı, ürün değişim opsiyonu sunulmalı.
	Müşteri hizmetleri ekibine sentiment analizi destekli dashboard sunulmalı, anında müdahale için.
Olumsuz yorumların %63’ü beden ve kumaş sorunlarına dayanıyor.
3 yıldız altındaki ürünlerde öneri oranı düşüyor (%5).

 Çözüm Önerileri
	Ürün sayfalarına gerçek ölçüleri içeren interaktif tablo ekleyin.
	Müşteri yorumlarından beden feedback'lerini otomatik highlight eden bir sistem kurun.
	Ürün açıklamalarına "Kumaş: %95 Pamuk, %5 Elastan" gibi teknik detaylar ekleyin.
	Video içeriklerle kumaşın esneme/şeffaflık derecesi gösterilmeli.
	"2 Saatte İade Onayı" gibi bir promosyonla güven artırılabilir.
	Anlaşmalı kargo firmalarıyla ücretsiz iade kolaylığı sağlayın.
	3 yıldız altı alan ürünler otomatik olarak "İyileştirme Listesi"ne alınmalı.
	Bu ürünler için müşteri anketi yapılarak kök neden analizi yapılmalı.

Uygulamanın güçlü yönleri
	Gerçek veri, kapsamlı analiz, duygu analizi ve görsel destek
Geliştirme önerileri
	Otomatik konu modelleme 
	Daha gelişmiş sınıflandırma algoritmaları (Random Forest, SVM)

İşletmeye Yönelik Yorumlar ve Stratejik Çıkarımlar
Bu öneriler doğrudan maliyet azaltma (daha az iade) ve gelir artırma (daha çok tekrar alışveriş) sağlar:
	Akıllı beden öneri sistemi = müşteri deneyimini kişiselleştirerek iade oranını düşürmek.
	“Bu ürün dar kalıptır” uyarıları = şeffaflık → güven.
Bu aksiyonlar müşteri memnuniyetini artırır, iade oranını düşürür:
	Gerçek müşteri fotoğrafları = sosyal kanıt → ikna oranı artar.
	Ürün açıklamalarında kumaş detayları → yanlış beklenti oluşmaz.
	Video içerik = dokunsal hissin yerini alır, güven sağlar.
	Otomatik yanıt sistemi → müşteri yalnız olmadığını hisseder.
	Özür mesajı, kupon → olumsuz deneyim → sadakate dönüşebilir.
	Sentiment dashboard → müşteri hizmetleri ekibi anlık müdahale edebilir, kriz büyümeden çözülür.
Genel Stratejik Yorum
Bu analiz; veri odaklı karar almanın müşteri memnuniyeti, iade oranı ve marka sadakati üzerindeki etkisini doğrudan ortaya koyuyor.
	Uygulanan stratejiler sayesinde:
o	İade oranları azalır
o	Satışlar artar
o	Müşteri yaşam boyu değeri (LTV) yükselir
o	Pazarlama maliyeti düşer (çünkü memnun müşteri markayı başkalarına önerir)
Kaynakça
	Kaggle veri seti:       https://www.kaggle.com/datasets/nicapotato/womens-ecommerce-clothing-reviews
	Python kütüphaneleri: pandas, nltk, TextBlob, sklearn

![Ekran görüntüsü 2025-06-16 221823](https://github.com/user-attachments/assets/2380d546-f892-4de9-953c-0a9eaeab7964)


![Ekran görüntüsü 2025-06-16 221833](https://github.com/user-attachments/assets/ff032aff-d7ce-441a-970d-41d722576428)


![Ekran görüntüsü 2025-06-16 221842](https://github.com/user-attachments/assets/81704122-eec9-40b5-aebe-7a1e29394e13)


![Ekran görüntüsü 2025-06-16 221852](https://github.com/user-attachments/assets/a11867a1-d8a5-4e11-870e-284dcda3c5de)


![Ekran görüntüsü 2025-06-16 221903](https://github.com/user-attachments/assets/b80fddb4-d268-448e-bf8e-c7055709fbac)


 ![Ekran görüntüsü 2025-06-16 221914](https://github.com/user-attachments/assets/2768e632-90c3-4394-b17b-46d0ddaabc9f)


