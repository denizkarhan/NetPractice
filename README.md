# NetPractice

### TCP/IP'nin Özellikleri

TCP, İletim Kontrol Protokolü anlamına gelir . Uygulama programlarının ve cihazların bir ağ üzerinden mesaj alışverişi yapmasını sağlayan bir iletişim standardıdır. İnternet üzerinden paket göndermek için kullanılır.

TCP, bir ağ üzerinden iletilen verilerin bütünlüğünü garanti eder. Verileri iletmeden önce, TCP bir kaynak ile hedefi arasında iletişim başlayana kadar aktif kalan bir bağlantı kurar. Ardından, herhangi bir veri kaybı olmadan uçtan uca teslimatı sağlarken, büyük miktarda veriyi daha küçük paketlere böler.

1. Segment Numaralandırma Sistemi
* TCP, iletilen veya alınan bölümlerin her birine tek tek numaralar atayarak kaydını tutar
* Segmentlere sıra numaraları atanırken, aktarılacak veri baytlarına belirli bir Bayt Numarası atanır
* Alınan segmentlere Onay Numaraları atanır
2. Akış Kontrolü
* Akış kontrolü, bir gönderenin verileri aktarma hızını sınırlar
* Bu, güvenilir teslimatı sağlamak için yapılır
* Alıcı, göndericiye sürekli olarak ne kadar veri alınabileceği konusunda ipucu verir (kayan bir pencere kullanarak)
3. Hata Kontrolü
* TCP, güvenilir veri aktarımı için bir hata kontrol mekanizması uygular
* Hata kontrolü bayt yönelimlidir
* Segmentler hata tespiti için kontrol edilir
Hata Kontrolü şunları içerir – Bozuk Segment ve Kayıp Segment Yönetimi, Sıra dışı segmentler, Yinelenen segmentler vb.
4. Tıkanıklık Kontrolü
* TCP, ağdaki tıkanıklık düzeyini hesaba katar
* Tıkanıklık düzeyi, bir gönderici tarafından gönderilen veri miktarına göre belirlenir

#### Avantajlar
* Güvenilir bir protokoldür.
Bir hata kontrol mekanizması ve kurtarma için bir mekanizma sağlar.
Akış kontrolü sağlar.
Verilerin tam olarak gönderildiği sırayla uygun hedefe ulaşmasını sağlar.
Herhangi bir kuruluşa veya kişiye ait olmayan Açık Protokol.
Ağdaki her bilgisayara bir IP adresi ve her siteye bir alan adı atar, böylece her cihaz sitesinin ağ üzerinden ayırt edilebilir olmasını sağlar.

#### Dezavantajları
* TCP, Geniş Alan Ağları için yapılmıştır, bu nedenle boyutu, düşük kaynaklara sahip küçük ağlar için sorun olabilir.
TCP, ağın hızını yavaşlatmak için birkaç katman çalıştırır.
Doğası gereği jenerik değildir. Yani, TCP/IP paketi dışında herhangi bir protokol yığınını temsil edemez. Örneğin, bir Bluetooth bağlantısı ile çalışamaz.
Yaklaşık 30 yıl önce geliştirilmelerinden bu yana herhangi bir değişiklik yapılmadı.
