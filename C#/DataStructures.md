## Veri Yapıları ve Algoritmalar
* Binary Numbers 
Bit, Bytes (8Bit=1 Byte)
8 bit=2^8=256 sembol
Şimdi karşımıza çıkan problemlerin bir tanesi, 256 sembolden daha fazla bir depolama alanı isteyebiliriz. Peki bu durum da ne yapacağız? Aslında çözüm çok basit byte'ları yan yana koyarak depolama alanımızı arttıracağız. 

* Recursion: Bir problemin alt problemlere bölünüp hesaplanmasına, nerde son bulacağımı belirttiğimiz ifadelere recursion (Özyineleme) diyoruz.( Fibonacci)

* Arrays: Dizi, ortak bir adla atıfta bulunulan benzer türde değişkenler grubudur. Ve her veri öğesine dizinin bir öğesi denir. Öğelerin veri türleri, char, int, float vb. gibi herhangi bir geçerli veri türü olabilir ve öğeler, bitişik bir konumda depolanır.

* Linked-List: Linked-List (Bağlı listeler), yan yana zorunluluğu olmadan veri tutmamızı sağlayan yapılardır. Yeni gelen eleman için hafıza'da yeni bir alan açmamız gerekmez. Array'dan farklı olarak evet elemanlar hafıza içerisinde dağılmış olabilir, fakat son gelen eleman kendinden bir önceki elemana adresini bildirmek zorundadır.

* Stack: Stack, LIFO (Last in First out) (En son giren en önce çıkar) mantığına dayanan, elemanlar topluluğundan oluşan bir yapıdır. Push, yığının üzerine eleman eklemek için kullanılır (Koliye kitap koymak). Pop ise, yığından eleman çıkarmak için kullanılır. Peek, yığının en üstteki öğesini döndürür.

* Queue: Queue (Kuyruk), FIFO (First in First out) (İlk giren ilk çıkar) prensibine dayanan, girişlerde ve çıkışlarda belirli bir kurala göre çalışan yapıdır. 
Queue (Kuyruk)'da eleman eklemesi yaparken enqueue methodunu kullanıyoruz. Eleman silerken ise dequeue methodunu kullanıyoruz.

* Hash Function/ Hash Table
Indexleme: Arraylerde 0 bazlı bir indexleme vardır. Bazı programlama dillerin 1 bazlı indexlemeler olsa da genel olarak 0 bazlı indexleme kullanılır.
Hash Table, key value prensibine dayanan bir array kümesidir. Key olarak çağırdığınız elemanın değerini (value) yansıtır. 
Hash fonksiyonları değişken uzunluklu veri kümelerini, sabit uzunluklu verilere dönüştüren fonksiyonlardır. Yani fonksiyonun çıktılarını array’in index’i olarak kullanıp, verileri bu indexlerde tutacağız.
Hash Function + Array  yapısına Hash Table deniyor. 

* Hash Collision: Hash Function farklı iki değerden aynı sayı üretilirse bu duruma Collison (çarpışma) denir. Bu olay istediğimiz bir durum değildir.

*	Hash Function'lar bazen farklı durumlar için farklı sonuçlar üretemeyebilir. Örnek olarak araçları bir hash function dan geçirelim. Bu fonksiyonumuz son harflerine göre bir değer atıyor. Örneğin, motor ve tır için aynı değerleri ataması collision'a neden oluyor.
*	Collision sorunuyla az karşılaşabilmek için kaliteli bir hash function olmalı. Bu sayede verimli bir Hash Table elde etmiş oluyoruz.
*	Çarpışma sayısı arttıkça aradığımız şeyi bulma hızı azalır.


### Algoritma Analizi
Algoritma analizi, var olan kaynaklara göre en uygun algoritmayı seçmek için uygulanır. Programlama dillerinden ve donanımlardan bağımsız bir şekilde Algoritma analizi yapılmalıdır. Aksi taktirde en uygun sonuç alınamayabilir.

Time-Complexity'i Caseleri:
1. Worst Case: Algoritmanın en yavaş çalışma durumu. Algoritma, en kötü senaryoya ne kadar hazırsa, bizi o kadar memnun edebilir. 
2. Average Case: Genel olarak beklediğim durum. 
3. Best Case: Algoritmayı en hızlı çalıştıran durum. Beklediğimiz en iyi durum.

