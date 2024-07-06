# Havayolu Rezervasyonları Tamamlama ve Ek Hizmet Talep Analizi

## Proje Bilgileri

- **Proje Adı:** PYTHON'DA MAKİNE ÖĞRENMESİ
- **Proje Yürütücüsü:** HABİB ŞAKO
- **Mentör:** BEHLUL KIZILTAŞ
- **Rapor Tarihi:** 14.06.2024

## Özet

Havayolu sektörü, müşteri memnuniyetini artırmak ve operasyonel verimliliği maksimize etmek için veri odaklı karar verme süreçlerine giderek daha fazla önem vermektedir. Bu bağlamda, yolcu davranışlarını ve tercihlerini anlamak, havayolu şirketlerinin hem gelirlerini artırmalarına hem de müşteri deneyimini iyileştirmelerine yardımcı olabilir. Özellikle rezervasyon tamamlama, ekstra bagaj talepleri ve uçak içi yemek talepleri gibi kritik hizmetlerin doğru tahmin edilmesi, hem operasyonel hem de stratejik avantajlar sağlamaktadır.

Bu çalışmanın amacı, havayolu şirketlerinin müşteri davranışlarını doğru bir şekilde tahmin edebilecek modeller geliştirebilmesi ve bu tahminlerin operasyonel ve stratejik karar alma süreçlerinde etkin bir şekilde kullanılmasıdır. Bu doğrultuda, yapılan tahminlerin havayolu şirketlerine nasıl fayda sağlayabileceği ve bu tahminlerin nerede ve nasıl kullanılabileceği üzerinde durulmuştur. Bu çalışma, havayolu sektöründe veri analitiği ve makine öğrenimi uygulamalarının önemini vurgularken, aynı zamanda şirketlerin rekabet avantajı elde etmelerine ve müşteri memnuniyetini artırmalarına yardımcı olmayı amaçlamaktadır.

Ayrıca hangi ek hizmetlerin daha fazla talep gördüğünü belirlemek ve bu hizmetlerin talebi ile gelir arasındaki ilişkiyi analiz etmek için ek hizmetlerden kaynaklanan geliri artırmak için stratejiler önerilecektir.

## Veri Seti

Bu veri seti, yolcu sayısı, satış kanalı, seyahat türü, satın alma teslim süresi, konaklama süresi, uçuş saati, uçuş günü, rota, rezervasyon menşei ve müşterinin ekstra bagaj isteyip istemediğini belirten çeşitli bayraklar dahil olmak üzere havayolu rezervasyonları hakkında bilgiler içerir. Tercih edilen koltuk veya uçakta yemek. Veri seti ayrıca toplam uçuş süresini ve rezervasyonun tamamlanıp tamamlanmadığını gösteren bir bayrağı da içerir.

### Veri setinin içeriğinde bulunan sütunların adları ve tuttuğu bilgiler:

- **num_passengers:** Seyahat eden yolcu sayısı
- **sales_channel:** Satış kanalı rezervasyonu şu tarihte yapıldı:
- **trip_type:** Yolculuk Tipi (Gidiş-Dönüş, Tek Yön, Dairesel Yolculuk)
- **purchase_lead:** Seyahat tarihi ile rezervasyon tarihi arasındaki gün sayısı
- **length_of_stay:** Varış yerinde geçirilen gün sayısı
- **flight_hour:** Uçuşun kalkış saati
- **flight_day:** Uçuşun kalkış haftasının günü
- **route:** Menşei -> varış uçuş rotası
- **booking_origin:** Rezervasyonun yapıldığı ülke
- **wants_extra_baggage:** Eğer müşteri rezervasyon sırasında ekstra bagaj istediyse
- **wants_preferred_seat:** Eğer müşteri rezervasyon sırasında tercih edilen bir koltuk istiyorsa
- **wants_in_flight_meals:** Müşteri rezervasyon sırasında uçakta yemek istiyorsa
- **flight_duration:** Toplam uçuş süresi (saat cinsinden)
- **booking_complete:** Müşterinin rezervasyonu tamamlayıp tamamlamadığını gösteren bayrak

## Giriş

