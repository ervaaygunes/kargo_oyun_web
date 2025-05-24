# Yapay Zeka Kullanım Belgesi

**Proje Adı:** Merdiven & Kargo Fırlatma Oyunu  
**Geliştirici:** Erva Aygüneş  
**Tarih:** 25/05/2025  

---

Bu proje geliştirilirken yapay zeka destekli araçlardan hem bilgi edinme hem de üretkenliği artırma amacıyla faydalanılmıştır. Projede yer alan mekanikler, kontroller, görsel efektler ve ses sistemleri gibi birçok unsurda yapay zekadan destek alınmıştır. Ancak tüm entegrasyon, kontrol ve karar süreçleri geliştirici tarafından gerçekleştirilmiştir. Bu dosyada, proje boyunca AI araçlarıyla yapılan etkileşimler ve alınan çıktılar detaylı şekilde belgelenmiştir.

---

## Kullanılan Yapay Zeka Araçları

| Araç            | Kullanım Amacı                                                                 |
| --------------- | ----------------------------------------------------------------------------- |
| ChatGPT (GPT-4) | Oyun mekaniklerini tasarlama, kontrolleri planlama, canvas hakkında bilgi alma, ses üretimi konusunda açıklama alma |
| Cursor IDE + AI | Kod tamamlama, çizim fonksiyonları yazma, fırlatma fiziği hesapları, öneri sunma |

---

## ChatGPT ile Etkileşimlerim

### Canvas Nasıl Kullanılır?

**Prompt:**  
HTML5 canvas nedir? createLinearGradient, arc, fillRect gibi fonksiyonları nasıl kullanabilirim? Bunlarla bir bina veya gökyüzü nasıl çizilir?

**Yanıt:**  
ChatGPT, HTML5 canvas yapısının nasıl çalıştığını, 2D grafik çiziminde hangi komutların ne işe yaradığını açıkladı. Özellikle getContext('2d') ile başlayan çizim sürecini, katman mantığıyla birlikte anlattı. ctx.arc() ile daire bulutlar, fillRect ile bina gövdeleri çizilebileceğini; createLinearGradient ile gökyüzü geçişlerinin estetik hale getirilebileceğini örnek kodlarla gösterdi. Bu sayede oyun içindeki bina, kutu ve arka plan gibi görselleri dışarıdan dosya kullanmadan kendim çizdim.

---

## Oyun Mekaniği ve Kontroller

**Prompt:**  
SPACE tuşuna basılı tutarak güç biriktireyim, bırakınca belirli açıyla kutu fırlasın. Ayrıca ← → tuşları ile açıyı değiştirebileyim. Canvas ile gösterilen merdivenin ucundan bu fırlatma olsun. Nasıl yaparım?

**Yanıt:**  
ChatGPT bu senaryoyu ayrıntılı adımlarla cevapladı. Öncelikle keydown ve keyup olaylarının nasıl yönetileceğini, setInterval veya Date.now() ile geçen süreye göre gücün hesaplanabileceğini anlattı. Ardından, açı bilgisinin derece olarak alınması gerektiğini ve Math.cos ile Math.sin kullanarak X ve Y bileşenlerine çevrilebileceğini söyledi. Canvas üzerinde bir nesnenin belirli bir yönde hareket ettirilmesi için bu vektörlerle pozisyonun her frame’de güncellenmesi gerektiğini belirtti. Bu bilgiler ışığında merdiven mekanizmasını da entegre ederek, gerçek zamanlı fırlatma sistemi kurdum.  
Ek olarak, kullanıcı kontrollerinin doğru geri bildirim vermesi için açının ekranda gösterilmesini, şarj barı ile güç seviyesinin takip edilebilmesini önerdi. Bunlar da projeye eklendi.

---

## Arka Plan Müziği ve Ses Efektleri

**Prompt:**  
Oyunda çalacak basit ama dinamik bir arka plan müziği üretmek istiyorum. Ayrıca kutu fırlatıldığında bir ses efekti olsun. Dosya kullanmadan Web Audio API ile bunu nasıl yaparım?

**Yanıt:**  
ChatGPT, Web Audio API'nin temel mimarisini açıkladı: AudioContext, createBuffer, createOscillator, gainNode gibi parçaların nasıl birleştirilerek ses yaratılabileceğini gösterdi. Arka plan müziği için pentatonik skala notalarından oluşan kısa ve tekrarlı bir dizi oluşturmayı önerdi. Her bir notanın süresi, geçiş aralığı ve frekans bilgisiyle nasıl bir melodi oluşturulabileceğini belirtti. Ayrıca, kutu fırlatıldığında çıkacak "whoosh" sesi için sinüs dalgasının frekansını zamanla azaltarak sesin sönümlenmesini önerdi.  
Bu ses sistemleri projeye entegre edildi ve arka planda sürekli çalan bir müzik ile aksiyona bağlı ses efektleri sağlandı.

---

## Cursor IDE ile Neler Yaptım?

Cursor, kod yazarken otomatik öneriler ve tamamlamalar sunarak projenin bazı kritik alanlarında büyük kolaylık sağladı. Özellikle aşağıdaki konularda etkili oldu:

### Grafik Fonksiyonları
- Cursor'un kod önerme yeteneği sayesinde, birçok görsel bileşeni yazarken vakit kazandım:
  - `createBuildingImage()`: Binanın pencere dizilimi, gövde dolgusu ve detay hatlarını AI önerisiyle oluşturdum.
  - `createSkyImage()`: Çok katmanlı gradient arka planı ve bulut şekillerini çizerken yapay zeka bana uygun arc kombinasyonlarını önerdi.
  - `createCrateImage()`: Kutuya ahşap dokusu ve çapraz hatlar kazandırmamı sağladı.

### Fırlatma Fiziği ve Oyun Döngüsü
- Güç değişkeninin zamanla artışı, fırlatma sırasında vektörel hesaplar ve yerçekimi simülasyonu Cursor’un yardımıyla sadeleştirildi.
- Paket yere çarptığında etki efektlerinin (parçacık yayılması, parlayan halkalar) görsel olarak eklenmesi önerildi.
- `requestAnimationFrame` döngüsü içinde her bir öğenin nasıl güncellenmesi gerektiği konusunda rehberlik etti.

---

## Sonuç

Bu projede, ChatGPT ve Cursor gibi yapay zeka araçlarından bilinçli ve kontrollü şekilde faydalandım. Amaç asla sadece koda sahip olmak değil; öğrenmek, fikir geliştirmek ve kaliteli bir oyun deneyimi oluşturmaktı.  
Yapay zeka bana sadece neyin "nasıl yapılabileceğini" gösterdi. Kodun bütünlüğü, özgünlüğü ve entegrasyonu tamamen benim kontrolümde gerçekleşti. Bu belge, yapay zekadan faydalanan ama yaratıcı sürecin merkezinde insanın yer aldığı bir projeyi temsil etmektedir.
