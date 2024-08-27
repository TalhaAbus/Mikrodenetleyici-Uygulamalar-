# What is the use of Volatile keyword?
- C ve C++ dillerinde değişkenlerin bellekte tutulma yönteminin optimize edilmemesini sağlar. Yani volatile olarak tanımlanan bir dğeişken, o değişkeni her okuma ve  yazma işleminde doğrudan kayıtlı olduğu bellek adresinden okuma ve yazma yapılmasını garanti eder.
- Normalde sıkça kullanılan değişkenler için, derleyici budeğişkenleri işlemci kayıtlarından okuyabilir. Bellekteki gerçek adresinden bu değeri okumaz ve yazmaz. Ancak volatile tanımlanan bir değişkeni derleyici optimizasyon yapmaz. Farklı threadler tarafından kontrol edilen değişkenler için çok kritik öneme sahip bir keyword olarak bilinir.
- Birden fazla thread  tarafından kullanılan bir değişken volatile olarak tanımlanmamışsa bir thread bu değişkenin en güncel değerini görmeyebilir. Derleyici değişkenin en güncel değerini görmeyebilir. Derleyici dğeişkenin değerini optimize edebilir ve sadece bu thread için saklanan değeri kullanabilir.

# Bir Pointer Volatile olarak tanımlanabilir mi?
- Evet. Volatile anahtar kelimesi pointer ile birlikte kullanılırsa, bu işaretçinin gösterdiği bellek bölgesinin içeriğinin, programın kontrolü dışında değişebileceğini belirtir.

# What is the size of character, integer, integer pointer, character pointer?
1. Char genellikle 1 byte boyutundadır.
2. int: işletim sistemi ve derleyiciye bağlıdır. En yaygın bıyutu 4 byte.
3. int pointer: Kullanılan sistemin adresleme mimarisine bağlıdır. 32 bit sistemlerde genelde 4 byte, 64 bit sistemlerde ise 8 byte boyutundadır.


  
