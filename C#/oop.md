## Object Orientented Programming ve Prensipleri Nedir?   
Object Orientented Programming Nedir?
Nesneye dayalı programlama Object Oriented Programming ismiyle ilk olarak 1960'larda yazılım geliştirme çözümü olarak ortaya çıktı. Yıllar içinde de olgunlaştı. Günümüzde de en sık kullanılan yaklaşımlardan biri haline geldi. Nesne yönelimli yaklaşım gerçek hayattaki modellerin yazılıma adapte edilebileceğini savunan bir yaklaşımdır.

Not: İlerleyen kısımlarında Nesne Yönelimli Programlama'dan yani Object Oriented Programming kavramından OOP ismiyle bahsedilebilir.

Günümüzde C# ile birlikte bir çok dil nesne yönelimli programlama yani OOP desteği sunar. OOP 3 ana prensipten oluşur.
1.	Encapsulation (Kapsülleme)
2.	Polymorphism (Çok Biçimcilik)
3.	Inheritance (Kalıtım)

### Inheritance  
Inheritance (Kalıtım)
Bir sınıfın başka bir üst sınıftan miras almasına kalıtım denir. Miras veren sınıf tüm özelliklerini alt sınıfa aktarmış olur. 

Sözdizimi :
<code> Kalıtım Alacak Alt Sınıf : Miras Verecek olan Üst Sınıf </code>

Kalıtım çok soyut bir kavram olması itibariyle anlaşılması zor bir konudur. Bunun için en kolay anlaşılabilecek örnekler üzerinden denenmesinin faydalı olduğunu düşünüyorum. Bu da Canlılar - Hayvanlar - Bitkiler ayrımı ile anlaşılabilir.

Hayvanlar ve Bitkileri canlılar sınıfından türeyen 2 sınıf gibi düşünebilirsiniz. Çünkü hem hayvanların hem bitlilerin ortak bazı özellik ve davranışlar vardır. Bunlar ne olabilir ?

Canlılar:Beslenme, Solunum, Boşaltım

Bu davranışlar hem hayvanlarda hem bitkilerde ortak olduğu için bir sınıf içerisinde tanımlanıp alt sınıflara yani hayvan ve bitkilere kalıtım olarak aktarılabilir. Tıpkı doğada da olduğu gibi.

Peki Hayvanlar sınıfına yakından bakarsak; Kus ve Ordek olarak 2 ayrı sınıf türetebiliriz. Tüm hayvanlarda ortak görülebilecek bitkilerden farklı olarak sürü haline hareket ettiklerini görürüz. Kus ve ördek içinse uçma ve yüzme gibi 2 ayrı davranış var.

Hayvanlar: Sürü halinde hareket etme
Kuş: Uçmak
Ördek: Yüzmek

Buradaki örnekleri arttırmak mümkün. Yazılımda kalıtım üzerinde çalışırken en önemli olan nokta bu gruplamayı doğru yapabilmektir.
Şimdi yukarıdaki modellemeyi koda dökerek sınıfları ve metotlarını yazalım.

Canlılar:
```
public class Canlilar {
    public void Beslenme(){
        Console.WriteLine("Canlılar beslenir.");        
    }

    public void Solunum(){
        Console.WriteLine("Canlılar solunum yapar."); 
    }

    public void Bosaltim()
    {
        Console.WriteLine("Canlılar boşaltım Yapar."); 
    }
}
```
Hayvanlar:
```
public class Hayvanlar: Canlilar{
    public void SuruHalindeHareket(){
        Console.WriteLine("Hayvanlar sürüler halinde hareket eder."); 
    }
}

public class Kus:Hayvanlar{
    public void Ucmak(){
        Console.WriteLine("Kuşlar uçar");
    }
}

public class Ordek:Hayvanlar{
    public void Yuzmek(){
        Console.WriteLine("Ördekler yüzer");
    }
}
```

```
Bitkiler:
public class Bitkiler: Canlilar{
    public void FotosentezYapmak(){
        Console.WriteLine("Bitkiler fotosentez yapar."); 
    }
}

public class TohumluBitkiler:Bitkiler{
    public void TohumlaCogalma(){
        Console.WriteLine("Tohumlu bitkiler tohumla çoğalır.");
    }
}

 public class TohumsuzBitkiler:Bitkiler{
    public void SporlaCogalma(){
        Console.WriteLine("Tohumsuz bitkiler sporla çoğalır.");
    }
}
```

