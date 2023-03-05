# NetPractice

## Giriş

Bu proje, ağ oluşturmayı keşfetmenize olanak tanıyan genel bir uygulama alıştırmasıdır.
Küçük ölçekli ağları yapılandırmanız gerekecek. Bunu yapmak için, bu kavramları anlamak gerekli olacaktır.

*  [Important concepts](#important-concepts)
    *    [TCP](#tcp)  
    *    [IP address](#ip-address)
    *    [TCP/IP model](#tcp/ip-model)
    *    [Subnet mask](#subnet-mask)
    *    [Switch](#switch)
    *    [Router](#router)

## Önemli Kavramlar

### TCP

   <br>
      <img src="https://github.com/K-zew/Netpractice/blob/main/Imgs/tcp-vs-udp-communications.png?raw=true" alt="TCP">
   <br>

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

NASIL veri gönderilir:
TCP protokolünde bildiğimiz gibi ilk defa hedefe bir paket göndermeye çalışır ve bağlantının canlı kalmasını sağlayarak paketin iyi alınıp alınmadığını kontrol eder. Her seferinde gönderilecek bir paket ekler, yani daha önce gönderilen paketlerin iki katını ikinci kez gönderir ve bağlantının iyi durumda olup olmadığını kontrol eder. Üçüncü kez, bu bağlantıda bir sorun oluşana kadar önceki paket sayısının iki katını ekler. Bu anda, verilerin uçtan uca veri iletimi için bu bağlantıyı sürdürmek, verici hızını artırmak ve doğruluğu korumak için gönderilen önceki paket sayısını geri alır. Bu süreci basit bir matematiksel formülle açıklayabiliriz: `2^(n)`. Burada n, paketin bu bağlantıda doğru şekilde gönderilme sayısıdır.

Sonuç olarak, veri iletmesi gereken üst düzey protokollerin tümü TCP Protokolünü kullanır. Örnekler, Dosya Aktarım Protokolü (FTP), Güvenli Kabuk (SSH) gibi eşler arası paylaşım yöntemlerini içerir...

<div align="right">
  <b><a href="#top">↥ back to top</a></b>
</div>

### IP Address

   <br>
      <p align="center">
         <img src="https://github.com/K-zew/Netpractice/blob/main/Imgs/IP_addressing.jpeg?raw=true" alt="IP">
      </p>
   </br>

IP, iletim kontrol protokolünü de içeren bir internet protokol paketinin parçasıdır. Birlikte, bu ikisi TCP/IP olarak bilinir. İnternet protokol paketi, ağlar üzerinden veri paketleme, adresleme, iletme, yönlendirme ve alma kurallarını yönetir.

IP adresleme, bir ağdaki cihazlara adres atamanın mantıksal bir yoludur. İnternete bağlı her cihaz benzersiz bir IP adresi gerektirir.

Bir IP adresinin iki bölümü vardır; bir kısım bilgisayar veya başka bir cihaz gibi ana bilgisayarı tanımlar ve diğer kısım ait olduğu ağı tanımlar. TCP/IP, bunları ayırmak için bir [alt ağ maskesi](#alt ağ maskesi) kullanır.

<div align="right">
  <b><a href="#top">↥ back to top</a></b>
</div>

### TCP/IP modeli

   <br>
      <img src="https://github.com/K-zew/Netpractice/blob/main/Imgs/tcp_ip_model.png?raw=true" alt="tcp_ip_model">
   </br>
   
   * Explained :
   
   <br>
      <img src="https://github.com/K-zew/Netpractice/blob/main/Imgs/tcp_ip.png?raw=true" alt="tcp_ip">
   </br>

<div align="right">
  <b><a href="#top">↥ back to top</a></b>
</div>

### IPv4 vs IPv6

IP addresses come in 2 versions--IPv4 and IPv6:

   <br>
      <img src="https://github.com/K-zew/Netpractice/blob/main/Imgs/IPv4-vs-IPv6-FR.png?raw=true" alt="IPv4 vs IPv6">
   </br>

İnternet Protokolü sürüm 4 (IPv4), bir IP adresini 32 bitlik bir sayı olarak tanımlar. Ancak, İnternet'in büyümesi ve mevcut IPv4 adreslerinin tükenmesi nedeniyle, IP adresi için 128 bit kullanan yeni bir IP sürümü (IPv6) 1998'de standartlaştırıldı. Ancak, NetPractice'te yalnızca IPv4 adresleri kullanılıyor.


- Genel Adres ve Özel Adres
Genel IP adresi, doğrudan internet üzerinden erişilebilen ve internet servis sağlayıcınız (İSS) tarafından ağ yönlendiricinize atanan bir IP adresidir. Genel (veya harici) bir IP adresi, internete ağınızın içinden ağınızın dışına bağlanmanıza yardımcı olur.

Özel bir IP adresi, ağ yönlendiricinizin cihazınıza atadığı adrestir. Aynı ağ içindeki her cihaza benzersiz bir özel IP adresi atanır (bazen özel ağ adresi olarak adlandırılır) — bu, aynı dahili ağdaki cihazların birbirleriyle bu şekilde konuşmasıdır.

Bir ağ internete bağlandığında, ayrılmış özel IP adreslerinden bir IP adresi kullanamaz. Aşağıdaki aralıklar özel IP adresleri için ayrılmıştır:

```
192.168.0.0 – 192.168.255.255 (65,536 IP addresses)
172.16.0.0 – 172.31.255.255   (1,048,576 IP addresses)
10.0.0.0 – 10.255.255.255     (16,777,216 IP addresses)
```
<div align="right">
  <b><a href="#top">↥ back to top</a></b>
</div>

# Subnet Mask

   <br>
      <p align="center">
         <img src="https://github.com/K-zew/Netpractice/blob/main/Imgs/subent_mask.png?raw=true" alt="subnet mask">
      </p>   
   </br>

Alt ağ maskesi, IP adresindeki bir ağ adresi ile bir ana bilgisayar adresini ayırt etmek için kullanılan 32 bitlik (4 bayt) bir adrestir. Bir ağ veya alt ağ içinde kullanılabilecek IP adresleri aralığını tanımlar.

- Ağ adresini bulma
Yukarıdaki Arayüz A1 aşağıdaki özelliklere sahiptir:
```
IP address | 104.198.241.125
Mask       | 255.255.255.128  
```
IP adresinin hangi kısmının ağ adresi olduğunu belirlemek için, maskeyi IP adresine uygulamamız gerekir. Önce maskeyi ikili biçimine dönüştürelim:
```
Mask | 11111111.11111111.11111111.10000000
```
Bir maskenin 1 olan bitleri ağ adresini temsil ederken, bir maskenin 0 olan kalan bitleri ana bilgisayar adresini temsil eder. Şimdi IP adresini ikili forma dönüştürelim:
```
IP address | 01101000.11000110.11110001.01111101
Mask       | 11111111.11111111.11111111.10000000
```
Artık IP'nin ağ adresini bulmak için maskeyi bitsel AND aracılığıyla IP adresine uygulayabiliriz:
```
Network address | 01101000.11000110.11110001.00000000
```
Hangi bir ağ adresine çevirir `104.198.241.0`.


- Ana bilgisayar adreslerinin aralığını bulma
Ağımız üzerinde hangi host adreslerini kullanabileceğimizi belirlemek için, IP adresimizin host adresine ayrılmış bitlerini kullanmamız gerekir. Önceki IP adresimizi ve maskemizi kullanalım:

```
IP address | 01101000.11000110.11110001.01111101
Mask       | 11111111.11111111.11111111.10000000
```
Ana bilgisayar adreslerimizin olası aralığı, tümü 0 olan maskenin son 7 bitiyle ifade edilir. Bu nedenle, ana bilgisayar adreslerinin aralığı:
```
BINARY  | 0000000 - 1111111
DECIMAL | 0 - 127
```
Ağımız için olası IP adresleri aralığını elde etmek için, ana bilgisayar adresi aralığını ağ adresine ekleriz. Olası IP adresleri yelpazemiz şu hale gelir: `104.198.241.0 - 104.198.241.127`.

ANCAK, aralığın uç noktaları belirli kullanımlar için ayrılmıştır ve bir arayüze verilemez:
```
104.198.241.0   | Ağ adresini temsil etmek için ayrılmıştır.
104.198.241.127 | Yayın adresi olarak ayrılmıştır; Bir ağın tüm ana bilgisayarlarına paket göndermek için kullanılır.
```
Therefore, our real IP range becomes `104.198.241.1 - 104.198.241.126`, which could have been found using an IP calculator.

* CIDR Gösterimi (/24)
Maske, Sınıfsız Etki Alanları Arası Yönlendirme (CIDR) ile de temsil edilebilir. Bu form, maskeyi bir eğik çizgi "/" olarak temsil eder ve ardından ağ adresi olarak hizmet veren bit sayısı gelir.

Bu nedenle, yukarıdaki "255.255.255.128" örneğindeki maske, 32 bitin 25 biti ağ adresini temsil ettiğinden, CIDR notasyonu kullanılarak /25 maskesine eşdeğerdir.

<div align="right">
  <b><a href="#top">↥ back to top</a></b>
</div>

### Switch

   <br>
      <p align="left">
         <img src="https://github.com/K-zew/Netpractice/blob/main/Imgs/switch real.webp?raw=true" alt="switch">
      </p>
      <p align="right">
         <img src="https://github.com/K-zew/Netpractice/blob/main/Imgs/switch.webp?raw=true" alt="switch">
      </p>
   <br>

Anahtar, birden çok cihazı tek bir ağda birbirine bağlar. Bir yönlendiriciden farklı olarak, anahtarın herhangi bir arabirimi yoktur, çünkü paketleri yalnızca yerel ağına dağıtır ve kendi dışındaki bir ağla doğrudan konuşamaz.

<div align="right">
  <b><a href="#top">↥ back to top</a></b>
</div>

### Router

   <br>
      <p align="left">
         <img src="https://github.com/K-zew/Netpractice/blob/main/Imgs/router.jpg?raw=true" alt="router">
      </p>
   <br>

Anahtarın birden çok cihazı tek bir ağ üzerinde birbirine bağlaması gibi, yönlendirici de birden çok ağı birbirine bağlar. Yönlendiricinin bağlandığı her ağ için bir arabirimi vardır.

Yönlendirici farklı ağları ayırdığından, arabirimlerinden birindeki olası IP adresleri aralığı, diğer arabirimlerinin aralığıyla örtüşmemelidir. IP adresi aralığındaki bir çakışma, arayüzlerin aynı ağ üzerinde olduğu anlamına gelir.
 <br>
      <p align="right">
         <img src="https://github.com/K-zew/Netpractice/blob/main/Imgs/router.png?raw=true" alt="router">
      </p>
</br>

<div align="right">
  <b><a href="#top">↥ back to top</a></b>
</div>

### Routing Table

   <br>
   <img src="https://github.com/K-zew/Netpractice/blob/main/Imgs/routing_table.png?raw=true" alt="routing_table">
   <br>
   
Yönlendirme tablosu, belirli ağ hedeflerine giden yolları listeleyen bir yönlendiricide veya ağ ana bilgisayarında depolanan bir veri tablosudur. NetPractice'te yönlendirme tablosu 2 öğeden oluşur:

Hedef: Hedef, bir ana bilgisayarın paketlerin son hedefi olduğu bir ağ adresini belirtir. Varsayılan yol veya 0.0.0.0/0, bir IP hedef adresi için başka yol olmadığında etkili olan yoldur. Varsayılan rota, paketleri belirli bir hedef vermeden yollarına göndermek için sonraki sekme adresini kullanacaktır. Varsayılan rota herhangi bir ağla eşleşir.

Sonraki atlama: Sonraki atlama, bir paketin geçebileceği bir sonraki en yakın yönlendiriciyi ifade eder. Paketin yolundaki bir sonraki yönlendiricinin IP adresidir. Her bir yönlendirici, yönlendirme tablosunu bir sonraki atlama adresiyle korur.

<div align="right">
  <b><a href="#top">↥ back to top</a></b>
</div>

## Levels

<details>
 <summary>Level 1</summary>
   <br>
   <img src="https://github.com/K-zew/Netpractice/blob/main/level1/level1.png?raw=true" alt="level1">
   <br>
   <br>
   
   **A1 arayüzü.** *İstemci A* ve *İstemci B* aynı ağda olduğundan, alt ağ maskesine göre IP adresleri aynı ağı temsil etmelidir.
<br>
Alt ağ maskesi "255.255.255.0" şeklindedir; bu, IP adresinin ilk 3 baytının ağı ve 4. baytın ana bilgisayarı temsil ettiği anlamına gelir. Aynı ağda olduğumuz için sadece host değişebilir.
<br>
Çözüm, aşağıdaki 3 hariç **104.96.23.0 - 104.96.23.255** aralığında herhangi bir şey olacaktır:
* **104.96.23.0:** Ana bilgisayar aralığındaki ilk sayı (bu durumda 0) ağı temsil eder ve bir ana bilgisayar tarafından kullanılamaz.
* **104.96.23.255:** Ana bilgisayar aralığındaki son sayı (bu durumda 255), yayın adresini temsil eder.
* **104.96.23.12:** Bu adres, *İstemci B* ana bilgisayarı tarafından zaten kullanılıyor.

**D1 arayüzü.** *1.* ile aynı mantık, ancak bu durumda alt ağ maskesi *255.255.0.0*'dır. IP adresinin ilk 2 baytı ağı temsil edecektir; ve son 2 bayt, ana bilgisayar adresi.
<br>
Çözüm, aşağıdakiler hariç **211.191.0.0 - 211.191.255.255** aralığında herhangi bir şey olacaktır:
* **211.191.0.0:** Ağ adresini temsil eder.
* **211.191.255.255:** Yayın adresini temsil eder.
* **211.191.89.75:** Host *Client C* tarafından zaten alınmıştır.
   
  <div align="right">
   <b><a href="#top">↥ back to top</a></b>
</div>
</br>
</details>

---

<details>
 <summary>Level 2</summary>
   <br>
   <img src="https://github.com/K-zew/Netpractice/blob/main/level2/level2.png?raw=true" alt="level2">
   <br>
   <br>
   
  **Arayüz B1.** *İstemci B*, *İstemci A* ile aynı özel ağda olduğundan, tam olarak aynı alt ağ maskesine sahip olmalıdır.
<br>
Çözüm yalnızca `255.255.255.224` olabilir.

**Arayüz A1.** "255.255.255.224" alt ağ maskesini anlamak için, buna *İstemci B*:'nin "192.168.56.222" IP'si ile birlikte ikili biçimde bakalım.

<center>

```
MASK: 11111111.11111111.11111111.11100000
IP:   11000110.00010000.00111000.11011110
```
</center>
Gördüğümüz gibi ilk 27 bit IP adresini temsil ederken sadece son 5 bit host adresini temsil ediyor.
<br>
Ağı temsil eden bu 27 bitin tümü, aynı ağdaki ana bilgisayarların IP adreslerinde aynı kalmalıdır. Cevabı almak için sadece sonuncuyu değiştirebiliriz (5 bit = 32 | 32-2 = 30).
<br>
<br>
Cevap şu aralıktadır:

```
BIN:  11000000.10101000.00111000.11000000 - 11000000.10101000.00111000.11011111
or
DEC:  192.168.56.192 - 192.168.56.223
```
çünkü "192.168.56.222" aralığındadır.

Hariç:
<br>
* **11000000.10101000.00111000.11000000:** Ağ adresini temsil eder (son 5 bitteki tüm 0'lara dikkat edin).
* **11000000.10101000.00111000.11011111:** Yayın adresini temsil eder (son 5 bitteki 1'e dikkat edin).
* **11000000.10101000.00111000.11011110:** *Müşteri B* bu adrese zaten sahip.

**D1/C1 arabirimi.** Burada *D1 arabiriminde* alt ağ maskesi için eğik çizgi "/" gösterimi ile tanışıyoruz. */30* alt ağ maskesi, IP adresinin ilk 30 bitinin ağ adresini ve kalan 2 bitin ana bilgisayar adresini temsil ettiği anlamına gelir:
<center>

```
Mask /30: 11111111.11111111.11111111.11111100
```
</center>

Bu ikili sayının '255.255.255.252' ondalık basamağına karşılık geldiğini görebiliriz, dolayısıyla *Arayüz C1*'de bulunan maske ile aynıdır.
<br>
<br>
Yanıtlar, aşağıdaki koşulları karşıladıkları sürece herhangi bir adres olabilir:
* Ağ adresi (ilk 30 bit) *Client D* ve *Client C* için aynı olmalıdır.
* Ana bilgisayar bitlerinin (son 2 bit) tümü 1 veya tümü 0 olamaz.
* *Client D* ve *Client C* aynı IP adreslerine sahip değildir.
   
```
like 1.1.0.1 and 1.1.0.2
 or  1.1.0.253 and 1.1.0.254 ..... 
```
  <div align="right">
   <b><a href="#top">↥ başa dönüş</a></b>
</div>
</br>
</details>

---

<details>
 <summary>Level 3</summary>
   <br>
   <img src="https://github.com/K-zew/Netpractice/blob/main/level3/level3.png?raw=true" alt="level3">
   <br>
   <br>
   
   
Bu alıştırma **anahtarın** (bu örnekte *Anahtar S*) kullanımını tanıtır. Anahtar, aynı ağın birden çok ana bilgisayarını birbirine bağlar.
   <br>
   <br>

  *İstemci A*, *İstemci B* ve *İstemci C* aynı ağ üzerindedir. Bu nedenle, hepsinin aynı alt ağ maskesine sahip olması gerekir. *Client C* zaten *255.255.255.128* maskesine sahip olduğundan, *Arayüz B1* ve *Arayüz A1* için maske de "255.255.255.128" (veya eğik çizgi gösterimiyle: "/25") olacaktır.
   <br>
   <br>
   *Arayüz B1* ve *Arayüz C1*'in IP adresi, *İstemci A*'nın IP'si ile aynı ağ aralığında olmalıdır. Bu aralık:
   <merkez>

   ```
   104.198.52.0 - 104.198.52.128
   aralıktaki Arayüz 104.198.52.125 nedeniyle.
   ```
   </orta>
   Elbette ağ adresi ve yayın adresi hariç.

   
   <div hizalama="sağ">
    <b><a href="#top">↥ başa dön</a></b>
</div>
</br>
</detaylar>

---

<ayrıntılar>
  <summary>4. Düzey</summary>
    <br>
    <img src="https://github.com/K-zew/Netpractice/blob/main/level4/level4.png?raw=true" alt="level4">
    <br>
    <br>
   
   Bu alıştırma **yönlendiriciyi** tanıtır. Yönlendirici, birden çok ağı birbirine bağlamak için kullanılır. Bunu birden çok arabirim (bu örnekte *Arayüz R1*, *Arayüz R2* ve *Arayüz R3*) kullanarak yapar.
   <br>
   <br>

    *Interface B1*, *Interface A1* ve *Interface R1* üzerindeki maskelerin hiçbiri girilmediğinden, kendi alt ağ maskemizi seçmekte özgürüz. **/24** maskesi, bize ana bilgisayar adresi için 8. baytın tamamını bıraktığı ve olası ana bilgisayar adresleri aralığını bulmak için ikili hesaplamalar gerektirmediği için idealdir.
   <br>
   <br>
   *Arayüz B1* ve *Arayüz R1* IP adresi, *Arayüz A1* IP adresi ile aynı ağ adresine sahip olmalıdır. */24* alt ağıyla olası aralık:
   <merkez>

   ```
   85.17.5.0 - 85.17.5.255
   ```
   </orta>
   Ağ adresi ve yayın adresi hariç.
   <br>
   <br>

   İletişimimizin hiçbirinin yönlendiricinin bu taraflarına ulaşması gerekmediğinden, yönlendirici *Arayüz R2* ve *Arayüz R3* ile etkileşime girmediğimizi unutmayın.
  <div align="right">
   <b><a href="#top">↥ back to top</a></b>
</div>
</br>
</details>

---

<details>
 <summary>Level 5</summary>
   <br>
   <img src="https://github.com/K-zew/Netpractice/blob/main/level5/level5.png?raw=true" alt="level5">
   <br>
   <br>
   
Bu seviye **rotaları** tanıtır. Bir rota 2 alan içerir, ilki giden paketlerin **hedefi**, ikincisi ise paketlerin **sonraki sekmesi**'dir.
   **hedef** "varsayılan", "0.0.0.0/0" ile eşdeğerdir ve bu, paketleri ayrım gözetmeksizin karşılaştığı ilk ağ adresine gönderir
   **sonraki atlama**, geçerli makinenin arabiriminin paketlerini göndermesi gereken bir sonraki yönlendirici (veya internet) arabiriminin IP adresidir.

     *İstemci A*'nın paketlerini gönderebileceği yalnızca 1 yolu vardır. Numaralandırılmış bir varış yeri belirtmenin bir faydası yoktur. *varsayılan* hedef, paketleri mevcut tek yola gönderir.
   <br>
   <br>
   Bir sonraki atlama adresi, paketlerin yolundaki bir sonraki yönlendirici arayüzünün IP adresi olmalıdır. Bir sonraki arabirim, "71.199.10.126" IP adresine sahip *Arayüz R1*'dir. Bir sonraki arayüzün *Arayüz A1* olmadığına dikkat edin, çünkü bu gönderenin kendi arayüzüdür.
   
   *Müşteri B* paketlerini gönderebileceği yalnızca 1 yola sahiptir. Numaralandırılmış bir varış yeri belirtmenin bir faydası yoktur. *varsayılan* hedef, paketleri mevcut tek yola gönderir.
   <br>
   <br>
   Bir sonraki atlama adresi, paketlerin yolundaki bir sonraki yönlendirici arayüzünün IP adresi olmalıdır. Bir sonraki arabirim, "133.185.132.254" IP adresine sahip *Arayüz R2*'dir. Bir sonraki arayüzün *Arayüz A1* olmadığına dikkat edin, çünkü bu gönderenin kendi arayüzüdür.
   
  <div align="right">
   <b><a href="#top">↥ back to top</a></b>
</div>
</br>
</details>

---

<details>
 <summary>Level 6</summary>
   <br>
   <img src="https://github.com/K-zew/Netpractice/blob/main/level6/level6.png?raw=true" alt="level6">
   <br>
   <br>
Bu seviye **interneti** tanıtır. İnternet bir yönlendirici gibi davranır. Ancak, bir arabirim doğrudan veya dolaylı olarak internete bağlıysa, aşağıdaki ayrılmış özel IP aralıklarında bir IP adresine sahip olamaz**:


   ```
   192.168.0.0 - 192.168.255.255 (65.536 IP adresi)
   172.16.0.0 - 172.31.255.255 (1.048.576 IP adresi)
   10.0.0.0 - 10.255.255.255 (16.777.216 IP adresi)
   ```
   **İnternet.** İnternetin **sonraki sekmesi** zaten girilmiştir ve *Interface R2*'nin IP adresiyle eşleşir. Bu nedenle, sadece internetin hedefi ile uğraşmamız gerekiyor.
   <br>
   <br>
   İnternet, paketlerini *İstemci A'ya göndermelidir. Bunu yapmak için, internetin hedefi *Müşteri A*'nın ağ adresiyle eşleşmelidir. *Client A*:'nın ağ adresini bulalım:
   <br>
   *İstemci A*'nın maskesi, "/25" ile eşdeğer olan "255.255.255.128" şeklindedir. Bu, IP adresinin ilk 25 bitinin ağ adresi olduğu anlamına gelir. IP adresinin ilk 3 baytının (24 bit) ağ adresinin bir parçası olduğunu biliyoruz:
   <merkez>
  227 sayısını ikiliye çevirirsek ``11100011`` elde ederiz. 25. bit'e karşılık gelen ilk hane 1'dir. Yalnızca 25. bit ağ adresinin bir parçası olduğu ve kalan 7 bit olmadığı için, ağ adresinin son baytı için ``10000000`` alırız. ondalık basamakta 128'dir.
   <br>
   <br>
   Tam ağ adresi:
   <merkez>

   ```
   104.124.215.128
   ```
   </orta>

   ``104.124.215.129 - 104.124.255`` aralığında veya ana bilgisayar adresleriyle.
   <br>
   <br>
   Artık bu '104.124.215.128' adresini İnternet hedefine koyabiliriz. Hedef adresinin ardından gelen "25", adresine uygulanan maskeyi temsil eder.
   <br>
   <br>
   "104.124.215.227/25" hedefi, *104.124.215.128/25* hedef adresine eşdeğerdir, çünkü */25* maskesi, hedefin ağ adresini almak için 25'ten sonraki tüm bitleri 0'a çevirecektir.

   ```
   104.124.215.?
   ```
   </orta>

   Şimdi sadece 25. bitin 1 mi yoksa 0 mı olduğunu bulmamız gerekiyor.
   <br>
   
  <div align="right">
   <b><a href="#top">↥ back to top</a></b>
</div>
</br>
</details>

---

<details>
 <summary>Level 7</summary>
   <br>
   <img src="https://github.com/K-zew/Netpractice/blob/main/level7/level7.png?raw=true" alt="level7">
   <br>
   <br>
   
Bu seviye **örtüşme** kavramını tanıtır. Bir ağın IP adresi aralığı, ayrı bir ağın IP adresi aralığıyla örtüşmemelidir. Ağlar yönlendiricilerle ayrılır.
   <br>
   <br>

  3 ayrı ağımız var:
   <br>

   1. *İstemci A* ile *Yönlendirici R1* arasında (Arayüz R11).
   2. *Yönlendirici R1* (Arayüz R12) ve *Yönlendirici R2* (Arayüz R21) arasında.
   3. *Yönlendirici R2* (R22 Arayüzü) ve *Client C* arasında.

   *Interface A1* için, *Interface R11* IP'si zaten girilmiş olduğundan IP adresimizi serbestçe seçemiyoruz. Ayrıca */24* şeklinde bir maske verirsek, IP adres aralığı önceden girilmiş olan *Interface R12* aralığı ile çakışacaktır. Her ikisi de ``90.198.14.0 - 90.198.14.255`` aralığında olacaktır.
   <br>
   <br>
   3 ayrı ağ için adreslere ihtiyacımız olduğundan, adresin son baytlarını 4 veya daha fazla adres aralığına bölmek uygundur. Bunu `/26` maskesini veya daha üstünü kullanarak yapıyoruz. Örneğin */28* maskesi bize 16 aralık verecek ve bunlardan aşağıdaki 3'ü kullanacağız:
   ```
   90.198.14.1 - 90.198.14.14 (İstemci A'dan Yönlendirici R1'e)
   90.198.14.65 - 90.198.14.78 (Yönlendirici R1'den Yönlendirici R2'ye)
   90.198.14.241 - 90.198.14.254 (Yönlendirici R2'den İstemci C'ye)
   ```

   Bir maskenin olası aralıklarını hesaplamak için:
  <br>
  [https://www.calculator.net/bandwidth-calculator.html](https://www.calculator.net/ip-subnet-calculator.html?c6subnet=64&c6ip=2001%3Adb8%3A85a3%3A%3A8a2e%3A370%3A7334&ctype=ipv6&printit=0&x=69&y=28#ipv6)
   
  <div align="right">
   <b><a href="#top">↥ back to top</a></b>
</div>
</br>
</details>

---

<details>
 <summary>Level 8</summary>
   <br>
   <img src="https://github.com/K-zew/Netpractice/blob/main/level8/level8.png?raw=true" alt="level8">
   <br>
   <br>
   
   
**İnternet.** *Client C* ve *Client D* ana bilgisayarları paketleri internete gönderir, ardından internet, paketleri ilk gönderene kadar geri göndererek yanıt verir. İnternet, bu paketleri göndermek için *139.84.118.0/26* hedefini kullanarak paketleri ``139.84.118.17.1 - 139.84.118.17.63`` aralığındaki ağlara gönderir.
   <br>
   <br>
   Tüm alıcı ağlar birbiriyle örtüşmeden bu aralıkta olmalıdır.
   <br>
   <br>

   **Yönlendirici R2.** *Arayüz R23* ve *Arayüz R22*'de */26* aralığını hedef adresinden uygun şekilde bölmek için '255.255.255.240' (veya */28*) maskesini kullanırız. 4 ayrı aralık. 4'ün bu şekilde ayrılması gereklidir, çünkü aşağıdaki 3 ağın birbiriyle örtüşmemesi gerekir:
   <br>

   1. *Yönlendirici R1* (yönlendirici R13) - *Yönlendirici R2* (yönlendirici R21).
   2. *Yönlendirici R2* (yönlendirici R22)'den *İstemci C'ye*.
   3. *Yönlendirici R2* (yönlendirici R23)'den *İstemci D'ye*.

   Bu ağların her biri daha sonra */28*: maskesiyle aşağıdaki IP aralığından birine atanabilir.
   ```
   139.84.118.0 - 139.84.118.15
   139.84.118.16 - 139.84.118.31
   139.84.118.32 - 139.84.118.47
   139.84.118.48 - 139.84.118.63
   ```
   Ağ adresinin (ilk) ve yayın adresinin (son) her aralıktan çıkarılması gerektiğini unutmayın.
   <br>
   <br>

**Yönlendirici R1** İnternet için hedef ve bir sonraki atlama zaten girilmiştir. *Router R2* için yalnızca bir sonraki sekmeye, yani *Interface R21* üzerindeki IP'ye girmemiz gerekiyor.
   ```
   139.84.118.61
   ```
   
  <div align="right">
   <b><a href="#top">↥ back to top</a></b>
</div>
</br>
</details>

---

<details>
 <summary>Level 9</summary>
   <br>
   <img src="https://github.com/K-zew/Netpractice/blob/main/level9/level9.png?raw=true" alt="level9">
   <br>
   <br>
   
İnternet başlangıçta paketlerini belirli bir ağa göndermediğinden, bu seviye oldukça basittir. Bu nedenle, ayrı ağların ortak bir adres aralığını paylaşması gerekmez. Seviye tamamlanana kadar seviyenin 6 hedefini tek tek takip etmenizi öneririm.
   <br>
   <br>
   Ayrılmış özel IP aralıklarından ağ adreslerini kullanmamayı unutmayın.
   <br>
   <br>

   **1** **Hedef 3**, *meson*'u *internete* bağlamamız gerektiğini belirtir. *İnternetin* *meson*'a yanıt vermesi gerekecek, bu yüzden *internetin* hedefine *meson'un* ağ adresini gireceğiz.
   <br>
   <br>
   **Hedef 6**, *cation*'ı *internete* bağlamamız gerektiğini belirtir, bu nedenle *internetin* hedefine *cation'ın* ağ adresini gireriz.
   <br>
   <br>
   *İnternetin* 3. hedefi için ve *Router R1'in* hedefinde boş bir alanın olması normaldir. Yönlendirme tablolarının tüm alanlarının doldurulması gerekmez.]
   
  <div align="right">
   <b><a href="#top">↥ back to top</a></b>
</div>
</br>
</details>

---

<details>
 <summary>Level 10</summary>
   <br>
   <img src="https://github.com/K-zew/Netpractice/blob/main/level10/level10.png?raw=true" alt="level10">
   <br>
   <br>
   In this level, there are 4 different networks:
  <br>
1. *Yönlendirici R1* (yönlendirici R11) *S1 Anahtarına*
   2. *Yönlendirici R1* (yönlendirici R13) - *Yönlendirici R2* (yönlendirici R21)
   3. *Yönlendirici R2* (yönlendirici R23) - *İstemci H4*
   4. *Yönlendirici R2* (yönlendirici R22)'den *İstemci H3'e*
   <br>

   **İnternet.** İnternet, paketlerini tüm ana bilgisayarlara gönderebilmelidir, bu nedenle hedefi tüm ana bilgisayarların ağ aralığını kapsamalıdır.
   <br>
   <br>
   *Arayüz R11* ve *Arayüz R13* halihazırda girilmiş bir IP adresine sahiptir. Bu IP adresi yalnızca son baytında farklılık gösterir. *Arayüz R11* son bayt **1**'e sahiptir ve *Arayüz R13* son bayt **254**'e sahiptir. Bu geniş IP adres aralığını kapsamak için *internetin* hedefi için **/24** maskesini alıyoruz. Bu hedef, ``170.235.26.0 - 170.235.26.255`` aralığını kapsayacaktır.
   <br>
   <br>

   **Önemli.** IP adreslerini seçerken 2 şeyden emin olmalıyız:
   <br>

   1. IP adresi *internet* hedefi kapsamındadır.
   2. Çeşitli ağların IP adresi aralığı çakışmaz.
   <br>
  
   IP adresleri zaten girilmişken (grileştirilmiş), çeşitli ağların kapsadığı aralıkları inceleyelim:
   <br>

   1. *Yönlendirici R1* (yönlendirici R11) - *Anahtar S1* - ``170.235.26.0 - 170.235.26.127`` (maske /25) aralığını kapsar.
   2. *Yönlendirici R2* (yönlendirici R23) - *İstemci H4* - ``170.235.26.128 - 170.235.26.191`` (maske /26) aralığını kapsar.
   3. *Yönlendirici R1* (yönlendirici R13) - *Yönlendirici R2* (yönlendirici R21) - ``170.235.26.252 - 170.235.26.255`` (maske /30) aralığını kapsar.
   4. *Yönlendirici R2* (yönlendirici R22) - *İstemci H3* - ??? (maske ???).

   "Yönlendirici R2'den İstemci H3'e" ağı için geriye kalan tek IP adresi ``170.235.26.192 - 170.235.26.251``dir. *Interface R22* ve *Interface R31* içine koymak için bu aralıktan 2 IP adresi almamıza izin verecek herhangi bir maskeyi seçebiliriz.

   
  <div align="right">
   <b><a href="#top">↥ geri dön</a></b>
</div>
</br>
</details>


