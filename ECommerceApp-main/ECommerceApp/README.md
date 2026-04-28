🛒 E-Commerce App - Yazılım Test ve Kalite Raporu
📌 Proje Konusu

Bu proje, bir e-ticaret sisteminde sepet (cart) ve sipariş (order) süreçlerinin test otomasyonu üzerine odaklanmaktadır. Kullanıcının ürün seçmesi, sepete eklemesi, sipariş oluşturması ve ödeme yapması gibi temel akışlar ele alınmıştır.

⚙️ Kullanılan Teknolojiler
💻 C#
🧪 NUnit
⚡ .NET 10.0
🎯 Projenin Amacı

Bu çalışmanın temel amacı, sistem içerisine bilinçli olarak yerleştirilmiş mantıksal hataları (bug) farklı test teknikleri kullanarak tespit etmektir.

Kullanılan test yaklaşımları:

🔍 White Box Test
🎯 Black Box Test
⚙️ Gray Box Test
🔗 Integration Test
📊 Test Senaryoları ve Sonuç Raporu

Sistem üzerinde toplam 10 adet test senaryosu çalıştırılmıştır.

✅ 5 test başarılı (PASS)
❌ 5 test başarısız (FAIL)

Başarısız olan testler, sistemde bilerek bırakılmış hataları ortaya çıkarmıştır. Bu sayede farklı test yöntemlerinin etkinliği gözlemlenmiştir.

1️⃣ Unit Test (White Box)

İç kod yapısı, algoritmalar ve mantıksal dallanmalar (if/else) hedef alınarak yazılmış testlerdir.

✅ TC01: GetTotalPrice (100 TL altı) → Sepet tutarı doğru hesaplandı.
❌ TC02: GetTotalPrice (100 TL üstü indirim)
👉 Neden Başarısız?
Sistemde %10 indirim uygulanması gerekirken, yanlış bir hesaplama yapılmış ve tutardan direkt 100 TL çıkarılmıştır.
Beklenen: 135 TL
Gerçek: 50 TL
✅ TC03: CartClear → Sepet başarıyla temizlendi.
2️⃣ Black Box Test

Sistemin iç yapısı bilinmeden, sadece giriş ve çıkışlara göre test edilmiştir (edge case odaklı).

❌ TC04: Negative Quantity
👉 Neden Başarısız?
Kullanıcı sepete -2 adet ürün eklediğinde hata alınması gerekirken, sistem bu durumu kontrol etmemiştir.
✅ TC05: Empty Cart Order → Boş sepetle sipariş engellendi.
❌ TC06: Negative Payment Amount
👉 Neden Başarısız?
Ödeme servisi negatif tutarı reddetmesi gerekirken işlemi başarılı (True) olarak kabul etmiştir.
3️⃣ Gray Box Test

Sistem iç durumu (state) ile dış davranış birlikte değerlendirilmiştir.

❌ TC07: Insufficient Stock
👉 Neden Başarısız?
Stoktan fazla ürün sipariş edilmesine rağmen sistem siparişi kabul etmiş ve stok değeri -1’e düşmüştür.
❌ TC08: Successful Payment → Cart Clear
👉 Neden Başarısız?
Ödeme başarılı olmasına rağmen sepet temizlenmemiştir.
Beklenen: 0 ürün
Gerçek: 1 ürün kaldı
4️⃣ Integration Test

Modüllerin birbiriyle uyumlu çalışması test edilmiştir.

✅ TC09: End-to-End Order Flow
👉 Ürün ekleme → sipariş → stok düşme süreci başarıyla çalıştı.
✅ TC10: Order With Discount
👉 İndirim hatalı olsa bile sistem çökmeden siparişi tamamladı.
✔️ Bu nedenle integration seviyesinde PASS verilmiştir.
📌 Sonuç ve Aksiyonlar

Test sonuçlarına göre sistemin canlı ortama alınmadan önce aşağıdaki iyileştirmelere ihtiyacı vardır:

⚠️ Stok kontrol mekanizması eklenmeli
🧹 Sipariş sonrası sepet temizleme işlemi garanti altına alınmalı
💸 İndirim algoritması düzeltilmeli
🚫 Negatif değer girişleri (adet ve ödeme) engellenmeli
🚀 Genel Değerlendirme

Bu proje, farklı test tekniklerinin gerçek hayattaki hataları nasıl yakaladığını açıkça göstermektedir. Özellikle:

White Box → Mantıksal hataları
Black Box → Kullanıcı kaynaklı hataları
Gray Box → Sistem durumu hatalarını
Integration → Modüller arası uyumu

başarılı şekilde ortaya çıkarmıştır.