Bu bitirme projesinin amacı, havayolu rezervasyonlarının tamamlanma olasılığını tahmin eden bir model geliştirmektir. Projede kullanılacak veri setinde, müşterilerin rezervasyon yapma ve tamamlama davranışları ile ilgili çeşitli değişkenler bulunmaktadır. Bu değişkenler kullanılarak, müşterilerin rezervasyonlarını tamamlama olasılıkları analiz edilecek ve tamamlanmamış rezervasyonları azaltmaya yönelik stratejiler önerilecektir.

### Temel Sorun: Rezervasyon Tamamlama Olasılığı

Havayolu şirketleri, müşteri rezervasyonlarının tamamlanmaması durumunda ciddi gelir kayıpları yaşayabilirler. Tamamlanmamış rezervasyonlar hem koltukların boş kalmasına hem de müşteri memnuniyetsizliğine yol açabilir. Bu projenin temel amacı, veri setindeki bilgilerden yararlanarak müşterilerin rezervasyonlarını tamamlama olasılığını tahmin etmektir. Bu olasılığı doğru bir şekilde tahmin edebilmek, havayolu şirketlerinin müşteri ilişkileri yönetimini iyileştirmelerine ve gelirlerini artırmalarına yardımcı olacaktır.

### Ek Sorun: Ek Hizmetlerin Talep ve Gelir Üzerindeki Etkisi

Projenin ikinci aşamasında, havayolu şirketinin sunduğu ek hizmetlerin (örneğin, bagaj hizmetleri, yiyecek ve içecek hizmetleri) hangi derecede talep gördüğü ve bu hizmetlerin şirketin gelirleri üzerindeki etkisi analiz edilecektir. Müşterilerin hangi ek hizmetlere daha fazla ilgi gösterdiği ve bu hizmetlerin talebi ile gelir arasındaki ilişkinin belirlenmesi, havayolu şirketlerine ek gelir kaynaklarını optimize etme fırsatı sunacaktır.

## Hedef ve Stratejiler

Bu projede geliştirilecek model ve analizler sonucunda, havayolu şirketleri için şu stratejiler önerilecektir:

- **Rezervasyon Tamamlama Stratejileri:** Müşterilerin rezervasyonlarını tamamlama olasılığını artırmak için hedefli pazarlama kampanyaları ve teşvik programları oluşturulabilir. Örneğin, rezervasyonlarını tamamlama olasılığı düşük olan müşteri segmentlerine özel indirimler veya esnek rezervasyon seçenekleri sunulabilir.
- **Ek Hizmet Stratejileri:** Talebi yüksek olan ek hizmetlerin tanıtımına yönelik kampanyalar düzenlenebilir ve bu hizmetlerin fiyatlandırma stratejileri gözden geçirilebilir. Ayrıca, ek hizmetlerin paket halinde sunulması ve bu paketlerin farklı müşteri segmentlerine özel olarak uyarlanması, gelirlerin artırılmasına katkıda bulunabilir.

Bu şekilde, havayolu şirketleri hem rezervasyon tamamlama oranlarını artırabilir hem de ek hizmetlerden elde edilen gelirleri maksimize edebilirler. Projenin nihai amacı, havayolu şirketlerinin operasyonel verimliliğini ve müşteri memnuniyetini artırarak rekabet avantajı sağlamalarına yardımcı olmaktır.

## Materyal & Metot

Bu bölümde, projenin gerçekleştirilmesi için kullanılan yöntemler ve adımlar detaylı olarak açıklanmaktadır.

### Veri Ön İşleme:

- Veri setindeki eksik ve hatalı verilerin temizlenmesi.
- Kategorik verilerin kodlanması ve gerekirse ölçeklendirilmesi.

### Keşifsel Veri Analizi (EDA):

- Değişkenlerin dağılımlarının incelenmesi.
- Rezervasyon tamamlama durumuyla ilişkili olabilecek değişkenlerin tespit edilmesi.

### Model Geliştirme ve Değerlendirme:

- Farklı makine öğrenimi algoritmalarının (lojistik regresyon, karar ağaçları, random forest, vb.) kullanılarak modellerin geliştirilmesi.
- Modellerin performanslarının doğruluk, hassasiyet, özgüllük gibi metriklerle değerlendirilmesi.

### İlişki Analizi ve Strateji Önerileri:

- Rezervasyon tamamlama durumu ile diğer değişkenler arasındaki ilişkilerin korelasyon ve regresyon analizleri ile incelenmesi.
- Tamamlanmamış rezervasyonları azaltmaya yönelik, örneğin belirli ülkeler veya belirli ek hizmetlerin talebi gibi faktörlere dayalı stratejiler geliştirilmesi.

