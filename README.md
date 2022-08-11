# Mikrodenetleyici-Uygulamalari-

Ders 1 (28.06.2021)
---
Mikrodenetleyici nedir?
---
- Aslında bir bilgisayar sistemini oluşturan elemanlardan bir tanesidir.
- En basit tanımı "Single chip Computer" (Tek bir çipten oluşan bilgisayar)
- Bilgisayar sistemini oluşturan bir çok birim bir araya getirilip tek bir çipte toplanmış hali. Tek çipte toplanmasaydı gerektiğinde ona ek ilaveler yapabilirdik. 
- Çok düşük güöçlerde çalışırlar.

>> Belli bir göreve adanmıştır fakat birden fazla alt görev işleyebilirler, >> Bunlar kendilerine yüklenen sabit bir programı çalıştırıyorlar. (Kalıcı bellekteki)

- Mikrodenetleyici aslında bir bilgisayar sistemidir fakat tek çipten oluşur. Bir bilgisayar sistemini oluşturmak için ise mikrodenetleyicinin çekirdek kısmına, çevresel birimlere ve bellek kısmına ihtiyaç vardır.

 Arm çekirdeği nedir?
 ---
 Mİkrodenetleyicinin belirli bir kısmı.
 ST firması mikrodenetleyici üretmek için ARM ile anlaşıyor ve ARM mikrodenetleyicinin temel birimlerini içeren çekirdek kısımlarının tasarımlarını satıyor. ST firması ürettiği çevresel birimleri ekleyerek bunları ARM çekirdeğine bağlıyor. 

Cortex M ->  m = Microcontroller 
Cortex = Beyin zarı

Örneğin: Arm firması beynini üretiyor ve st firması da organları üretiyor gibi. Bu şekilde mikroişlemci bütün haline getiriyor.

- Flaş memoryler kalıcı belleklerdir. İçindeki programlar silinmiyor. (Aslında siliniyor ama çok uzun süre 200 yıl gibi)
- Yazma zamanları yavaş, okuma zamanalrı hızlıdır.

- Arm çekirdek kısmının üretimini yapmıyor, sadece data dosyalarını veriyor. Üretim de firmalar tarafından yapılıyor. Arm, mimarisini satıyor.
- CPU ve core aynı şey mi? Aslında cpu işlemcinin merkezi işlem birimi. Bilgisayar sisteminde core kısmı cpu kısmı oluyor diyebiliriz.

