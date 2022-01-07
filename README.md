# Mikrodenetleyici-Uygulamalari-

Ders 1 (28.06.2021)
---
Mikrodenetleyici nedir?
---
- Aslında bir bilgisayar sistemini oluşturan elemanlardan bir tanesidir.
- En basit tanımı "Single chip Computer" (Tek bir çipten oluşan bilgisayar)
- Bilgisayar sistemini oluşturan bir çok birim bir araya getirilip tek bir çipte toplanmış hali. Tek çipte toplanmasaydı gerektiğinde ona ek ilaveler yapabilirdik. 
- Çok düşük güöçlerde çalışırlar.

>> Belli bir göreve adanmıştır fakat birden fazla alt görev işleyebilirler, >> Bunlar kendilerine yüklenen sabit bir programı çalıştırıyorlar.

 Arm çekirdeği nedir?
 ---
 Mİkrodenetleyicinin belirli bir kısmı.
 ST firması mikrodenetleyici üretmek için ARM ile anlaşıyor ve ARM mikrodenetleyicinin temel birimlerini içeren çekirdek kısımlarının tasarımlarını satıyor. ST firması ürettiği çevresel birimleri ekleyerek bunları ARM çekirdeğine bağlıyor. 

Cortex M ->  m = Microcontroller 
Cortex = Beyin zarı

Örneğin: Arm firması beynini üretiyor ve st firması da organları üretiyor gibi. Bu şekilde mikroişlemci bütün haline getiriyor.

- Flaş memoryler kalıcı belleklerdir. İçindeki programlar silinmiyor. (Aslında siliniyor ama çok uzun süre 200 yıl gibi)
- Yazma zamanları yavaş, okuma zamanalrı hızlıdır.