Şimdi Tohumlu bitkiler ve Ördek sınıfının nesnesini yaratalım.
```
TohumluBitkiler tohumluBitki = new TohumluBitkiler();
tohumluBitki.Beslenme();
tohumluBitki.Bosaltim();
tohumluBitki.Solunum();
tohumluBitki.FotosentezYapmak();
tohumluBitki.TohumlaCogalma();

Console.WriteLine("**********************");

Ordek ordek = new Ordek();
ordek.Solunum();
ordek.Beslenme();
ordek.Bosaltim();
ordek.SuruHalindeHareket();
ordek.Yuzmek(); 
```

Yukarıdaki örnekte görebileceğiniz üzere. Her sınıf kendi kalıtım aldığı sınıfın metotlarına erişebiliyor. Çünkü üst sınıfından belirli davranışları miras almıştır.

Types of Inheritance:
* Single Inheritance
* Multi-level Inheritance
* Hierarchical Inheritance
* Hybrid Inheritance 
* Multiple Inheritance

Important Points: 
•	C#'ta kalıtıma üç tür katılabilir: Class, Struct ve Interface.
•	Bir sınıf yalnızca tek bir sınıfı miras alabilir. Birden fazla sınıftan miras alamaz.
•	Bir sınıf bir yapıdan miras alamaz.
•	Bir sınıf, bir veya daha fazla arayüzü devralabilir (uygulayabilir).
•	Bir Yapı, bir veya daha fazla arabirimden miras alabilir. Ancak, başka bir yapıdan veya sınıftan miras alamaz.
•	Bir arabirim, bir veya daha fazla arabirimden miras alabilir, ancak bir sınıftan veya yapıdan miras alamaz.
•	Yapıcılar veya yıkıcılar miras alınamaz.

Not:
Super Class: Özellikleri miras alınan sınıf, süper sınıf (veya bir temel sınıf veya bir üst sınıf) olarak bilinir.
Sub Class: Diğer sınıfı miras alan sınıf, alt sınıf (veya türetilmiş sınıf, genişletilmiş sınıf veya alt sınıf) olarak bilinir. Alt sınıf, üst sınıf alan ve yöntemlerine ek olarak kendi alanlarını ve yöntemlerini ekleyebilir.
Reusability: Kalıtım, "yeniden kullanılabilirlik" kavramını destekler, yani yeni bir sınıf oluşturmak istediğimizde ve zaten istediğimiz kodun bir kısmını içeren bir sınıf olduğunda, yeni sınıfımızı mevcut sınıftan türetebiliriz. Bunu yaparak, mevcut sınıfın alanlarını ve yöntemlerini yeniden kullanıyoruz. 

![inheritance](/images/inheritance.jpg)

### Polymorphism ve Sealed Class  
Polymorphism (Çok Biçimcilik)
Çok biçimcilik ile birlikte hayatımıza **sanal** yani **virtual** metotlar giriyor. Virtual metotlar ile nesne yönelimli programlama ilkesi olan **polymorphism**'i uygularız. Sanal metotlar kalıtım alınan yani miras veren sınıf içerisinde yazılan ve daha sonra alt sınıflarda yeniden yazılabilen metotlardır. Bunu da **virtual** ve **override** anahtar kelimeleri sağlar.

Virtual metot tanımı :
```
public virtual void UyaranlaraTepki(){
    Console.WriteLine("Canlılar uyaranlara tepki verir.");
}
```

Alt sınıf içerisinde override metot kullanımı:
```
public override void UyaranlaraTepki()
{
    base.UyaranlaraTepki(); // üst sınıftaki komutları çalıştırır.
    Console.WriteLine("Bitkiler güneşe tepki verir.");
}
```

