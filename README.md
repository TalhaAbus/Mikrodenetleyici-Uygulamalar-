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
- 





