Not:
---
![image](https://user-images.githubusercontent.com/75746171/142284261-591e643f-fd83-41af-9f89-f0e5cb61c054.png)

- Buradaki dhrystone bir benchmark testi. İşlemcileri değişik testlere sokarak performanslara göre işlemcileri karşılaştılılıyor ve performans değeri veriyorlar.
- İşklemciyi 10 MHz de çalıştırırsam 12.5 DMIPS işlem günüden olacak. max çalıştırırsam 75x1.25 olacak.
- Bu işlemcilerin işlem gücünü karşılaştırmak için kullanılıyor.
- Single cycle özellik ise tek cycle da çarpma ve bölme ypaabilme özelliği. Bu verimli çalıştırğını gösterir.
- SRAM, Static ram. Yazılı silinir bellk.  

Static ram ve dynamic ram
---
- DRAM yapısal olarak daha basit bir bellek türü.
- İkisi de yazılır silinir bellek.
- SRAM daha hızlıdır. ve daha pahalıdır, transistör sayısı daha fazladır. 
- SRam daha çok hızlı çalışması gereken birimlerde tervcih ediliyor. Güç harcaması daha düşük.


![image](https://user-images.githubusercontent.com/75746171/142285172-ef1a3c48-7251-4795-b95b-6526f5e94c47.png)

- Düşük voltajlar da bir avantaj.
- Power on reset ve Power down reset. Gerilim düştüğünde işlemcinin stabil kalanbilmesi için özel reset devreleri.
- POR işlemcinin düzgün çalışmaya başlaması için gerekiyor.
- PDR ise gerilim düştüğünde stabil kalmasını sağlar. 2 volt altına düştüğünde reset ediyor ve normal seviyeye çıkınca tekrar çalıştırmaya başlıyor.
- Internal RC osilatörü ile çalışmaya başlıyor sonra kristal osilatör 72 MHZ'e pll devresi ile getiriliyor. Bu internal osilatör startup ta kullanılıyor.

PLL: Stabil bir frekansın tam katında bir stabil çıkış elde etmek içinç kullanılıyor.

- Mesela kristal ösilatör 72 mhz ile çalışmıyor. Kristal osilatör stabil olarak çalıştılıp plls devres i ile çarpılarak hedef frekansa geçiliyor.

Dahili osilatör mü kararlı harici osilatör mü?
---
- Harici osiltör. Dahili osilatör RC osilatörüdür. Hata oranları çok daha yüksektir. RC osilatörlerin sıcaklığa karşı gösterdiği değişm de kristale göre daha yüksektir.

- Arm mikroişlemcilerin en öbnemli özelliği düşük güç harcamaları ve verimli çalışmaları bu yüzden mobilde arm lider durumda.

![image](https://user-images.githubusercontent.com/75746171/142287375-bd07a081-9970-4b9b-b1cf-1ec7cacfce61.png)

- Sleep modunda işlemcinin saati ve çevresel birimler çalışmaya decam eder. Fakat çekirdek çalışmayı durdurur. Komutları işlemez.
- Uzaktan kumanda gibi bastığımda çalışsın basmadığımda sleep modunda kalsın.
- Stop modu işlmeci duruyor fakat saat de duruyor. Bu modda hem çekirdek birimi hem de çevresel birimleri çalışmayı durdurur.
- Standby ise işlemciyi tamamen kapatmak. 

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

Ders 3 (06.01.2022)
---

![image](https://user-images.githubusercontent.com/75746171/148369127-81e2c99f-a807-499a-9f47-e739267a1177.png)

Neden 32 bit değil de 8 bit genişlikte adresler?

İşlemci 32 bit işlem yapabilem yeteneğine sahip fakat yeri geldiğinde 8 veya 16 bitlik veriler de çekebilir. Eğer 32 olsaydı 8 bit kullanılacağı zaman gereksiz yere 32 bit geçecekti.

![image](https://user-images.githubusercontent.com/75746171/148371347-4e427bdb-0749-4f02-8079-8209fd46817c.png)

- İşlemcinin çevresel birimlerini kullanmak için biz aslında bu bellek bölgelerine erişiyoruz.
- Yani çevresel bşirimleri yönetme şeklimiz, çevresel bellek bölgesine erişerek buraya bazı değerler yazarak ve okuyarak gerçekleşiyor.
- 

![image](https://user-images.githubusercontent.com/75746171/148372041-dbfd131f-e956-42bd-abfa-c4acc40cfcf7.png)

- İçsel çevresel birimler. Çekirdeğin yönetimi ile ilgili bazı özellikler var. Örneğin NVIC bu bölgede.

![image](https://user-images.githubusercontent.com/75746171/148372384-d655940d-23f7-4284-b76e-37eee46e3033.png)

- Flash memory programın kodunu yani komutlarını bulunduran bölge. Okuma zamanları hızlı ve yazma zamanları yavaş. Enerji kesildiğnde değerlerini korurlar.
- 

![image](https://user-images.githubusercontent.com/75746171/148373463-0bd80b98-6b7c-47b5-ac27-39e8e3647f55.png)

option bytes, Burada işlemcinin kalıcı konfigürasyonlarını yapacak bazı alanlar var. Program çalıştırmak amacı ile değil. 

![image](https://user-images.githubusercontent.com/75746171/148373731-f35e4f4e-105c-4eae-a29f-079c44e6c743.png)

Bildiğimiz RAM. System memory. 


![image](https://user-images.githubusercontent.com/75746171/148374813-ce0c78d0-452f-4235-9f04-8dfd77fcd96f.png)

-  VB pini. Backup batarya Pini. 3.3V verilecek.  Ana güç kaynağını kessek bile backup memoryde kalan bilgiler kalıcı oluyor. 

Register: İşlemcinin çekirdek bölgesinin doğrudan kullanabildiği, aritmetik lojik işlemlerde kullandığı bölgeler.

Stack pointer: İşlemcinin veriler istack memoryde saklayıp geri çekmek için kullandığı bellek bölgesi. Local değişkenlerin tutulduğu alan. İşlemci alt programa girerken belli register depğerlerini saklama kzorunda. 

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

I/O portu: Lojik seviyede 0 ve 1 haberleşmes iiçin giriş çıkış içinç kullanılan veya özel durumlarda analog seviyede giriş çıkış almak için kulanılan uçlardır.

![image](https://user-images.githubusercontent.com/75746171/148382192-a7f3f1a1-7748-4ca0-8355-837e851cc992.png)

2 device birbirine bağlandığında (i-o kanalları aracılığıyla) iki tarafı da 0 yapabiliriz.

Open drain ne zaman kjullanılıyor?
- 2 durumlu haberleşme. Bazı haberleşme protokolleri 2 durumlu kullanılıyor. (ı2c) Hiçbir zaman taraflar çıkış 1 durumunu kullanöıyor.

Ders 4 )(07.01.2022)
---

![image](https://user-images.githubusercontent.com/75746171/148546470-55ea7965-4493-4c3d-9db6-96d05446dfd0.png)

Buradaki offset aslında o structer'ın neresinde olduğunu gösteriyor.

Offset: bir nokta referans alınarak o noktadan ne kadar uzak olduğunu belirleme.




















