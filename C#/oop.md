## Object Orientented Programming ve Prensipleri Nedir?   
Object Orientented Programming Nedir?
Nesneye dayalı programlama Object Oriented Programming ismiyle ilk olarak 1960'larda yazılım geliştirme çözümü olarak ortaya çıktı. Yıllar içinde de olgunlaştı. Günümüzde de en sık kullanılan yaklaşımlardan biri haline geldi. Nesne yönelimli yaklaşım gerçek hayattaki modellerin yazılıma adapte edilebileceğini savunan bir yaklaşımdır.

Not: İlerleyen kısımlarında Nesne Yönelimli Programlama'dan yani Object Oriented Programming kavramından OOP ismiyle bahsedilebilir.

Günümüzde C# ile birlikte bir çok dil nesne yönelimli programlama yani OOP desteği sunar. OOP 3 ana prensipten oluşur.
1.	Encapsulation (Kapsülleme)
2.	Polymorphism (Çok Biçimcilik)
3.	Inheritance (Kalıtım)

## Inheritance  
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

## Polymorphism ve Sealed Class  
Polymorphism (Çok Biçimcilik)
Çok biçimcilik ile birlikte hayatımıza sanal yani virtual metotlar giriyor. Virtual metotlar ile nesne yönelimli programlama ilkesi olan polymorphism'i uygularız. Sanal metotlar kalıtım alınan yani miras veren sınıf içerisinde yazılan ve daha sonra alt sınıflarda yeniden yazılabilen metotlardır. Bunu da virtual ve override anahtar kelimeleri sağlar.

Virtual metot tanımı :
```
public virtual void UyaranlaraTepki(){
    Console.WriteLine("Canlılar uyaranlara tepki verir.");
}
```
```
Alt sınıf içerisinde override metot kullanımı:
public override void UyaranlaraTepki()
{
    base.UyaranlaraTepki(); // üst sınıftaki komutları çalıştırır.
    Console.WriteLine("Bitkiler güneşe tepki verir.");
}
```

## Interface 
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

## Abstract Class  
Abstract class'ları sadece kalıtım için kullanılan sınıflar gibi düşünebilirsiniz. Bazı özellikleri ile sınıflara benzerlerken bazı özellikleriyle arayüzlere benzerler. Abstract sınıfları arayüz ve virtual metotların birleşimi gibi davranış gösterirler.

Kısaca abstract sınıfların özelliklerine bakacak olursak:
•	Normal sınıflar gibi new() anahtar kelimesi ile türetilemezler.
•	Interface ler gibi metot bildirimi yapabilirsiniz.
•	Sanal metotları override eder gibi abstract metotlar override edilebilir.
•	Abstract metotların gövdesi yazılamaz.
•	Bir abstract class bir abstract metot içeriyorsa, abstract sınıftan türeyen tüm sınıflar bu metodu override etmek zorundadır.
•	Bir sınıf sadece tek abstract sınıftan kalıtım alabilir.
•	Abstract sınıf başka bir abstract sınıftan kalıtım alabilir. Dolaylı olacak türeyen sınıfta birden fazla abstract dan kalıtım almış olur. Ve bağlantılı olduğu tüm abstract sınıfların bildirimi yapılmış olan abstract metotlarını override etmek zorundadır.

ÖNEMLI: Abstract sınıf içerisinde metot bildirimi yapabilmek için metodun erişim belirtecinden sonra "abstract" anahtar kelimesi mutlaka yazılmalıdır.

ÖNEMLI: Abstract metotdan türetilmiş sınıf içerisinde abstract metodun kullanılabilmesi için de override anahtar kelimesinin kullanılması gerekir.

