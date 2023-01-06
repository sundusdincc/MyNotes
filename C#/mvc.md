## MVC(Model-View-Controller);
MVC, model-view-controller anlamına gelir. MVC, iyi tasarlanmış, test edilebilir ve bakımı kolay uygulamalar geliştirmeye yönelik bir kalıptır. Bu yazıda denetleyici eklemeyi öğreneceksiniz.
ASP.NET MVC çerçevesi, MVC tabanlı Web uygulamaları oluşturmak için ASP.NET Web Formları modeline bir alternatif sağlar. 
Model verileri temsil eder. Görünüm, Kullanıcı Arayüzüdür. Denetleyici, istek işleyicisidir. 

* Controllers: Backend 
* Models: Veritabanı
* Views: Frontend

![mvc](/images/mvc.jpg) ![mvc](/images/mvc-user.jpg)

### N Katmanlı Mimari(N Tier Arc.);
* Kod tekrarını önlemek
* Dry(Don’t Repeat Yourself)
* Projeye olan hakimiyet artar
* Kod okunaklığı artar.
* Clean Code yapısı sağlanır.
* Hata yönetimi kolaylaşır.

1. Entity Layer         : Tablo-Sütun(Class)
2. Data Access Layer    : Crud Operations
3. Business Layer       : Validation 
4. Prensentation Layer  : UI
5. Core Layer                    
6. Api                                

![mvc](/images/bl.jpg)
![mvc](/images/bl1.jpg)

### FluentValidation
FluentValidation bir veri doğrulama kütüphanesidir. FluentValidation ve benzeri ürünlerin kullanılması, verilerin doğru şekilde yani verilerin oluştururken konulmuş kısıtlamaları sağlayarak kurallara uyumlu halde olmasını ve kullanıcı ya da sistem kaynaklı hataların oluşmasını engeller.

### CRUD Operations;
* Create
* Read
* Update
* Delete

```
{
     void Insert(T t);
     void Delete(T t);
     void Updete(T t); 
     List<T> GetListAll();
     T GetByID(int id);
}
```


### Entity Framework mimarisinde temelde üç adet yaklaşım;
1. Code First
2. Database First
3. Model First

EF Core, nesne ilişkisel bir eşleyici (O/RM) olarak görev yapabilir ve bu şunları getirir:
* .NET geliştiricilerinin .NET nesnelerini kullanarak bir veritabanıyla çalışmasını sağlar.
* Genellikle yazılması gereken veri erişim kodunun çoğuna olan ihtiyacı ortadan kaldırır.

Attributes;
1. Predefined Attributes
2. Custom Attributes

### Language-Integrated Query(LINQ);
Sorgu yeteneklerinin doğrudan C# diline entegrasyonuna dayalı bir dizi teknolojinin adıdır.

### API(Application Programming Interface);
Bilgisayar programcılığında, bir uygulama programlama arabirimi (API), yazılım ve uygulamalar oluşturmak için bir dizi alt program tanımı, protokolü ve aracıdır. 
Uygulama programlama arayüzü, bir yazılımın başka bir yazılımda tanımlanmış işlevlerini kullanabilmesi için oluşturulmuş bir tanım bütünüdür. API; web uygulaması, işletim sistemi, veritabanı, donanımlar yahut yazılım kütüphanesi için kullanılabilir.

## Repository Design Pattern;
Programcıların bir varlıkla ilgili tüm temel veri işlemlerini tek bir ana sınıfa entegre etmesine izin verdiği için, bir uygulamada uygulanması tercih edilen kalıplardan biridir.
Bu kalıp olmadan, geliştiricilerin her varlık için aynı mantıkla birden çok sınıf oluşturması gerekir. 
Veritabanımıza herhangi bir ara katman veya Veri Erişim Katmanı (DAL) kullanmadan doğrudan erişiyoruz. 

## Razor syntax;
Razor syntax, sunucu tabanlı kodu bir web sayfasına gömmek için basit bir programlama sözdizimidir. Razor sözdizimini kullanan bir web sayfasında iki tür içerik vardır: istemci içeriği ve sunucu kodu.

```
    @if(IsPost) {
    // This line has all content between matched <p> tags.
    <p>Hello, the time is @DateTime.Now and this page is a postback!</p>
     } else {
    // All content between matched tags, followed by server code.
    <p>Hello <em>stranger</em>, today is: <br /> </p>  @DateTime.Now
     }
```

## Generic Repository;
* CRUD operasyonları
* Her bir crud operasyonuna ait bir metot tanımlanacak.
* Metotların imzası olarak interfaceler kullanılacak.
* Abstract üzerinde soyut ifade olarak interfaceleri tanımlar.
* Concrate üzerinde somut ifade olarak bu interfaceler içinde yer alan metotların içini doldur.
* Genericbütününe uygulanacak.     
* Ekleme-Silme-Güncelleme=>Void türünü kullan.

## SOLID Prensipleri;
SOLID ilkesi, Bob Amca olarak da bilinen Robert C. Martin tarafından tanıtıldı ve programlamada bir kodlama standardıdır. Bu ilke, aşağıda verilen beş ilkenin kısaltmasıdır…
1. Single Responsibility Principle (SRP)
2. Open/Closed Principle
3. Liskov’s Substitution Principle (LSP)
4. Interface Segregation Principle (ISP)
5. Dependency Inversion Principle (DIP) 

1.Single Responsibility Principle (SRP);
Bu ilke, “bir sınıfın değişmek için tek bir nedeni olması gerektiğini” belirtir, bu da her sınıfın tek bir sorumluluğu veya tek işi veya tek amacı olması gerektiği anlamına gelir.

2.Open/Closed Principle:
Bu ilke, "yazılım varlıklarının (sınıflar, modüller, işlevler, vb.) genişlemeye açık, ancak değişikliğe kapalı olması gerektiğini" belirtir; bu, bir sınıf davranışını değiştirmeden genişletebilmeniz gerektiği anlamına gelir.

3.Liskov’s Substitution Principle:
İlke 1987'de Barbara Liskov tarafından tanıtıldı ve bu ilkeye göre "Türetilmiş veya alt sınıflar, temel veya ebeveyn sınıflarının yerine geçmelidir". 
Bu ilke, bir ebeveyn sınıfının çocuğu olan herhangi bir sınıfın, herhangi bir beklenmedik davranış olmaksızın ebeveyni yerine kullanılabilir olmasını sağlar. 

4.Interface Segregation Principle:
Bu ilke, SOLID'de sınıflar yerine Arayüzler için geçerli olan ilk ilkedir ve tek sorumluluk ilkesine benzer.
Tek bir genel arayüz yerine birçok client arayüzünü tercih etmeli ve her arayüzün kendine özel bir sorumluluğu olmalıdır. 

5.Dependency Inversion Principle:
Bu ilkenin ana amacı, bağımlılıkları ayrıştırmaktır, böylece A sınıfı değişirse, B sınıfının değişiklikleri umursaması veya bilmesi gerekmez.

Yüksek seviyeli modüller/sınıflar, düşük seviyeli modüllere/sınıflara bağlı olmamalıdır. Her ikisi de soyutlamalara bağlı olmalıdır.
Soyutlamalar ayrıntılara bağlı olmamalıdır. Detaylar soyutlamalara bağlı olmalıdır. 

Örneğin;
Bir TV uzaktan kumanda pilinin gerçek hayattaki örneğini düşünebilirsiniz. Uzaktan kumandanızın bir pile ihtiyacı vardır ancak pil markasına bağlı değildir.