Not:
* Sealed class: Kalıtımı alınmasına izin vermez. (Virtual, Protected keywordu kullanılmaz.)
Virtual: Üst sınıfta geriye dönüş tipinden önce kullanılır ve metodun alt sınıflarda override edilmesine izin verir.
* Override: Alt sınıfta geriye dönüş tipinden önce yazılır. Üst sınıftaki metodun biçimini değiştirmek istediğimizde kullanırız.

```
1.	public class X  
2.	{  
3.	    public virtual void A()  
4.	    {  
5.	    }  
6.	}  
7.	public class Y : X  
8.	{  
9.	    public override void A()  
10.	    {  
11.	        base.A();  
12.	    }  
13.	}  
```

*	Mühürlü sınıf, bir sınıfın miras alınmasını durdurmak için kullanılır. Ondan herhangi bir sınıf türetemez veya genişletemezsiniz.
*	Başka hiçbir sınıfın onu devirip kendi yöntemini uygulayamaması için Sealed method uygulanır.
*	Mühürlü sınıfın asıl amacı, kullanıcıdan kalıtım niteliğini geri çekmektir, böylece mühürlü bir sınıftan bir sınıf elde edemezler. Mühürlü sınıflar, statik üyeleri olan bir sınıfınız olduğunda en iyi şekilde kullanılır.
```
•	public class Y : X  
•	{  
•	    public sealed override void A()  
•	    {  
•	    }  
•	} 
```

### Interface 
Interface (Arayüzler)
Interface yani arayüzler nesneye dayalı programlamanın önemli özelliklerinden biridir. Sınıfların içermesi gereken metotların imzalarının yer aldığı, özelliklerin tanımlandığı bir taslak gibi düşünebiliriz.

Kesin belirlenmiş bir kural olmamasıyla beraber interface isimleri "I" ile başlar. I ile başlayan bir isim gördüğümüzde kolaylıkla bunun bir arayüz olduğunu anlarız. Dolayısıyla standartlara bağlı kalmakta fayda var.

Interface içerisindeki property'lere bir değer ataması yapılmaz, metotların ise gövdesi yazılmaz. Sadece implemente eden sınıfın ne iş yaptığının bir arayüzüdür interface'ler. Ve bir sınıf aynı anda birden fazla arayüzden kalıtım alabilir.

Örnek interface tanımı:
```
public interface ILogger{
    //sadece imzası
    void WriteLog();
}
```

Implementasyon:
```
public class FileLogger : ILogger
{
    public void WriteLog()
    {
        Console.WriteLine("Dosyaya yazdım.");
    }
}

public class DatabaseLogger : ILogger
{
    public void WriteLog()
    {
        Console.WriteLine("Database'e yazdım.");
    }
}
```

### Abstract Class  
Abstract class'ları sadece kalıtım için kullanılan sınıflar gibi düşünebilirsiniz. Bazı özellikleri ile sınıflara benzerlerken bazı özellikleriyle arayüzlere benzerler. Abstract sınıfları arayüz ve virtual metotların birleşimi gibi davranış gösterirler.

Kısaca abstract sınıfların özelliklerine bakacak olursak:
*	Normal sınıflar gibi **new()** anahtar kelimesi ile türetilemezler.
*	Interface ler gibi metot bildirimi yapabilirsiniz.
*	Sanal metotları override eder gibi abstract metotlar override edilebilir.
*	Abstract metotların gövdesi yazılamaz.
*	Bir abstract class bir abstract metot içeriyorsa, abstract sınıftan türeyen tüm sınıflar bu metodu override etmek zorundadır.
*	Bir sınıf sadece tek abstract sınıftan kalıtım alabilir.
*	Abstract sınıf başka bir abstract sınıftan kalıtım alabilir. Dolaylı olacak türeyen sınıfta birden fazla abstract dan kalıtım almış olur. Ve bağlantılı olduğu tüm abstract sınıfların bildirimi yapılmış olan abstract metotlarını override etmek zorundadır.

ÖNEMLI: Abstract sınıf içerisinde metot bildirimi yapabilmek için metodun erişim belirtecinden sonra "abstract" anahtar kelimesi mutlaka yazılmalıdır.

ÖNEMLI: Abstract metotdan türetilmiş sınıf içerisinde abstract metodun kullanılabilmesi için de override anahtar kelimesinin kullanılması gerekir.