![image](https://user-images.githubusercontent.com/75746171/170818784-4e258129-1130-4f20-bd55-5020ce90ee5a.png)

- Çekirdeğe dahil olan kısım sol üstteki kısım ve veri yollarıdır. 
- Birden fazla yol olmasının sebebi aynı yolun aynı anda kllanılamaması.
- Eğer tek bir yol olsaydı işlemci komutu çalıştırmak için program memoryden çekerken aynı zamanda başka bir çevresel birim ile iş yapamazdı.
- Flash belleğin yazma sınırı 10bin ise, hep aynı bellek gözlerine yazdıldığında o bellek bir daha yazılama duruma gelebilir. 
- Flash disk sadece device olarak çalışır, flash diski l-kullanabilmek için mikroişlemci tarafından host gerekir. Flash diski pc'nin us portuna bağlayarak kullanabilirim fakat stm32f103'ün usb portuna bağlayarak çalıştıramam çünkü onu host olarak çalıştırma şansım yok. (Uygun bir işlemcide mümkün olabilir)
- 


Not:
---
![image](https://user-images.githubusercontent.com/75746171/142284261-591e643f-fd83-41af-9f89-f0e5cb61c054.png)

- Buradaki dhrystone bir benchmark testi. İşlemcileri değişik testlere sokarak performanslara göre işlemcileri karşılaştılılıyor ve performans değeri veriyorlar. Saniyedeki milyon işlem sayısı.
- İşklemciyi 10 MHz de çalıştırırsam 12.5 DMIPS işlem günüden olacak. max çalıştırırsam 75x1.25 olacak.
- Bu işlemcilerin işlem gücünü karşılaştırmak için kullanılıyor.
- Single cycle özellik ise tek cycle da çarpma ve bölme ypaabilme özelliği. Bu verimli çalıştırğını gösterir.
- SRAM, Static ram. Yazılı silinir bellk.  
- Flash hafıza, EEPROM'un gelişmiş versiyonu gibi.
- İşlemcinin çalışma frekansı, işlemcinin işlem yapma gücüyle doğrudan orantılı.
- 
Static ram ve dynamic ram
---
- DRAM yapısal olarak daha basit bir bellek türü.
- İkisi de yazılır silinir bellek.
- SRAM daha hızlıdır. ve daha pahalıdır, transistör sayısı daha fazladır. 
- SRam daha çok hızlı çalışması gereken birimlerde tervcih ediliyor. Güç harcaması daha düşük.
- Hızın önemli olduğu fakat bellek miktarının önmemli olmadoığı irimlerde tercih ediliyor.
- 


![image](https://user-images.githubusercontent.com/75746171/142285172-ef1a3c48-7251-4795-b95b-6526f5e94c47.png)

- Düşük voltajlar da bir avantaj.
- Power on reset ve Power down reset. Gerilim düştüğünde işlemcinin stabil kalanbilmesi için özel reset devreleri.
- POR işlemcinin düzgün çalışmaya başlaması için gerekiyor.
- PDR ise gerilim düştüğünde stabil kalmasını sağlar. 2 volt altına düştüğünde reset ediyor ve normal seviyeye çıkınca tekrar çalıştırmaya başlıyor.
- Internal RC osilatörü ile çalışmaya başlıyor sonra kristal osilatör 72 MHZ'e pll devresi ile getiriliyor. Bu internal osilatör startup ta kullanılıyor.
- İşlemcinin saat işaretininüretildiği yerin tasarlandığı kısım st tarafından tasarlanıyor.
- Arm işlemcileri çalışmaya başlarlken kendi içlerindeki rc osilatörden başlıyor.
- Yazılımsal olarak kristal osilatör ve pll devresiyle yükseltilebiliyor.
- Kristallerdeki ppm değeri, kristalin 1 milyon pulse da kaç pulse hata yaptığını gösteriyor.
- TCXO osilator sistemleri, değişen sıcaklığa göre ayrı bir mikrodenetleyici ile kristalin frekansına müdahale ddiyor.
- PLL: Stabil bir frekansın tam katında bir stabil çıkış elde etmek içinç kullanılıyor.

- Mesela kristal ösilatör 72 mhz ile çalışmıyor. Kristal osilatör stabil olarak çalıştılıp plls devres i ile çarpılarak hedef frekansa geçiliyor.

Dahili osilatör mü kararlı harici osilatör mü?
---
- Harici osiltör. Dahili osilatör RC osilatörüdür. Hata oranları çok daha yüksektir. RC osilatörlerin sıcaklığa karşı gösterdiği değişm de kristale göre daha yüksektir.

- Arm mikroişlemcilerin en öbnemli özelliği düşük güç harcamaları ve verimli çalışmaları bu yüzden mobilde arm lider durumda.

![image](https://user-images.githubusercontent.com/75746171/142287375-bd07a081-9970-4b9b-b1cf-1ec7cacfce61.png)

- Sleep modunda işlemcinin saati ve çevresel birimler çalışmaya decam eder. Fakat çekirdek çalışmayı durdurur. Komutları işlemez.
- Uzaktan kumanda gibi bastığımda çalışsın basmadığımda sleep modunda kalsın.
- Stop modu işlmeci duruyor fakat saat de duruyor. Bu modda hem çekirdek birimi hem de çevresel birimleri çalışmayı durdurur.
- Standby ise işlemciyi tamamen kapatmak. (Yazılımsal olarak işlemciyi durdurma)

- RTC devresi var. Real time clock. 

![image](https://user-images.githubusercontent.com/75746171/142289076-85025de4-65e4-4269-a022-1e53587ca5c6.png)

- SWD daha basit daha az uç var daha efektif.

- Timerlar bir sayaç registerları. 
- SysTick timer çekirdekten geliyor. Tüm arm işlemcilerinde var. Fakat diğer timerları ST firması eklemiş.

 ![image](https://user-images.githubusercontent.com/75746171/142450446-c7eb2960-3ac3-45b5-a360-85bd8cd82910.png)

8x16= 128 mb

- İlk 128 mb bölümü gerçekte var olan bir bellek değil. Flash memorynin bir kopyası da burada bulunuyor. Duruma göre başka bir alanı içeriyor. Yani burada bir memory yok başka bir adresteki değer burada da gözüküyor.
- Burası bir ynsıma bölgesi. Burayı okuması bot seçeneğine bağlı. Yani işlemcinin power on sırasında boot pinlerinin 0-1 konfigürasyonlarına göre burası hgaritalanıyor ve bu alanın nereyi temsil edeceğini belirliyor. Yani ben işlemcinin başlayacağı yeri belirliyorum fakat bnu direk o adresten başltatmıyorum, bu adresi 0 adresine kopyalayıp işlemciyi 0'dan başlatıyortum.
- Bunun amacı işlemcinin boot ettiği adres değişmesi fakat fiziksel olarak farklı yerden başlayabilsin diye düşünülmüş.

- Burada system memory, bootloader uygulamalarında kulla nılıyor. Farklı ir bellekten boot etmek için. Aslında işlemci her zaman 0'dan boot ediliyor. Ama öyle oluyor ki flash memory başlangıç bölgesine kopyalandığı için işlemci flash memoryden başlamış oluyor.

Ders 2
---

![image](https://user-images.githubusercontent.com/75746171/170874717-73450138-d70b-4e66-a277-405409776a1c.png)

- Register diyebilmemiz için işlemcinin çekirdek kısmıyla bağlantılı ve komut kümesi ile doğrudan işleme sokulabilen alanlar olması gerekir. (ARM mimarisi için)
- STM32 - 32 bit bellek adresleme yeteneği olan bir işlemci toplam kaç bellek gözü adresleyebilir?

![image](https://user-images.githubusercontent.com/75746171/170876134-cae74a6f-f5a3-40ff-bc88-0da3efc3648c.png)
![image](https://user-images.githubusercontent.com/75746171/170876155-9fcbe0f6-1598-449a-a194-487601e26f12.png)

- 10'luk sistemdeki her bir basamağı kaç bit ile ifade edebiliriz?

![image](https://user-images.githubusercontent.com/75746171/170878098-655bc0d3-556d-4894-8362-dca2c732b80e.png)

![image](https://user-images.githubusercontent.com/75746171/170879267-e9a41590-e7a0-46ee-88c7-42ca50712e3e.png)

- Reference manual
- stm32f1 ile başlayan işlemci ailesinin çinde yerr laan tüm çevresel irimlerin detaylı açıklaması var. (ADC nin nasıl kullanılacağı, registerlar, ayarlar)



Ders 3 (06.01.2022)
---

![image](https://user-images.githubusercontent.com/75746171/148369127-81e2c99f-a807-499a-9f47-e739267a1177.png)

Neden 32 bit değil de 8 bit genişlikte adresler?

İşlemci 32 bit işlem yapabilem yeteneğine sahip fakat yeri geldiğinde 8 veya 16 bitlik veriler de çekebilir. Eğer 32 olsaydı 8 bit kullanılacağı zaman gereksiz yere 32 bit geçecekti.

![image](https://user-images.githubusercontent.com/75746171/148371347-4e427bdb-0749-4f02-8079-8209fd46817c.png)

- İşlemcinin çevresel birimlerini kullanmak için biz aslında bu bellek bölgelerine erişiyoruz.
- Yani çevresel bşirimleri yönetme şeklimiz, çevresel bellek bölgesine erişerek buraya bazı değerler yazarak ve okuyarak gerçekleşiyor.
- 
![image](https://user-images.githubusercontent.com/75746171/170947299-567c1415-0ce4-4e31-bdfa-df52240544a9.png)
- İşlemcinin donanımını kontrol ederken aslında bu bölgelere yazıp okuma yapıyoruz.
- İşlemcinin kullanılan seri portuna (USART2) bellek gözüne yazılan bazı değerler ile ayarlamalar yaparız. 


![image](https://user-images.githubusercontent.com/75746171/148372041-dbfd131f-e956-42bd-abfa-c4acc40cfcf7.png)

- İçsel çevresel birimler. Çekirdeğin yönetimi ile ilgili bazı özellikler var. Örneğin NVIC bu bölgede.

![image](https://user-images.githubusercontent.com/75746171/148372384-d655940d-23f7-4284-b76e-37eee46e3033.png)

- Flash memory programın kodunu yani komutlarını bulunduran bölge. Okuma zamanları hızlı ve yazma zamanları yavaş. Enerji kesildiğnde değerlerini korurlar.
- İşlemcinin veri yolu her bölgeyi çalıştıracak şekilde tasarlanmamış. Mesela çevre birimlerinin olduğu adrese gidip oradaki kod yürütülemez, hata verir.
- 

![image](https://user-images.githubusercontent.com/75746171/148373463-0bd80b98-6b7c-47b5-ac27-39e8e3647f55.png)
  
- option bytes, Burada işlemcinin kalıcı konfigürasyonlarını yapacak bazı alanlar var. Program çalıştırmak amacı ile değil. 
- Çevresel birimlere çalışma zamanında veriler yazıyoruz fakat option byte kısmına programlama aşamasında veri yazıyoruz.
- System memory, 2 farklı programım varsa bunlardan istediğimi başlatmama yarayabilir.

![image](https://user-images.githubusercontent.com/75746171/148373731-f35e4f4e-105c-4eae-a29f-079c44e6c743.png)

- Bildiğimiz RAM. System memory. SRAM den kod çalıştırılabiliyor. Fakat oraya giden yol daha uzun bir yol, oradan çalışan kodlar daha yavaş çalışır.  Aslında işlemci flash memoryden kod çalıştırmaya optimize edilmiştir. 


![image](https://user-images.githubusercontent.com/75746171/148374813-ce0c78d0-452f-4235-9f04-8dfd77fcd96f.png)

-  VB pini. Backup batarya Pini. 3.3V verilecek.  Ana güç kaynağını kessek bile backup memoryde kalan bilgiler kalıcı oluyor. 

Register: İşlemcinin çekirdek bölgesinin doğrudan kullanabildiği, aritmetik lojik işlemlerde kullandığı bölgeler.

Stack pointer: İşlemcinin verileri stack memoryde saklayıp geri çekmek için kullandığı bellek bölgesi.  Local değişkenlerin tutulduğu alan. İşlemci alt programa girerken belli register depğerlerini saklama kzorunda. Last in first out şeklinde çalışır.

Link register: Alt programdan çıktıktan sonra eri dönebilşmek için.

Program counter: O anda çalışan programın hangi adreste olduğunu gösteriyor.

Clock tree
---

![image](https://user-images.githubusercontent.com/75746171/148378143-9b93ae40-8ecd-4ff7-ab4b-2b1f1a3e3843.png)

- internal osilatörler RC osilatörlerdir. RC osilatörlerin çalışma frekansları RC elemanları ile belirleniyor.
- 

![image](https://user-images.githubusercontent.com/75746171/148378364-ab4856d1-b870-4721-9162-2cb3a398ff8a.png)

- Kristal + 2 kapasite. Kristalin frekansı ne ise osilatör o frekans ile çalılıyor. Exernal da osilatör aslında içeride fakat frekansı belirleyen kristal elemanı dışarıda yer alıyor. Bunun sebebi Kristalin yer kaplaması ve gerektiğinde değiştirilebilmesi.

Yani İşlemciler çalışmaya her zaman internal dan başlıyorlar. Fkat bir alt program devreye girererek farklı yolu devreye sokarak kristal osilatörden frekansı değiştiriyor. Yani önce 8 mhz den çalışmaya başlıyor daha sonradan kristal devreye giriyor. External doğrudan devreye girmiyor.

Kaç mhz de çalıştırmalıyız?
---
İşlemcinin mhz başına harcadığı akım bellidir. Uzun süre dayanması gereken batarya varsa ve hız önemli değilse düşük frekansta çalıştırılabilşir. Fakat çalışma hızı çalışlma zamanında da değiştirilebilir..

![image](https://user-images.githubusercontent.com/75746171/148380207-46c2caec-3780-4179-81f7-3bc43be3a1d6.png)

Kontrol uçlarından yön seçerrek saat işareti ile birlikteveri gönderiiyor. Aynı anda bir yerden bir yere gönderilenbilir. Aynı anda 2 yön olmaz. Aynı anda kullanılacaksa busmatrix denilen kavşak noktalarına ihtiyaç var.

![image](https://user-images.githubusercontent.com/75746171/148380379-7c799083-497c-4f11-8daf-a9a2ad87c135.png)
- DMA işlemcinin araya girmeden bir bellek bölgesinden başka bir bellek bölgesine veri trasnferini sağlayan birim.
- I/O portu: Lojik seviyede 0 ve 1 haberleşmes iiçin giriş çıkış içinç kullanılan veya özel durumlarda analog seviyede giriş çıkış almak için kulanılan uçlardır.

![image](https://user-images.githubusercontent.com/75746171/171000633-61da5048-cf10-414e-ba47-b6c5f2e3ccc7.png)
- Koruma diyotları, yüksek veya ters gelen gerilimi bloke et. Uca yüksek gerilim uygulanması durumunda.
- VDD + 07 volt ve üstü gerilimlerde diyot üzerinden akım yukarı gidecek ve iç sistemi koruyacak. Aynısı ters yönde de geçerlidir.
- 3 durumlu bir anahtarlama çıkış devresi NMOS-PMOS
- Flloating, kullanılmayan uç varsa inputsa, ben onu 0 veya 1 okuyabilirim. Kullanılmayan uıçların toprağa bağlanmasının tavsiye edilmesinin sebebi, bu uçlardan parazit almamak.





![image](https://user-images.githubusercontent.com/75746171/148382192-a7f3f1a1-7748-4ca0-8355-837e851cc992.png)

2 device birbirine bağlandığında (i-o kanalları aracılığıyla) iki tarafı da 0 yapabiliriz.

Open drain ne zaman kjullanılıyor?
- 2 durumlu haberleşme. Bazı haberleşme protokolleri 2 durumlu kullanılıyor. (ı2c) Hiçbir zaman taraflar çıkış 1 durumunu kullanöıyor.

Ders 4 )(07.01.2022)
---
Bluepill - cortex m3
Blackpill - cortex m4

![image](https://user-images.githubusercontent.com/75746171/171632949-81c758b3-dc3e-4cbd-985b-f3be2442840e.png)

- Vcc - Gnd uçları 
Bunlara 100 nf bypass bağlanması lazım, içeride yüksek frekanslı işaretler dolaşırken direnç gösterir. Yüksek frekanslı işlemleri işlemcinin dışına çıkmadan bypass etmek.

![image](https://user-images.githubusercontent.com/75746171/148546470-55ea7965-4493-4c3d-9db6-96d05446dfd0.png)

Buradaki offset aslında o structer'ın neresinde olduğunu gösteriyor.

Offset: bir nokta referans alınarak o noktadan ne kadar uzak olduğunu belirleme.

Not
---
![image](https://user-images.githubusercontent.com/75746171/181219250-a4207548-ceaf-4f65-b846-711ff3eefe00.png)

- Burada base olarak tanımlanan yer bellekte çevresel birimler için ayrılan bellek bölgesinin başlangıç adresine karşılık geliyor.

![image](https://user-images.githubusercontent.com/75746171/181220283-72036129-66f0-44a0-bf66-9b73d241e7fd.png)

- PortC nin başlangıç adresi
- 
![image](https://user-images.githubusercontent.com/75746171/181220398-076a21a4-6b80-4514-8f46-16d5ac10a7d7.png)

Not
---
![image](https://user-images.githubusercontent.com/75746171/181220657-ab449af5-5b15-4a3a-956f-5d908259ef49.png)

- Buradaki değerler yazdığımız değerlerin dışında dışsal sebepler ile değişebilir demek.
- 5 yazarım ama okuduğumda 7 alabilirim.
- Ne yazıyorsam onu okuyorum olayı yoksa volatile vardır.
- Çevresel registerların tamamı volatile olarak tanımlanmış.

![image](https://user-images.githubusercontent.com/75746171/181222241-ec50b53f-a4a4-463c-b03a-794080ad4574.png)

- uint32 4 byte lık bir integer olduğu için 4 byte offset.

![image](https://user-images.githubusercontent.com/75746171/181224933-97c53586-0b67-4a36-bff5-330765b45b11.png)

![image](https://user-images.githubusercontent.com/75746171/181224978-1f072234-cdb1-47c6-bbc7-f7e407b9d13f.png)

- 16 pin var ve 4 bit ile ifade ediliyor. 64 tek register a yetmediği için CRL ve CRH diye ayrılmış.

Ders 5
---

![image](https://user-images.githubusercontent.com/75746171/181235698-3d512890-72b0-4233-937a-fa0b27a6e9de.png)

- Mod bitleri giriş ve çıkış olduğunu belirliyor.


Set - Reset Register
---
![image](https://user-images.githubusercontent.com/75746171/181241525-3b2f10dd-c135-4cbc-bca4-82f32812e429.png)

- İlk 16 bit set işlemi, diğer 16 bit reset işlemi.
- 3 - 6 - 7 - 12 Çıkış 1 oldu
- 2 - 5 - 10 - 13 - 14 sıfır oldu.

![image](https://user-images.githubusercontent.com/75746171/181250059-54c8933f-04ec-4fda-a51e-69a15ac6307b.png)

- Bir delay fonksiyonu
- Burada wait yerine boş deyim verseydik bazı derleyiciler optimize edip bu kodu atlayabiliyor.

Port Configuration Lock Register
---

![image](https://user-images.githubusercontent.com/75746171/181250980-2683731e-8d7a-482f-9031-1410ffc0a489.png)

Notlar:
---
- İşlemci resetten çıktığı zaman registerlar hangi değerleri alıyor?
- GPIO nun konfigurasyon registerları floating input olarak başlıyor.
- Open drain ve push pull arasında güç harcama farkı bazı işlemcilerde var fakat bazılarında yok. Mosfet açık devre olduğnda yüksek empedansı olması sebebiyle kayda değer bir güç kaybı olmaz.

Handler
---
Belirli bir görevi yapmak üzere (kesme) yazılmış olan alt program parçalarına handler deniliyor.

- Event - Olay
- Eylem - Handler


Ders 6-A
---
Multitasking
 
RTOS sistemleri multitasking'i etkin bir biçimde yapılmasını sağlıyor.

- Paralal olarak yapılabilir. YAni her bir görev farklı bir işlemci tarafından gerçekleştirilebilir.
- Yani Birden fazla işlem aynı işlemci taraf-fından yapılıyor olabilir.
 

![image](https://user-images.githubusercontent.com/75746171/151873516-3bed6b94-d85c-42ab-a060-70bcca9b48e3.png)

- RTOS Sistemlerin en önemli özelliği de olayların gerçekleşmesi ile işlenme zamanları arasında geçen süreyi minimum tutarak Kısa zamanda işlemek.
- Bu işletim sistemlerinde birden fazla process var ve bunlar mümkün olduğunca düşük gecikmeyle işlenmesi durumunda fayda sağlamaktadır.

Örnekler:
---
- Otonom araçlar
- Kalp pili


RTOS sistemleri avantaj ve dezavantajları
---
- Gerçek zamanlı çalışma
- Hazır sistem fonksiyonları
- Sistemi çok iyi bilmeliyiz. RTOS ta sistem çok iyi bilinmiyorsa verim alınamaz.
- RTOS da cpu nun core sistemi RTOS un kontrolünde. Ayrıcalıklı çalışmaya izin vermeyecek.
- non-rtos sistemde tüm sistmee hakimiz fakat diğer tarafta sistemin kritik özellikleri RTOS'a devredilmiş.


Interrupt
---

Olay >>> İşlem

Bir olay ve olayın  gerçekleşmesi
Sıcaklık 30 dereceyi geçince ocağı aç.

![image](https://user-images.githubusercontent.com/75746171/151876483-feae2511-73c8-4d7d-a812-c3f70f9a73b1.png)

- Proc_A içindeyken ProcF yi çalıştırmayı gereken bir durum oldu.
- Burada interrupt devreye giriyor. Bu aslında var olmayan bir alt programın çağırılmasıyla olay orada işleniyor ve kaldığı yerden devam ediyor.
- Yani kesme nedir? Bir olay ile bağlantılı olarak o olayın işlenmesi için bir alt programın çağrılmasıdır.

Kesme kaynağı : Bir olayın kesme oluşturabilme özelliği varsa kesme kaynağıdır.

![image](https://user-images.githubusercontent.com/75746171/151877338-95952cba-4bdb-4963-8677-611d88b5a935.png)

- Interrupt mekanizmasının kullanabilmesi için bir kesme kaynağının işlemcinin kesme yöneticisine (NVIC) bağlanmış olması lazım. 

ISR (Interrup Service Routine)
---
Olay >>> işlem

- Buradaki işlemin alt programı ISR dir. Yani olay gerçekleştiğinde çalşacak olan alt program bizim ISR'miz.

Handler: Bir olayı işleyen fonksiyondur.
ISR: KEsme işleyen fonksiyondur.

Her ISR bir handler fakat her handler bir ISR değil.

IRQ (Interrupt Request)
---
![image](https://user-images.githubusercontent.com/75746171/151879427-0ae32c0e-cb98-408d-ab70-f040dbd66f1d.png)

- Koşulların tünmü sağlanıyorsa NVIC e bir başvuru yapılıyor. Controller da duruma göre (Interrupt Priority)



Interrupt vector Table
---
- Kaç numaralı kesme geldiğinde nereye gitsin.
- Interrupt adres tablosu
- Olay gerçekleşiyor fakat olay gerçekleşince nereye gideceğini nereden biliyor?
- Olaylar ve kesme kaynağı (interrupt source) ilişkilendirmesini biz yapanmıyoruz. Bunlar donanımsal olarak ayarlanmış.
- PA0 ucunda yükselen ya da düişen kenar olduğunda 7 nolu kesme oluşacak. Bunu biz belirleyemiyoruz. 

Ders 6 - B
---

![image](https://user-images.githubusercontent.com/75746171/152142910-79b9121c-7e1e-4697-9fa5-ba3cd880f6ae.png)

Buraya kullanmadığımız çevresel birimleri de dahil etseydik bir zararı olmazdı. Çünkü bu linkerlar akıllı. Kullanılmayan fonksiyonları koda dahil etmiyorlar.

- BASE PROJESİ YAZILDI, TEKRAR ET.

State Machine Modellemesi
---
![image](https://user-images.githubusercontent.com/75746171/181515852-3ebe6585-9a32-4e05-9d33-c21281ea2cf0.png)

Saat ayarlama state machine:

![image](https://user-images.githubusercontent.com/75746171/181517231-ecf333b3-f9a4-4455-bc7c-62f586e1c67c.png)

Kod ile ifadesi:

![image](https://user-images.githubusercontent.com/75746171/181517493-91f7e4b9-7b3f-46e0-99b4-1c9217e7349e.png)

- Görev fonksiyonlarında iyi çalışan model state machine modelidir. İyi kurgulanması gerekir.

Ana program kesmeden nasıl etkilenmiyor?

- Ana program akarken kesme geliyor ve kesme oluştuğunda o andaki kaldığı yer ve registerları kaydeder. Diğer fonksiyondan geri çıktığında kaydetteiği her şeyi geri yükleyerek program kaldığı yerden devam ediyor. 
- Kesilme öncesi bilgileri işlemci stack bölgesine kaydediyor, stack onları otomatik olarak push ediyor.

Saat
---
![image](https://user-images.githubusercontent.com/75746171/181524414-59934975-09b8-479b-86bd-6151a9e81292.png)

- Saat bize her zaman gerekiyor. Devamlı artan bir sayaç.  

Not:
---

![image](https://user-images.githubusercontent.com/75746171/181545608-9e298e06-ac39-4859-95f8-24ae12ac17d7.png)

- Normalde volatile olmasaydı a ve b'ye 5 değerini atabilirdi. Ama volatile oldğu zaman yazdığım değeri okuma garantim yok. En son bulunan değeri korumak zorunda değil. Volatile derleyiciyi uyarır. O değişkene erişirken her zaman kendisine eriş. Dolaylı olarak erişme.

Ders 7 
---
Tüm arm çekirdeklerinin içinde bir timer var. Arm çekirdeğinden gelen. Geriye doğru sayan timer. SystemTick timer. Biz u timer ı programlayarak standart bir timer olarak kullanabiliriz. Tipik olarak task switching de kullanılıyor. Bir RTOS kullanıldığı zaman her task ı belli süre çalıştırıp diğerine geçmek için bu handler kullanılıyor.

![image](https://user-images.githubusercontent.com/75746171/181699844-c770b22b-4354-427a-b634-003cb13a2dcf.png)

- Kesmenin oluşması için donanımsal bir sebep gerekir. Bu kesmede donanımsal sebep sayacın sıfıra ulaşmasıdır.
- Kesmenin de bireysel olarak aktive edilmesi de gerekir. Default olarak 2 tane donanımsal kesme hariç tüm kesmeler deaktive edilmiştir.

![image](https://user-images.githubusercontent.com/75746171/181700916-10784455-73cb-4469-bd67-90e876d00464.png)

- IO'ların kullanılabilmesi için onlara clock sağlanabilmesi gerekir.

- Bazı alternate function uçları open drain durumunda oluyor. I2C haberleşmesi 2 durumlu bir haberleşme olduğu için çıkış 1 kullanılmıyor. 

Ders 8
---

Katmanlama
---
![image](https://user-images.githubusercontent.com/75746171/181763602-7e4b6e39-969a-49fb-b78f-ee8507f7c5a8.png)

- En altta donanımın fiziklse kısmı bulunuyor
- Biz donanıma erişmek için RAM bölgesindeki özel bazı alanları kullanıyoruz. Registerlar. Function Register

![image](https://user-images.githubusercontent.com/75746171/181755523-925fcd67-103e-43f1-938b-a095b5600a65.png)

- CMSIS Denilen bölge arm çekirdek özelliklerini kontro letmek amacıyla ve ST nin çevresel özelliklerini kontrol etmek amacıyla yapılmış olan tanımlamaları buılunduruyor.
- Bir üst kademede 2 adet library bulunuyor.
- Bir tanesi CMSIS in kütüphane kısmı. 3 dosya halinde görüyoruz. misc.c - cm3.c - cm3.h

- Çekirdek + çevresel donanımı kontrol etmek için structer kullanacaksınız.

![image](https://user-images.githubusercontent.com/75746171/181759326-ad2b00b3-8f0a-4793-a519-b586ad761401.png)

- ST Preipheral Library çevresel birimlerin kontrolü amacıyla düzenlenmiş kütptane. Uart, spi, gpio...
- CMSIS ARM ın kendi çekirdek bölgesinin kontrolü için (NVIC, DMA)

Hardware Abstraction Layer (HAL) (io.c - io.h)

![image](https://user-images.githubusercontent.com/75746171/181766131-b9c6de1a-8c66-40b2-8005-7c63c5f3b9d4.png)

- Değişik çevresel birimler için yazılmış çevresel birim kütüphaneleri.

![image](https://user-images.githubusercontent.com/75746171/181775976-a1a6b9f0-3904-43d5-910a-38902bb1576e.png)

- misc.c  Kesmelerde bazı fonksiyonları kullanmamzıı sağlayacak.
- Hangi birimi kullanırsan kullan onun saat işaretini aktive etmek için ve kapatmak gerekebileceği için rcc.c yi dahil ettik.
- Kullanmadığımız çevresel birimleri de dahil etseydik bir zararı olmazzdı çünkü bu linkerlar çağırılmayan fonksiyonları koda dahil etmiyorlar.

Real time:
---
Biz uygulamalarda yaptığımız işlem hep bir olay ve olayın işlenmesi şeklinde gerçekleşir.

![image](https://user-images.githubusercontent.com/75746171/152150640-7918d119-95d9-4ec1-a140-37ae8a5a6509.png)

Olay 9 öncelikli ise olay 2 işlenirken işlem 2 den mümkün olduğunca kısa szamanda çıkarak olay 9 a geçer.

Real time demek olayların öncelik sırasına bakarak bunlarn mümkün olduğunca gecikmesiz olarak işlenmesi demektir.
Real time sistem dediğimiz zaman olay ve işleme zamanının önceliğin de göz önüne alınarak kısa tutulması.
Oay ve oalyın işlenmesi arasındaki süreç uzuyorsa real time'dan uzaklaşıyoruz demektir.
RTOS da olayların mümkün olduğunca az gecikme ile işlenmesi hedeflenir. Fakat birden fazla olay aynı zamanda meydana gelebileceği için önceliklere uygun olarak en az gecikme ile gerçekleşir.

Haberleşme
---
Gömülü sistemlerde haberleşme dahili ya da harici olarak yapılabilir

Sistemin kendi içinde haberleşmesi ve başka bir sistemle haberleşmesi.

Haberleşme seri ya da paralel olabilir.

Seri: Aynı zaman diliminde tek bir bit verinin gönderilmesi.
Paralel: n-bit

SDIO, HD44780, Memory controler - Paralel haberleşme
Usart/UART, SPI, I2C - Seri Haberleşme

![image](https://user-images.githubusercontent.com/75746171/152194150-492e4ed5-5cfa-4508-8311-bcd6f36818fa.png)

![image](https://user-images.githubusercontent.com/75746171/152195775-57443dbe-6483-472e-8215-83b3de6a29ef.png)

USB çoklu çünkü host tarafından birden fazla slave bağlanabiliyor. I2C çoklu.

Başlatma yetkisi olan: Master Device

Sadece cevap yetkisi olan: Slave Device

En basit: telefon haberleşmesi. Arayan taraf master cevap veren slave.
USB haberleşmesinde PC'deki portumuz master olan host portu. Cihaz ise slave.

Senkron haberleşme: Ortak saat kullanımı
Asenkron haberleşme: Kendi saatlerini kullanma

![image](https://user-images.githubusercontent.com/75746171/152198168-66a7a490-f933-4d39-90ff-0d4dfc91f5d9.png)


![image](https://user-images.githubusercontent.com/75746171/152198527-13725ec1-a876-4cc8-9f12-ffb067ea5e2a.png)

SPI- Senkron
UART - Asenkron

Kontrol uçlaından 1 tansini adres - data seçimi için kullanarak aynı veri yolu adres ve veri iletimi olarak kullanılması yaygın bir uygulama.

Ders 9
---

Neden senkron haberleşme deniliyor?
---
Veri hazırlandığı zaman B tarafı veriyi hemen kabul etmez. Kabul edilmesi için clock hattında yükselen kenar(örneğin) oluştuğunda bu onay anlamına gelir. B tarafı yükselen kenarı gördüğünde veriyi kabul eder. Bu onaylama mekanizması senkron haberleşmenin ana ilkesidir. Saat işaretini üreten taraf master device. 

1 Adım veri, senkron haberleşme kaç bir yapılıyorsa o kadar bit veri gönderilmesi demek.

1. Data Setup (Verinin hazırlanması)
2. Clock Generation (Saat işaretinin üretilmesi)
Saat işaretinin buradaki anlamı onaylama.
Veri hazırlanırken karşı taraf almaya kalkarsa yanlış veri gidebilir.

![image](https://user-images.githubusercontent.com/75746171/152201677-22356c5c-ea4e-4efc-8226-75a2a906694a.png)

Veri clock tan önce gelmelidir.

Delay fonksiyonu
---
![image](https://user-images.githubusercontent.com/75746171/152202158-9a44724c-e096-4a0f-b092-564ee2d3c168.png)

Bekleme süresi = sabit bir süre +- tolerans değeri.

Kritikte bekleme süresinin tam istenilen değerde olmasını istiyoruz. 

Kritik olmayanda bekleme süresi > sabitherhangi bir değer.

![image](https://user-images.githubusercontent.com/75746171/152203077-8c224173-108b-454d-bdc7-aabcb5e3b38e.png)
 
Critical section yönetimi neden gerekiyor? Araya kesme girerse bekleme süresi uzayarak kritik beklemeden uzaklaşacağımız için giriyor.

Kritik beklemeler genelde mikrosaniyeler mertebelerindedir.

Aslında critical section yönetiminde kesmeleri kapatıyoruz. 


LCD
---

![image](https://user-images.githubusercontent.com/75746171/152207636-c09c7923-6b14-42f3-a6ae-b465c3a7478c.png)

3 tane kontrol ucu var. 4-5-6
6 ucu clock işareti olarak kullanılıyor. Onaylama mekaniğzması high-low olarak ayarlanmış.
5 ucu read-write ayarı

Display'e gönderilen veri 2 tür olabilir. Bu RS ucuyla belirlenebilir.
Bir komut olabilir.
Bir karakter kodu olabilir.

Komut Göndermek: Hangi konuma yazdığını blirmeke istiyorsan komut gönderirsin.
Karakter kodu: Hangi karakteri yazacağını belirlemek için

![image](https://user-images.githubusercontent.com/75746171/152834208-babb3333-6f4f-45b6-bf31-6f7c1391b478.png)

0 Nolu komut clear screen.

![image](https://user-images.githubusercontent.com/75746171/182317941-be4e3582-0a18-4300-943f-2df4f7e84ac3.png)

Ve bunların tanımlamaları

![image](https://user-images.githubusercontent.com/75746171/182318092-021b6805-f21f-4eee-ba2b-17e5efe16e3e.png)

Bu uçlar, biz simplex kullanacağımız için bunların hepsi pushpull çıkış olarak kullanılacak.

![image](https://user-images.githubusercontent.com/75746171/182319198-c04fcc9a-355f-401e-aa2b-d2c5198ccd15.png)

E'yi başlatmadan önce 0 olduğundan emin oluyorum.

![image](https://user-images.githubusercontent.com/75746171/182323450-520f0f79-55ef-429d-a0fd-d70ec06e682c.png)

![image](https://user-images.githubusercontent.com/75746171/182324175-aa3a914f-4274-4899-a5b8-05d37fd0d5f7.png)

Portları değerler ile and işlemine tabi tutuyor ve yazılacak değerleri aktarıyor.

Veriyi hazırladık, göndermek için saat işretini üretmemiz gerekiyor.


![image](https://user-images.githubusercontent.com/75746171/182325610-66e4af24-ae11-4674-8124-bf1c33289cca.png)

![image](https://user-images.githubusercontent.com/75746171/182326282-b1aac940-1245-4eb7-b59f-3646baea3f5d.png)

- = operatörü olmadığı için öteleme operatörü c nin değerini değiştirmez.

![image](https://user-images.githubusercontent.com/75746171/182327198-7ced62cd-ed9d-4936-a257-5b1e614de1d7.png)

- Komut gönderdiğimiz için rs değerini ayarlıyoruz. 

Display nasıl çalışır?
---
Tüm displaylerin bellek bölgesi var. Birde fiziksel display var, gözüken kısmı.

Display kontroller, display memory e bakarak fiziksel kısma görüntüyü aktarıyor.Display memory nin her bir hafıza gözüne biz karakter kodu yazıyoruz.

![image](https://user-images.githubusercontent.com/75746171/182352469-b00da216-6fab-4e16-9dac-b4b17ba2b19a.png)

LCDInit fonksiyonu

![image](https://user-images.githubusercontent.com/75746171/182358395-0256a4fd-b80c-44d5-b9d3-fe55ccc5b59e.png)

- Port yapılandırma

![image](https://user-images.githubusercontent.com/75746171/182358740-a7533a50-06ea-4451-b549-14c3b8c51b28.png)

- Diğer ayarlar
 
Ders 10
---
![image](https://user-images.githubusercontent.com/75746171/182578263-7ffb4a74-b428-4dfe-bf93-0dfaaff3b72a.png)

- İlerde LCD display yerine konsoldan Uart, oled display gibi ortamlar kullanacağız o yüzden genel bir consoleinit fonksiyonu yazalım.

![image](https://user-images.githubusercontent.com/75746171/182594755-1d2c4c93-6ad6-4ea5-99b0-f7b1da022cfe.png)

Console ile ilgili 3 tanımlama. 

Printf nereye yazacak?

- Aslında printf kendi içinde düşük seviyeli right fonksiyonunu çağırıyor. (Handle değeri olarak, stdout'u vererek). Write ın da nereye yazdığı belli değil. 
- Write fonksiyonunu biz yazıyoruz, aslında printf olarak write çağırılıyor, bunun nereye gönderileceğine biz karar veriyoruz. Bizim yazmamız gereken şey write fonksiyonu. 
- IAR __ write olarak kullanıyor. Write fonksiyonu standartlarda belirtilmiş bir fonksiyon değil. Ama sonradan bu stardart hale gelmiş. Write fonksiyonunu farklı derleyiciler bu fonksşyona direkt değil önüne _ koyarak kullanabiliyorlar.
- Printf kullanmak projenin kod boyutunun büyümesine sebep olur fakat çok büyük avantajları vardır.
- Bazı derleyiciler aşağıda putch'yı çağırıyor. Bu standart değil. Biz IAR derleyicisinin write fonksiyonunu çağırdığını biliyoruz ve kontrol altına alıyoruz.
- Fakat burada printf bizim yazdığımız write fonksiyonunu çağırmıyor, biz yazmasak ta orada bir write fonksiyonu var. Biz write fonksiyonunun yeni bir versiyonun yaıyoruz. Boş bir write yerine dolusunu yazıyoruz.
- Write fonksiyonu link aşamasında nasıl soruna yol açmıyor?
- Derleyicinin özelliği. __ weak dediğimiz zaman bunun sadece weak versiyonunun yazılmasına linker izin veriyor ve sorun çıkmıyor. 2 tane versiyonu varsa ..

![image](https://user-images.githubusercontent.com/75746171/182599925-439cb4e8-0fde-4580-b707-35023b2476fb.png)

- Yani aslında bir yerde bu fonksiyonun weak ile tanımlamasını yapmışlar, biz bunu weak olmadan yazdığımızda ona overwrite yapmış oluyoruz. Bu durumda bağlamada problem çıkmıyor.


![image](https://user-images.githubusercontent.com/75746171/182596775-d84c8f0e-4fee-4678-a4a4-1acebce10bbe.png)

- Bunu bu şekilde çağırırsam printf bunu çağırır ama hiçbir şey olmaz.

![image](https://user-images.githubusercontent.com/75746171/182597076-1752759d-dcaf-4489-a808-eba2041d86f0.png)

- Burada ise standart tanımlamalara göre print edilen karakter sayısını döndürecek.

- Write fonksiyonunu yazıyoruz

![image](https://user-images.githubusercontent.com/75746171/182604820-96b85975-23ef-4ff0-ba7e-af61c6e4a4a5.png)

- Eğer buffer = NULL ise başlangıçta hemen çıkıyoruz.

Örnek:
---
![image](https://user-images.githubusercontent.com/75746171/182605371-2ce7a646-c07b-4b55-86b7-af2c935746ae.png)

- Bunlar hep PUBWEAK olarak tanımlanmış. PUBWEAK C'deki __ önekiyle yazılan fonksiyonlar gibidir. PUBWEAK bunun assembly versiyonudur.
- Burada tanımlananları tekrar yazarsak PUBWEAK versiyonu devre dışı kalacak.
- Printf'in nereye yazacağına biz kendi yazdığımız write fonksiyonu ile belirliyoruz.

Write fonksiyonu
--- 

![image](https://user-images.githubusercontent.com/75746171/182615421-db636208-84a1-4a3b-b8d3-0d3c5aab5b5b.png)

![image](https://user-images.githubusercontent.com/75746171/182615960-3187c2c0-70ea-4feb-8cf5-100285a31110.png)

Putch Fonksiyonu
---

![image](https://user-images.githubusercontent.com/75746171/182618598-458ed15a-966a-425a-b02a-2870f9c41a30.png)

- Bazı özellikler ekleyeceğiz, özel karakterlerde farklı davranabiliriz.

- printf'in nereye yazacağı belli olmadığı için (mikrodenetleyici programlarında), terminali belirlemek bize bırakılmış.

![image](https://user-images.githubusercontent.com/75746171/182629240-a864b08d-c80d-47d6-a58a-0e0957d24c2a.png)

- printf write'ı çağırıyorsa, başka bir görevi yok mu neden biz çağırıyoruz?
- prinft aslında formatlı yazıyor. Format açılımını yaparak (%'leri açarak) çözümleyerek formatsız string haline çevirip standart output dosyasına yazmak üzere bize gönderiyor. Amawrite fonksiyonun içerği de belli olmadığı için onu da biz yazıyoruz. Biz write fonksiyonun içeriğini öyle ayarladık ki çıkış LCD'de gözükecek. Biz farklı bir write fonksiyonu yazarak bu çıkışı UART'a gönderebilirdik. (Terminal açardık ve printf'in içeriğini pc'de görürdük)

RS-232
---
- A ve B device
- Taraflar birbirlerine 2 ayrı hat ile bağlılar. rx-tx. Toprak hatları ortak.
- Endüstride çok kullanılmasının sebebi uzun mesafe haberleşmesine uygun olacak şekilde yüksek gerilim tanımlanmış olması.

- Normalde TTL'de biz 1 için 3.3 - 5V 0 için 0 volt.

- Genel olarak < 20 metre
- RS232 elektriksel, mekanik, veri transfer özelliğklerini bulunduran birleşik bir protokoldür. RS485 - RS422 sadece elektriksel.
- RS232 1 eksi gerilim 0 artı gerilim olarak çalışıyor.

UART - USART
---
![image](https://user-images.githubusercontent.com/75746171/182835984-4d4c2595-bc69-4eef-98b3-cfad8563d7a2.png)

- RS232 eksi gerilimi 1 olarak Artı gerilimi 0 olarak çeviriyor. RS232 Transceiver. MAX232 5V - MAX3232 3.3V seviyesinde.
- Yani biz gerçek RS232 portuna UART bağlamak istiyorsak MAX3232 gibi bir çevirici kullanmamız lazım. İki taraf ta UART ise RS485 kullanmamıza gerek yok. Eğer RS485 çalışan bir cihaza bağlanmak istiyorsak çevirici kullanmamız lazım. MAX

- UART < 5 metre
- RS232 < 20 metre
- RS485 Çok daha uzun mesafe. 1000 metre örnek

- UART 2 şekilde kullanılabiliyor. Kart içi ve dışı.
- Tipik kullanım hızları 1200 bps - 115200 bps

Bu haberleşmenin kısıtları
---
Haberleşme sırasında veriler 0-1 olarka gönderildiği için, hattın kapasitesi arttıkça kareler eğilmeye bağlar. Bir noktadan sonra sinüse yakın bir duruma gelir. Okuyan tarafın bunu yanlış bulma ihtimali ortaya çıkar. Hat kapasitesi ile iletişim hızı ters orantılıdır.

![image](https://user-images.githubusercontent.com/75746171/182837653-1bd3b844-4e81-419d-aa18-0b49b4898a2e.png)

Örneğin:
- UART ı işlemcinin 10 cm yakınında cihaza bağladığımda 1 milyon bps ile haberleşebilirm fakat 2m uzaktaki cihaza kablo ile bağladığı mzaman sorun çıkabilir.
- Hat kapasitsini belirleyen ise kullanılan kablonun kalitesi ve kablonun uzunluğu.
- Kablo uzadıkça koblonun toplam kapasitesi artacak bu da iletişim kalitesini etkileyecektir.

Ders 11
---

Uart - RS232
---

Bir tanesi TTL, diğeri - ve +. Elektriksel kısımları farklı.
Uart sadece mikrodenetleyici standartlarında kullanılan elektriksel değerleri kullandığı için sorun çıkarmıyor. ikrodenetleyicileri birbirini bağlamakta ve sensörlere bağlamakta yaygın olarak kullanılıyor. 
- Seri haberleşmedir. AYnı anda tek bit gönderilebilir. 
- Asenkronm haberleşmedir. Onaylama mekanizması, clock hattı ya da enable hattı bulunmuyor. sadece gönderme ve alma hattı olacak. 
- Full Duplex bir haberleşmedir.

![image](https://user-images.githubusercontent.com/75746171/182839315-bfeb38b6-a405-4e19-aff6-df2c2e8dd451.png)

- Uart ve RS232 birimini birbirine bağlıyorsak bunların aralarına bir dönnüştürücü koymamız gerekiyor.
- Bu dönüştürücü elektriksel seviyeleri tersine çevirir , MAX232 5V TTL, MAX 3232 3.3V 

![image](https://user-images.githubusercontent.com/75746171/183365644-079d7ae3-c381-4796-ad7d-a5335d04093f.png)

Fakat biz farklı bir dönüştürücüye bağlayacağız. UART - USB serial çeviren bir dönüştürücü ile.  Ve diğer tarafını da PC'ye bağlayacağız.

![image](https://user-images.githubusercontent.com/75746171/183365860-38f3488d-df60-46d9-8e7e-df944eb29f3b.png)

- PC'ye bağlandığında PC'deki terminal programı aracılığı ile diğer tarafı UART seviyesinde bir seri haberleşme sağlıyor.
- Eski zamanlardaki tüm pc'lerde RS232 portu vardı fakat artık yok. şimdi pc bağla ntısı için bu tür dönüştürücüler kullanıyoruz.


- Seri haberleşmede Tx - RX hattındaki işaretin zmana göre değişmesi
- Normal şartlar altında gerilim vdd seviyesinde (IDLE). 
- Gönderme işlemi hattı 0'a çekerek başlıyor, T süresi boyunca.
- Sonra dşük anlamlı bitten başlayarak  T süresi kadar hattı 1 veya 0 yapıyor.
- En son data bitincen sonra en az 1 T lik bir boşluk lazım (STOP bit).

![image](https://user-images.githubusercontent.com/75746171/183369317-25031964-d901-4fa5-bf99-e6a304291494.png)


- En son gönderilen veri 0 olduğunda, alıcı taraf yeni bir veri gönderecek. Fakat hat zaten sıfır. O yüzden bu ihtimale karşı araya idle geçme boşluğu veriliyor. 
- Yani son bit bittikten sonraen az 1T süre kadar bir beklemeyi zorunlu tutuyor
![image](https://user-images.githubusercontent.com/75746171/183370240-386288aa-fc55-4542-a08c-a40af64143f7.png)

IDLE'ın IDLE olduğu nereden anlaşılıyor?
---
- Haberleşme portları direkt 1'den başlıyorlar. Gönderen taraf hattı 1'de tuttuğu için alıcı taraf direkt 1'den başlıyor. Zaten haberleşme IDLE'dan başlıyor.
- Harhangi bir start biti gelmediği sürece IDLE kabul edilir. Eğer start biti geldiyse de frame'in içinde olduğu için IDLE'da değil kabul ediliyor.

![image](https://user-images.githubusercontent.com/75746171/183375022-a56a2d9f-58d4-4ea6-a9d2-bf49a61c05ce.png)

İki tarafın baudrate'i doğru çalışmayor olsun:

![image](https://user-images.githubusercontent.com/75746171/183382315-060145e4-9ae0-43c2-9971-7d1d0e32c23f.png)

- Alıcı tarafın örnek alma anı her seferinde bir miktar sola kayacak. Yeni start biti ile birlikte hata resetlenir ve sıfırdan başlar. 
- Buradaki hatalar frame in sonunda max değeri bulur.

 Parity (EŞLİK)
 ---

- Bir hata belirleme algoritmasıdır.
- Parity haberleşmesinin kullanılan bit oranına göre verimsizliği sabit olarak ortaya çıktıpı için (hata belirleme kapasitesinin düşüklüğü nedeniyle) neredeyse kullanılmıyor. 
- Tek- çift olarak toplam 1 sayısının tek ya da çift olmasına göre bunu tek veya çifte tamamlama algoritmasıdır.

![image](https://user-images.githubusercontent.com/75746171/183395908-0705b28c-7ce8-42bb-b8a6-5128f399ba44.png)

- En zayıfı parity haberleşmesi, gönderilen bit oranına göre hata belirleme oranı çok düşük.
- Checksum - Orta seviye. n byte gönderildikten sonra her bir n byte için tekrar k byte kadar toplam değeri eklenir. Modüler olarak toplanır. 
- Alıcı taraf ta bu veriyi aldıktan sonra toplayarak karşılaştırır ve doğruluğuna bakar.

![image](https://user-images.githubusercontent.com/75746171/183397520-e92a9b82-ecee-4b20-9eb8-d131c9818780.png)

Checksum ve parity artık gözden düşen algoritmalar artık bunların yerini CRC aldı.

UART Kod
--

Biz kendimiz bir UART konfigürasyon yapısı tanımlkayalım. Bu bizim daha basit bir şekilde kullanmamızı sağlayacak.

![image](https://user-images.githubusercontent.com/75746171/183411098-31f8822a-d363-4e46-b7a8-921a7d8483c3.png)

- TX pininin io indeksi, Bizim dipğer io library miz ile uyumlu bir yapı elde etmek istiyoruz.

Bu veri türündeki elemanı tyanımlayalım.

![image](https://user-images.githubusercontent.com/75746171/183411530-8ed64beb-9601-4f6e-a086-310042cefa4d.png)

Port tanımlamaları

![image](https://user-images.githubusercontent.com/75746171/183413895-b728170a-99a6-4a4c-9660-2a75eaad532f.png)

Uart init fonksiyonu

![image](https://user-images.githubusercontent.com/75746171/183414317-7fc8bee8-d4fb-4ebe-a700-b35bd9b318b9.png)

- Firmalar arm cmsis yapısına uygun kalabilmek için kütüphanelerini buna uygun olarak tasarlıyorlar. 
- Başlatmak structer ı var. Bu ilgili header dosyasında tanımlı. 

Haberleşme
---
Seri haberleşmede gönderme ve alma işlemlerinde kullanılan shift registeri vardır. Burada gönderme ve alma işlemleri birbirinden bağımsız yapıldığından burada 2 register vardır.

TSR'nin boş olduğunu varsayıyorum. Bu verileri TSR'ye biz yüklüyoruz. Star ve stop bitlerini ekledi. Düşük bitten başlayarak sağa doğru iterek iletti.

![image](https://user-images.githubusercontent.com/75746171/183435970-cf35fb5a-5c5d-4892-9059-f166dddb7ed1.png)

Veri gönderme

![image](https://user-images.githubusercontent.com/75746171/183436326-87f29821-0a74-4fa1-9628-e6882ee9ce13.png)

Ben veriyi yüklediğmide veri gidiyor. Bu yüzden yüklemenin bitip bitmediğini kontrol etmem gerekiyor.

![image](https://user-images.githubusercontent.com/75746171/183436623-b2a2c994-f120-43bf-b22c-ac5de4edfcf3.png)

- İlk parametre port indeksi. 2. parametre veri.

Ders 12
---

![image](https://user-images.githubusercontent.com/75746171/183585761-6d74f022-9a11-471d-b504-f6cc663282c2.png)

- Ver igönderme işlemi transmit shift register da yapılıyor ve alma işlemi REceive shift registerda yapılıyor.
- Fakat biz doğrudan bu registra yüklemek yerine aradaki transmit data register a yükllüyoruz. (USART data register a veri attığımız zaman TDR ye aktarılıyor. Eğer tsr boşsa buradakiveri de tsr ye geçer).
- Gönderme ve almada veri kaybı olmaması için biz aradaki tdr ve rdr den veriyi çekmemiz lazım. Bazı işlemcilerde bu registerlar daha fazla ve buradaki birikecek veri sayısı daha fazla oluyor. Fakat hepsi dolduktan sonra yeni veri geldiğinde üzerine yazılır ve veri hatalı aktarılır.

![image](https://user-images.githubusercontent.com/75746171/183597218-8b6d7080-05f2-4c50-a0e2-891c7cca8dfd.png)

- İlk önce inittypedef tanımlıyoruz. IO port modu.
- Clock işareti sağlanır.
- init yapısı
- Çevresel aktifleştir.

![image](https://user-images.githubusercontent.com/75746171/183601068-aea647db-306f-4192-847a-f29b22420441.png)

- Aslında 1.5 T sonra örnekleme yapıyor demiştik fakat bu örnekleme tek bir noktada değil. Birden fazla noktada örnekleme yapmayı bekliyor ve hep aynı değeri bulmayı bekliyor. Eğer farklı değer okursa işarette bozukluk vafr demektir. Noise error flag stabil olmayan gürültülü bir işaret olduğu anlamına geliyor.
- Frame error stop bitinin beyni gibidir. Stop biti olması gereken yerde 0 bulursa frame de bozukluk var demektir. Frame error hangi şartlarda ortaya çıkabilir?
- Baudrate uyumsuzluğunda ortaya çıkabilir. Veri yolundaki problemlerde de çıkabilşr.
- Parity kontrolü yapılyıorsa ve parity biti bozxuksa parity error çıkabilir.

De bouncing
---

![image](https://user-images.githubusercontent.com/75746171/183614145-b07f39c2-d33d-499b-84da-b01c094fc730.png)

Aradaki gürükltülerin giderilmesi işlemi 

Başarının tekrarı sayacı:

![image](https://user-images.githubusercontent.com/75746171/183615700-671aea18-c2d5-476d-a510-fb6f23f17244.png)

Dezavantajı, De bouncing süresi kadar gecikme olması. Araya giren faz farkı.

![image](https://user-images.githubusercontent.com/75746171/183616454-9bd14fb2-1a02-4576-9059-5d1bb2924e29.png)

Bazı yerlerde butona heman basılmasından sonra bir delay fonksiyonu kullanılıyor. Bu da de bouncing in ilkel bir yoludur. Aslında bu kötü bir yöntem. Çünkü bu sıçramalar sadece başta ve sonda değil aralarda da olabilir.

Kumanda örneği: Normalde tuşa basılmadığı müddetçe uyku modunda minimal enerji harcıyor.Tuşa basıldığında bu kesme ile uyanıyor, uyandıktan sonra debouncing uyguluyor olabilir. Tuş bırakıldıktan sonra da tekrar uyku moduna geçiyor. Yani interrupt + çift yönlü debouncing iyi bir yöntem.

Tek yönlü debouncing  tuşa basma anının belirlenmesi sorgulanmaz. Hat sıfıra düşünce tuş bastı kabul edilir. Ve tuşa basıldıktan sonra tuşun bırakılması kontrol edilir. Yani sıçrama sadece tuşa basıldıktan sonra olduğu kabul edilir. 

![image](https://user-images.githubusercontent.com/75746171/183619185-4eb584eb-561d-4ad2-8ff6-f80ca2d80216.png)

Tek yönlü debouncing bu tür dalgaları da tuşa basılmış olarak kabul edebilşr. Bu bir dezavanatajdır fakat çok nadirdir.


Çift yönlüde ise iki yönde de kontrol edilir.

Ders 13
---
Tüm elemanların bir ömrü vardır, elemanın türüne ve imal edilişine göre değişiyor. Kristal elemanının bile zamanla aşınması oluyor. MEekanik olarak titreşiyorlar ve agent parametreleri var zamanla bunların rezonans frekansları değişiyor.

Button uygulaması
---

Tekrar et

Ders 14
---

Real Time Clock
---

![image](https://user-images.githubusercontent.com/75746171/183636107-9901606a-e894-4384-a9c6-3c4beb90a543.png)

- Sleep mode, sadece cpu duruyor. İşlem yapmayı kesiyor. Bir event gelene kadar. Fakat bu sırada tüm regulator ve system clocklar çalışmaya devam ediyor.
- Stop mode, daha Yüksek güç kazancı, regulatorler düşük güç moduna geçer. CPU nun clock osilatorleri de duruyor bu sebeple external interrup durumunda çıkıyor. Saat işaretleri de durduğu için çevreseller de çalışmayı durduruyor. Fakat besleme gerilimleri eksilmediği için bunların hafızaları muhafaza ediliyor. 
- Standby tamamen kapatma modu. Saat kesiliyor, regulatoler kesişliyor, VBAT hariç hepsi off durumuna geliyor. İşlemci softwaremode kapatma yöntemi.

Bakcup Registers BKP
---

![image](https://user-images.githubusercontent.com/75746171/183637155-2bf0c285-5255-4d4a-a498-c5ded986653f.png)

- C13 ucu farklı özelliklere sahip. Toplam akım verebilme kapasitesi daha düşük. Temper detection özelliği. Bazı durumlarda beckıp registerlarını sıfırlamak gerekebilir. 
- Bu özellik default olarak aktif değil. Aktif hale getirdiğimizde temper pinine bir buton bağlayarak 0 ve 1 geçisinde backup registerlarını dışardan sıofırlamak için.

![image](https://user-images.githubusercontent.com/75746171/183638251-a1da5e4a-4d8b-4f9b-8115-9e5bd12ad31a.png)

- RTC ve RTCC. RTCC olunca takvim kısmı da var ama RTC sadece bir sayaç. 32 bit. Belirlediğimiz periyotta artan. 
- Bizim saniye sayacımız fakat bu backup domainde yer alması nedeniyle enerji kesilse bile busaymaya devam ediyor.
- Belirli bir referanstan başlayarak şu ana kadar kaç saniye geçti.

DERS 16
---

Semaphore 
---
- Bir işaretleşme mekanizması.
- İki ayrı thread ortak bir veri alanını kullanıyor. Thread multitaskingde çalışan her bir kol.
- A işini bitriince global alanını true yapar. B true yu görünce A nın işinin bittiğini görür ve işlemine kaldığı yerden devam eder.

![image](https://user-images.githubusercontent.com/75746171/184075496-f64e9588-3258-44d9-b888-3f05bf08b249.png)

Mutex
---

Kaynak var ve bu kaynağa ulaşmak isteyen farklı thread ler var. 

![image](https://user-images.githubusercontent.com/75746171/184075922-a2f76b0f-9eaf-4a31-8813-80383614526f.png)

Mutex 0 ise kaynak kullanımda değil. Kullanan thread onu 1 yapıyor ve meşgul hale getiriyor başkası geldiğinde blokeye giriyor.

SPI - Serial peripheral interface
---

- En basit olmasına rağmen en kafa karıştırandır. 
- Kabul görmüş bir standartı olmadığı için herkes farklı yorumlamış.
- Büyük firmaların kabul gördüğü standartlardan kullanacağız.
- Seri ve senkron bir haberleşmedir. (Haberleşen tarafların 1 tanesi saat işareti üretiyor ve ortak kullanılıyor.)
- Haberleşme çift yönlü, full duplex.
- Data exchange protokolüdür.

![image](https://user-images.githubusercontent.com/75746171/184106137-bcebfc2c-17a1-4969-87ce-5881d87fba9e.png)

- Her gönderdiğinde alır.
- Çok yüksek hız gerektiren haberleşmelerde tercih edilir.

![image](https://user-images.githubusercontent.com/75746171/184108117-a1f33733-6016-4f03-8925-c0ead422f762.png)

- Seri haberleşmede saat işareti onay mekanizması olarak kullanılıyor.

![image](https://user-images.githubusercontent.com/75746171/184108859-d8d62b44-2b98-4107-9e45-4cebcb01f42d.png)

- R ve C parametreleri yükseldikçe işaret bozulmaya başlar. (Kareden uzaklaşır). Sıfırlar ve 1 lerin yerleri karışmay başlar.

Hızlı olmasının sebebi :

- Senkron olması, ortak saat vardır ve örnekleme zamanları tam ortaya gelecek şekilde ayarlarnmıştır.
- Tarafların RC'si düşük. Daha keskin, yükselme ve düşme zamanları daha düşük.

![image](https://user-images.githubusercontent.com/75746171/184109713-e8317a28-e4ef-4f74-a8be-64f3af9738f8.png)

SPI bağlantısı tipik 4 hat.

![image](https://user-images.githubusercontent.com/75746171/184111243-219b64cd-9b69-4910-890b-2bb93f5a5fe0.png)

- 4 adet SPI modu var.
- CPOL, IDLE durumunu belirliyor. CPOL 0 ise IDLE 0.

![image](https://user-images.githubusercontent.com/75746171/184113593-c00d2bfe-3025-4279-93cc-0dfc6c6490e3.png)

![image](https://user-images.githubusercontent.com/75746171/184113621-89f0b878-3766-4dae-bb98-4b81f4d58230.png)

SPI Mode Number


![image](https://user-images.githubusercontent.com/75746171/184113681-5da8a135-9664-4acc-aaaa-18b05bb39ecc.png)

Haberlerşme şeması
---

![image](https://user-images.githubusercontent.com/75746171/184114030-35f6f10c-8890-4116-9038-2278d2026868.png)

- Burada donanımsal olarak SS1, 2 ve 3 hatlarımız yok. Bunlar herhangi bir IO uçlarıdır.
- SS1 i 0 da tuttuysam en üsttekini seçtim demektir. Clock hepsine bağlı oldğu için haberleşme hepsine gidiyor fakat diğerleri cevap vermeyecek.

Gönderme ve alma aynı anda oluyorsa slave nasıl cevabı hazırlayıp gönderiyor?

- Master soruyu soruyor aslında slave cevabı bir sonraki bytte gönderiyor.

Not: Ölü pikseller, sürekli aynı pikseller kullanıldığında o piksellerin diğerlerine görekalibrasyonu bozulabiliyor.

SSD1306 oled display
---

Biz aslında bir şey gönderdiğimiz zaman displayin RAM bölgesine yazıyoruz. O da kendi ramindeki bilgiyi eşleyerek displayde gösteriyor. Biz aslında ram ile irtibat kuruyoruz. Onun ram ile display arasında bir fiziksel elektronik devre var. 

![image](https://user-images.githubusercontent.com/75746171/184129111-28d89c0d-eec6-4dc6-9e58-5b17e63d6d3c.png)

Ya mod 0 ya da mod3 kullanmalıyız. Modu kullanacağımız elemana göre belirliyoruz.

![image](https://user-images.githubusercontent.com/75746171/184129859-8818c8ed-526b-4126-9dd1-7717599614ba.png)

- 128x64 her bir kesişim noktasında bir led var. Her bir page de 8 tane var. Her bir satırda 128 tane segment var. Herhangi bir piksele ulaşabilmek için o pikselin hangi page de olduğunu bulamız lazım. 
- 111,25 noktasına gidelim. Page 3 ün 1. bitini ve segment 111 seçtiğim zaman ulaşıyorum.

![image](https://user-images.githubusercontent.com/75746171/184130833-805e4a1a-05e1-49d3-ac1f-2a2c5622ccfb.png)

- Öncelikle buradaki değeri kopyalamamız lazım. Sonra aldığım değerde değiştirmek istediğim yere karşılık gelen yeri maskeliyoruz ve tekrar geri yazıyoruz. 


DC hatını 0 veya 1 de tutarak komut veya veri gönderiyoruz.

![image](https://user-images.githubusercontent.com/75746171/184137061-87fa8607-234b-453f-85b8-23d29d1465c8.png)

![image](https://user-images.githubusercontent.com/75746171/184137134-856005a4-7f3a-4b72-84b5-0d3e33a3c57c.png)

A5 - A6 - A7 , PB0 - PB1 - PB10 Display sırasına göre res - DC ve CS olarak kullanılacak.

![image](https://user-images.githubusercontent.com/75746171/184137747-4ae0003c-d45e-44b0-9a89-8571181eddf9.png)

DERS 17
---











