### Ek Hizmet Talebi ve Gelir Analizi:

- Ek hizmet taleplerinin analiz edilmesi ve hangi ek hizmetlerin daha fazla talep gördüğünün belirlenmesi.
- Ek hizmet talebi ile gelir arasındaki ilişkinin analiz edilmesi.
- Ek hizmetlerden kaynaklanan geliri artırmak için stratejiler önerilmesi.

## Makine Öğrenimi Modeli Seçimi

1. **Rezervasyon Tamamlama Olasılığı:** Karar Ağaçları, Lojistik Regresyon veya Random Forest. Rezervasyonların tamamlanma olasılığını tahmin etmek için karar ağaçları, lojistik regresyon ve random forest modelleri kullanılabilir. Karar ağaçları ve random forest modelleri, veri özelliklerine dayalı olarak güçlü sınıflandırma yetenekleri sunarken, lojistik regresyon, rezervasyon tamamlama olasılığını doğrudan tahmin etmek için etkili bir yöntem sağlar. 
    - **Hedef değişken:** `booking_complete`
2. **Ek Hizmetlerin Talebi:** K-Means veya GMM. Yolcuların ek hizmet taleplerini değerlendirmek için K-Means ve Gaussian Mixture Models (GMM) kullanılabilir. Bu modeller, yolcuların ek hizmet taleplerine göre segmentlere ayrılmasını sağlar ve bu segmentler, pazarlama stratejilerini özelleştirmek ve gelir artırıcı fırsatlar yaratmak için kullanılabilir.
    - **Hedef değişkenler:** `wants_extra_baggage`, `wants_preferred_seat`, `wants_in_flight_meals`

## Yapılan Çalışmalar

### Veri Yükleme:

Proje başlangıcında veri seti `Latin1` karakter kodlaması kullanılarak yüklendi. Bu işlem sırasında veri setindeki boş değerler kontrol edildi ve veri temizleme işlemleri gerçekleştirildi.

### Kategorik Verilerin Analizi:

Kategorik veriler incelendi ve `unique` fonksiyonu kullanılarak her sütundaki benzersiz değerler tespit edildi. Kategorik sütunlardaki değerler gerektiğinde kodlandı ve analiz için uygun hale getirildi.

### Aykırı Değerlerin Tespiti ve Analizi:

Veri setinde aykırı değerler belirlendi ve bu aykırı değerlerin veri analizi üzerindeki etkileri değerlendirildi. Aykırı değerler gerektiğinde veri setinden çıkarıldı veya uygun şekilde işlendi.

### Özellik Mühendisliği:

Veri setindeki mevcut özelliklere ek olarak, yeni özellikler oluşturuldu ve mevcut özelliklerin daha anlamlı temsilleri elde edildi. Özellik mühendisliği, model performansını artırmak için önemli bir adımdır.

### Veri Setinin Hazırlanması:

Veri seti dört farklı şekilde hazırlandı:
1. Orijinal veri seti
2. Aykırı değerler çıkarılmış veri seti
3. Özellik mühendisliği uygulanmış veri seti
4. Aykırı değerler çıkarılmış ve özellik mühendisliği uygulanmış veri seti

Bu farklı veri setleri üzerinde modeller eğitildi ve değerlendirildi.

## Model Eğitim ve Değerlendirme

Modellerin eğitimi ve değerlendirilmesi için geliştirilmiş fonksiyonlar kullanıldı. Her veri seti için en iyi model ve doğruluk değerleri belirlendi ve raporlandı.

## Sonuçlar

Çeşitli veri ön işleme teknikleri ve model değerlendirmeleri sonucunda elde edilen bulgular aşağıda özetlenmiştir:

- **Logistic Regression ve Random Forest modelleri genellikle en iyi performansı göstermiştir.**
- **Veri setleri üzerinde yapılan değerlendirmeler sonucunda en iyi modeller belirlenmiştir.**

## Kullanım Kılavuzu

Projenin kodlarını çalıştırmak için aşağıdaki adımları izleyin:

1. **Proje dosyalarını indirin ve uygun bir dizine çıkarın.**
2. **Gerekli Python kütüphanelerini yükleyin:**
   ```bash
   pip install -r requirements.txt