Big O Notation: Argüman belirli bir değere veya sonsuzluğa yöneldiğinde bir fonksiyonun sınırlayıcı davranışını tanımlayan matematiksel bir gösterimdir.

Sorting (Sıralama) Algoritmaları:
Sorting, bir eleman dizisini, belirli sıralama kurallarına göre sıralama yapar.
* Insertion Sort-n2
* Merge Sort-nlogn
* Quick Sort-pivot

Searching (Arama) Algoritmaları:
Arama algoritmaları ise istediğim özellikteki verinin elimdeki veri setlerinde aranıp, bulunup getirilmesi demek.
* Linear Search: Tek tek elemanları dolandıktan sonra istediğim elemanın olup olmadığına bakmaktır.
* Binary Search: low-mid-high
* Binary Search Tree 


### Variables
Değişkenler bizim uygulama geliştirirken kullandığımız veri tutucularımızdır. 

Variable Declaration:
1.	Lokal değişkenler: Fonksiyonların içinde
2.	Parametre olarak tanımlanan değişkenler: Fonksiyon parametresi olarak
3.	Global değişkenler: Tüm fonksiyonların dışında

```
#include <stdio.h>

int gid = 21; // Global değişkene sadece sabit bir değer atanabilir.
int fonk(void);
int main(void)
{
  int id1 = 84;      // Lokal değişkene sabit değer atama
  int id2 = id1/gid; // Lokal değişkene bir işlem sonucunu atama
  int id3 = fonk();  // Lokal değişkene fonksiyonun geri döndürdüğü değeri atama

  printf("id1 değişken değeri: %d\n", id1);
  printf("id2 değişken değeri: %d\n", id2);
  printf("id3 değişken değeri: %d", id3);
  
  return 0;
}

int fonk(void)
{
  int id = gid/3;
  return id;
}
```
### Operatörler 
Uygulama içerisinden bir atama işlemi ya da durum karşılaştırması yapmak istediğimizde operatörleri kullanırız. Bazen koşullara bağlı olarak çalıştırılacak kod bloğunun değişmesi gerekir. Karar yapıları ve operatörler birlikte kullanılarak bu sağlanabilir.
İşlevlerine göre operatörler aşağıdaki gibi kategorilendirilir.
*	Atama ve İşlemli Atama Operatörleri (=, +=, -=, *=, /=)
*	Mantıksal Operatörler (||, &&, !)
*	İlişkisel Operatörler (==,!=, <, >, >=,<=)
*	Aritmetik (+, -, *, /, %, ++, --)

### Tip Dönüşümleri
1.	Implicit Conversion (Bilinçsiz ya da kapalı dönüşüm)
2.	Explicit Conversion (Bilinçli ya da açık dönüşüm)

```
// Implicit Conversion
      double numDouble = numInt;
```

```
// Explicit casting
int numInt = (int) numDouble;
```
### Try-Catch-Finally  ve Mantıksal Hatalar 
Try catch blokları sayesinde uygulama içerisinde bir hata oluştuğunda belirtilen işlemler yaptırılabilir.

Exception Handling:

try{ Hataya sebebiyet verme ihtimali olan kod }
catch { Hata ile karşılaşıldığında ne yapılacağı buraya yazılır }
finally{ Hata olsun olmasın mutlaka yapılmasını istediğimiz işler varsa buraya yazarız }

Örnek:
```
try
{
    int a = int.Parse(Console.ReadLine());

    int b = int.Parse(Console.ReadLine());

    int c = a+b;

    Console.WriteLine(c);
}
catch(Exception ex)
{
    Console.WriteLine("Bir Hata Oluştu: "+ ex.Message);
}
finally
{
    Console.WriteLine("İşlem tamamlandı.");
}
```

Yukarıdaki örnekte konsoldan alınan string ifade int.Parse metodu ile integer a dönüştürülüyor. Ama konsoldan girilen veri sayıya dönüştürülebilen bir string olmayabilir. Bu durumda bu kod hataya düşecektir. try catch bloğu içerisinde alınması gerekir.

Uygulama geliştirirken bu tarz hataya neden olabilecek noktaları yakalıyor olmak gerekiyor. Bunun için de kod üzerinde zaman geçirmek ve düşünmek gerekiyor. Hızlıca kodu yazıp geçmek doğru bir yaklaşım değildir. Yazdığımız kod bloğunun açıklarını düşünmemiz ve bu açıklar için önlemler alıyor olmamız gerekiyor.

Error Types :
*	Compile Time 
*	Run Time


