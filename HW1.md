**1 – Neden NYP kullanmalıyiz? Başlica NYP dilleri nelerdir? (Why we need to use OOP? Some major OOP languages?)**

Nesne Yönelimli Programlama (NYP), kodu veriler etrafında yapılandırmak için "nesneler" (`objects`) ve "sınıflar" (`classes`) kullanarak programlamaya odaklanan bir yaklaşımdır. NYP'ye ihtiyaç duymamızın temel nedenleri şunlardır:

- **Karmaşıklığı Yönetme:** Karmaşık sistemleri daha küçük, yönetilebilir `object`'lere ayırarak sorun gidermeyi kolaylaştırır.
- **Yeniden Kullanılabilirlik:** Kalıtım (`inheritance`) sayesinde mevcut `class`'lara dayalı yeni `class`'lar oluşturarak kodun tekrar kullanılabilirliğini artırır.
- **Esneklik ve Uyarlanabilirlik:** Çok biçimlilik (`polymorphism`), farklı `object` türlerinin ortak bir üst sınıfın `object`'leri gibi ele alınabilmesini sağlayarak kodu daha az uzmanlaşmış ve daha uyarlanabilir hale getirir.
- **Modülerlik:** Ekiplerin aynı anda kodun farklı bölümleri üzerinde çalışmasına olanak tanır.
- **Bakım Kolaylığı:** Gerçek dünya nesnelerini modellemek, kodun daha okunabilir ve bakımı daha kolay olmasını sağlar.
- **Veri Güvenliği:** Kapsülleme (`encapsulation`), verileri ve metotları bir araya getirerek verilere doğrudan erişimi kısıtlar ve istenmeyen veri bozulmalarını önler.
- **Ölçeklenebilirlik:** NYP'nin esnekliği, yazılım sistemlerinin karmaşıklık arttıkça ölçeklenmesini kolaylaştırır.

Başlıca NYP dillerinden bazıları şunlardır: Java, Python, C++, C#, JavaScript, Ruby, PHP, Dart, Swift, Kotlin. Java, özellikle Android uygulama geliştirme ve kurumsal dünyadaki sağlamlığı ve güvenlik özellikleriyle öne çıkan en popüler NYP dillerinden biridir. Temel avantajlarından biri "bir kez yaz, her yerde çalıştır" (Write Once, Run Anywhere - WORA) özelliğidir.

**2 – Interface ve Abstract class arasindaki farklar nelerdir? (Interface vs Abstract class?)**

Hem `interface` hem de `abstract class`, Java'da soyutlamayı (`abstraction`) gerçekleştirmek için kullanılan mekanizmalardır. Temel farklar şunlardır:

| Özellik                | `Abstract Class`                                             | `Interface`                                                                                    |
| :--------------------- | :----------------------------------------------------------- | :--------------------------------------------------------------------------------------------- |
| Anahtar Kelime         | `abstract class`                                             | `interface`                                                                                    |
| Oluşturma              | Nesnesi doğrudan oluşturulamaz                               | Nesnesi doğrudan oluşturulamaz                                                                 |
| Metotlar               | Soyut (`abstract`) ve somut (uygulanmış) metotlar içerebilir | Java 8 öncesinde yalnızca soyut metotlar (Java 8 sonrası `default` ve `static` metotlar hariç) |
| Değişkenler            | Örnek değişkenleri içerebilir                                | Yalnızca `public static final` sabitleri içerebilir                                            |
| Yapıcı (`Constructor`) | Yapıcıya sahip olabilir                                      | Yapıcıya sahip olamaz                                                                          |
| Kalıtım                | Tek bir `abstract class`'ı genişletebilir (`extends`)        | Birden çok `interface`'i uygulayabilir (`implements`)                                          |
| Çoklu Kalıtım          | Doğrudan desteklemez                                         | Türün çoklu kalıtımını destekler                                                               |
| Erişim Belirteçleri    | `private`, `protected`, `public`, `static` olabilir          | Metotlar varsayılan olarak `public abstract`'tır                                               |
| `main()` metodu        | Olabilir                                                     | Olamaz                                                                                         |
| Amaç                   | Kod paylaşımı ve davranış tanımlama                          | Davranış sözleşmesi tanımlama                                                                  |

**Ne zaman `abstract class` kullanmalı?**

- Birkaç yakından ilişkili sınıf arasında kod paylaşmak istediğinizde.
- Alt sınıfların birçok ortak metodu veya alanı olmasını beklediğinizde veya `public` dışında erişim belirteçleri (`protected` ve `private` gibi) gerektiğinde.
- `static` olmayan veya `final` olmayan alanlar bildirmek istediğinizde.
- Bir grup alt sınıf için bir şablon sağlamak ve alt sınıfların kullanabileceği en azından bazı uygulama kodlarına sahip olduğunuzda.

**Ne zaman `interface` kullanmalı?**

- İlişkisiz sınıflar arasında ortak bir davranışı tanımlamak istediğinizde.
- Belirli bir veri türünün davranışını belirtmek istediğinizde, ancak kimin uyguladığıyla ilgilenmediğinizde.
- Türün çoklu kalıtımından yararlanmak istediğinizde.
- Diğer sınıfların kalıtım ağacındaki konumlarından bağımsız olarak oynayabileceği rolü tanımlamak için.
- Uygulayan sınıf tarafından tam bir uygulamanın sağlanmasını istediğinizde.

**3 – Neden `equals` ve `hashCode`'a ihtiyacimiz var? Ne zaman geçersiz kılmaliyiz? (Why wee need equals and hashcode? When to override?)**

- **`equals()` metodu:** İki nesnenin içeriklerinin mantıksal olarak eşit olup olmadığını kontrol etmek için kullanılır. `Object` sınıfındaki varsayılan uygulaması referans eşitliğini (bellekte aynı nesne olup olmadıklarını) kontrol eder.
- **`hashCode()` metodu:** Bir nesne için tamsayı bir karma kod değeri döndürür. Bu değer, `HashMap` ve `HashSet` gibi karma tabanlı koleksiyonlar tarafından nesneleri verimli bir şekilde depolamak ve erişmek için kullanılır.

**Neden İhtiyacımız Var?**

`HashMap` gibi koleksiyonlar, önce doğru "kova"yı bulmak için nesnenin `hashCode()` değerini kullanır ve ardından bu kova içindeki nesneleri karşılaştırmak için `equals()` metodunu kullanır. Bu, arama işlemlerini hızlandırır.

**`equals()` ve `hashCode()` Arasındaki Sözleşme:**

- Eğer iki nesne `equals()` metoduna göre eşitse, `hashCode()` metotları aynı tamsayı değerini döndürmelidir. Aksi takdirde, karma tabanlı koleksiyonlar düzgün çalışmayabilir.
- Eğer iki nesne `equals()` metoduna göre eşit değilse, `hashCode()` değerlerinin farklı olması gerekmez, ancak performans nedenleriyle farklı olması önerilir.

**Ne Zaman Geçersiz Kılmalıyız?**

- **`equals()`:** Nesneleri içeriklerine göre karşılaştırmak istediğinizde (varsayılan referans eşitliği yerine). Bu, özellikle "değer nesneleri" için önemlidir.
- **`hashCode()`:** `equals()` metodunu geçersiz kıldığınızda, sözleşmeyi korumak için `hashCode()` metodunu da geçersiz kılmalısınız. Eğer bir sınıfı `HashMap`, `HashSet` gibi karma tabanlı koleksiyonlarda anahtar olarak kullanmayı planlıyorsanız, her ikisini de geçersiz kılmak zorunludur.

**Örnek:**

```java
class Person {
    String name;
    int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        Person person = (Person) obj;
        return age == person.age && name.equals(person.name);
    }

    @Override
    public int hashCode() {
        return java.util.Objects.hash(name, age);
    }

    public static void main(Stringargs) {
        Person person1 = new Person("Ayşe", 30);
        Person person2 = new Person("Ayşe", 30);
        System.out.println(person1.equals(person2)); // Çıktı: true
        System.out.println(person1.hashCode() == person2.hashCode()); // Çıktı: true
    }
}
```

**4 – Java'da Elmas Problemi nedir? Nasil çözülür? (Diamond problem in Java? How to fix it?)**

Elmas problemi, bir sınıfın ortak bir atayı paylaşan iki veya daha fazla sınıftan (veya `interface`'den) miras alması ve bu atada aynı imzaya sahip bir metot tanımlanması durumunda ortaya çıkan bir belirsizliktir. Bu durum, kalıtım hiyerarşisinde elmas şeklini andırır (A -> B, A -> C, B+C -> D). Problem, D sınıfı A'da tanımlanan bir metodu çağırdığında ve B ile C bu metodu farklı şekillerde geçersiz kıldığında hangi metodun çağrılacağının belirsizleşmesidir.

**Java'da Çözümü:**

Java, `class`'lar için çoklu kalıtıma izin vermeyerek elmas problemini önler. Bir `class` aynı anda yalnızca bir üst sınıfı genişletebilir (`extends`).

Ancak Java, `interface`'ler aracılığıyla çoklu kalıtımı destekler. Java 8'den önce `interface`'ler metot uygulaması sağlamadığından, çakışan uygulamalar riski yoktu. Java 8'de eklenen varsayılan metotlar (`default methods`) ile bir `interface` içinde metot uygulaması sağlamak mümkün hale geldi.

Eğer bir `class`, aynı imzaya sahip çakışan `default method`'lara sahip birden çok `interface`'i uyguluyorsa (`implements`), derleyici bu belirsizliği gidermek için `class`'ın bu metodu geçersiz kılmasını ve hangi uygulamayı kullanacağını açıkça belirtmesini veya kendi uygulamasını sağlamasını (örneğin, `InterfaceName.super.methodName()` kullanarak) gerektirecektir. Bu açık çözüm, herhangi bir belirsizliği önler.

**Örnek:**

```java
interface A {
    default void selamVer() {
        System.out.println("A'dan selamlar!");
    }
}

interface B {
    default void selamVer() {
        System.out.println("B'den selamlar!");
    }
}

class C implements A, B {
    @Override
    public void selamVer() {
        A.super.selamVer(); // A interface'indeki selamVer metodunu çağırır
        // veya
        // B.super.selamVer(); // B interface'indeki selamVer metodunu çağırır
        System.out.println("C'den özel bir selam!");
    }

    public static void main(Stringargs) {
        C c = new C();
        c.selamVer();
    }
}
```

Bu örnekte, `C` sınıfı hem `A` hem de `B` `interface`'lerini uygular. Her iki `interface` de aynı imzaya sahip bir `default method` olan `selamVer()`'e sahiptir. `C` sınıfı bu metodu geçersiz kılarak hangi `interface`'in metodunu çağırmak istediğini açıkça belirtir.

**5 – Neden Çöp Toplayiciya ihtiyacimiz var? Nasil çalişir? (Why we need Garbage Collector? How does it run?)**

Çöp Toplayıcı (`Garbage Collector` - GC), Java'da artık kullanılmayan (ulaşılamayan) nesneler tarafından işgal edilen belleği otomatik olarak geri kazanan bir bellek yönetimi sürecidir. GC olmasaydı, program çalıştıkça bellek dolar ve sonunda `OutOfMemoryError` hatası alınırdı.

**Neden İhtiyacımız Var?**

- **Otomatik Bellek Yönetimi:** Geliştiricileri belleği manuel olarak ayırma ve serbest bırakma yükünden kurtarır. Bu, programcıların uygulama mantığına odaklanmasını sağlar.
- **Bellek Sızıntılarının Önlenmesi:** Kullanılmayan nesnelerden belleği otomatik olarak geri kazanarak bellek sızıntılarını önler.
- **Üretkenlik Artışı:** Geliştiriciler bellek yönetimiyle uğraşmak yerine kod yazmaya daha fazla zaman ayırabilir.
- **Uygulama Kararlılığı:** Bellek kaynaklı hataları azaltır.

**Nasıl Çalışır?**

Temel süreç şunları içerir:

1.  **İşaretleme (`Marking`):** GC, program tarafından hala ulaşılabilir olan nesneleri belirler. Bu işlem, "GC kökleri"nden (örneğin, yerel değişkenler, aktif iş parçacıkları, `static` değişkenler) başlayarak nesneler arasındaki referansları takip ederek yapılır. Ulaşılabilir nesneler "canlı" olarak işaretlenir.
2.  **Süpürme (`Sweeping`):** İşaretlenmemiş nesneler (ulaşılamayanlar) "çöp" olarak kabul edilir ve bu nesnelerin kullandığı bellek geri kazanılır.
3.  **Sıkıştırma (`Compacting` - İsteğe Bağlı):** Bazı GC algoritmaları, bellek parçalanmasını azaltmak için canlı nesneleri bir araya taşıyabilir. Bu, daha büyük bitişik boş bellek alanları oluşturur.

**Nesilsel Çöp Toplama (`Generational Garbage Collection`):**

Java'da yığın (`Heap`), nesnelerin ömrüne göre nesillere ayrılmıştır:

- **Genç Nesil (`Young Generation`):** Yeni oluşturulan nesneler bu alanda (Eden alanı) tutulur. Eden alanı dolduğunda, küçük bir çöp toplama işlemi (`Minor GC`) gerçekleşir. Canlı kalan nesneler Kurtulan alanlarına (`Survivor Spaces`) taşınır.
- **Yaşlı Nesil (`Old Generation` veya `Tenured Generation`):** Genç nesildeki birden fazla `Minor GC` işleminden sağ kurtulan nesneler bu alana taşınır. Bu alanda daha seyrek ve daha maliyetli büyük çöp toplama işlemleri (`Major GC` veya `Full GC`) gerçekleşir.

GC, JVM tarafından bellek azaldığında veya belirli eşiklere ulaşıldığında otomatik olarak tetiklenir. `System.gc()` veya `Runtime.getRuntime().gc()` metotları ile GC'yi tetiklemek mümkün olsa da, bunun hemen gerçekleşeceği garanti edilmez.

Java'da farklı çöp toplayıcı türleri bulunur (örneğin, Serial GC, Parallel GC, CMS GC, G1 GC, ZGC), her birinin farklı performans özellikleri ve kullanım senaryoları vardır. Örneğin, Serial GC tek bir iş parçacığı kullanırken, Parallel GC daha hızlı toplama için birden çok iş parçacığı kullanır. G1 GC ise büyük yığınlar için tasarlanmıştır ve düşük duraklama sürelerini hedefler.

**6 – Java `static` anahtar kelimesi kullanimi? (Java ‘static’ keyword usage?)**

Java'da `static` anahtar kelimesi, bir sınıfın herhangi bir örneğine (nesnesine) değil, doğrudan sınıfın kendisine ait olan üyeleri (değişkenler, metotlar, bloklar ve iç içe sınıflar) tanımlamak için kullanılır.

- **`static` Değişkenler (`Class Variables`):** Bir sınıfın tüm örnekleri arasında paylaşılan değişkenlerdir. Sınıf başına yalnızca bir kopyası bulunur. Sabitler (`constants`) veya nesne sayısını tutmak gibi durumlar için kullanılır.

  ```java
  class BenimSinifim {
      public static int nesneSayisi = 0;

      public BenimSinifim() {
          nesneSayisi++;
      }

      public static void main(Stringargs) {
          BenimSinifim nesne1 = new BenimSinifim();
          BenimSinifim nesne2 = new BenimSinifim();
          System.out.println(BenimSinifim.nesneSayisi); // Çıktı: 2
      }
  }
  ```

- **`static` Metotlar (`Class Methods`):** Nesne oluşturmaya gerek kalmadan doğrudan sınıf adı üzerinden çağrılabilirler. `static` metotlar, herhangi bir belirli nesne örneğiyle ilişkilendirilmedikleri için doğrudan örnek değişkenlerine (non-`static`) erişemezler. Yardımcı metotlar veya nesne durumundan bağımsız işlemler için kullanılırlar.

  ```java
  class Matematik {
      public static int kareAl(int sayi) {
          return sayi * sayi;
      }

      public static void main(Stringargs) {
          int sonuc = Matematik.kareAl(5);
          System.out.println(sonuc); // Çıktı: 25
      }
  }
  ```

- **`static` Bloklar:** Bir sınıf JVM'ye ilk yüklendiğinde yalnızca bir kez çalıştırılan kod bloklarıdır. `static` değişkenleri başlatmak veya sınıf için bir kerelik kurulum işlemleri yapmak için kullanılırlar.

  ```java
  class OrnekSinif {
      public static int sabitDeger;

      static {
          System.out.println("Statik blok çalıştı.");
          sabitDeger = 10;
      }

      public OrnekSinif() {
          System.out.println("Kurucu metot çalıştı.");
      }

      public static void main(Stringargs) {
          OrnekSinif nesne1 = new OrnekSinif();
          System.out.println("Sabit değer: " + OrnekSinif.sabitDeger);
      }
  }
  ```

- **`static` İç İçe Sınıflar (`Static Nested Classes`):** Bir iç içe sınıf `static` olarak bildirilebilir. Bu tür sınıflara, dış sınıfın bir örneği olmadan dış sınıf adı kullanılarak erişilebilir. Yalnızca dış sınıfın `static` üyelerine erişebilirler.

  ```java
  class DisSinif {
      static int disStaticDeger = 20;
      int disNonStaticDeger = 30;

      static class IcSinif {
          void yazdir() {
              System.out.println("Dış statik değer: " + disStaticDeger);
              // System.out.println("Dış non-statik değer: " + disNonStaticDeger); // Hata!
          }
      }

      public static void main(Stringargs) {
          DisSinif.IcSinif icNesne = new DisSinif.IcSinif();
          icNesne.yazdir(); // Çıktı: Dış statik değer: 20
      }
  }
  ```

**7 – Değişmezlik ne anlama gelir? Nerede, nasil ve neden kullanilir? (Immutability means? Where, How and Why to use it?)**

**Değişmezlik (`Immutability`)**, bir nesnenin durumu (verileri) oluşturulduktan sonra değiştirilememesi anlamına gelir. Değişmez bir nesne başlatıldıktan sonra, değerleri programın çalıştığı süre boyunca sabittir.

**Java'da Değişmez Sınıflar Oluşturma Kuralları:**

1.  Sınıfı `final` olarak bildirin. Bu, sınıfın alt sınıf oluşturulmasını engeller ve davranışının değişmeden kalmasını sağlar.
2.  Tüm veri üyelerini `private` ve `final` olarak ayarlayın. `private` erişimi kısıtlar, `final` ise değerlerinin yalnızca kurucu metotta bir kez atanabileceği anlamına gelir.
3.  Nesnenin durumunu değiştirebilecek herhangi bir `setter` metodu sağlamayın.
4.  Eğer sınıf değişken (mutable) nesneler içeriyorsa, kurucu metotta bu nesnelerin derin bir kopyasını (`deep copy`) oluşturarak atayın. Bu, değişmez nesnenin dışarıdan değiştirilebilen nesnelere referans tutmasını engeller.
5.  Alıcı (`getter`) metotlarda, eğer döndürülen alan değişken bir nesne ise, orijinal referansı döndürmek yerine bu nesnenin savunmacı bir kopyasını (`defensive copy`) döndürün. Bu, çağıran kodun alıcı metot aracılığıyla değişmez nesnenin iç durumunu değiştirmesini önler.

**Nerede Kullanılır?**

- Oluşturulduktan sonra durumunun değişmemesi gereken değer nesneleri için (örneğin, para birimi değerleri).
- Eşzamanlı programlamada iş parçacığı güvenliğini (`thread safety`) sağlamak için. Birden çok iş parçacığı, veri bozulması riski olmadan değişmez nesnelere güvenli bir şekilde erişebilir.
- `HashMap`'te anahtar (`key`) ve `HashSet`'te öğe olarak. Bir anahtarın durumu `HashMap`'e eklendikten sonra değişirse, harita bozulabilir.
- Önbellekleme (`caching`) amacıyla, değerleri sabit kaldığı için.
- Kullanıcı adları ve parolalar gibi hassas bilgileri depolamak için (güvenlik nedeniyle).

**Neden Kullanılır?**

- **İş Parçacığı Güvenliği:** Doğal olarak iş parçacığı güvenlidirler, senkronizasyona gerek duymazlar.
- **Basitlik:** Oluşturulması, test edilmesi ve kullanılması daha kolaydır çünkü her nesne yalnızca bir durumda bulunur.
- **Savunmacı Kopyalamaya Gerek Yok:** Birçok durumda savunmacı kopyalama ihtiyacını ortadan kaldırır.
- **Kimlik Mutasyonunu Önler:** Nesnenin kimliği (durumu) değişmez.
- **Önbellekleme Kolaylığı:** Değerleri sabit olduğu için önbellekleme daha kolaydır.
- **Daha Sağlam Kod:** Daha az hataya eğilimli kod yazılmasına yardımcı olur.

**Java'daki Değişmez Sınıf Örnekleri:**

`String`, sarmalayıcı sınıflar (`Integer`, `Boolean`, `Long` vb.), `BigInteger`, `BigDecimal`.

**Örnek (Basit Değişmez Sınıf):**

```java
final class BenimDegismezSinifim {
    private final String deger;

    public BenimDegismezSinifim(String deger) {
        this.deger = deger;
    }

    public String getDeger() {
        return deger;
    }

    // Setter metodu yok!
}
```

**8 – Kompozisyon ve Agregasyon ne anlama gelir ve aralarindaki farklar nelerdir? (Composition and Aggregation means and differences?)**

Hem **kompozisyon (`Composition`)** hem de **agregasyon (`Aggregation`)**, nesneler arasında bir "sahiptir" (`has-a`) ilişkisini temsil eden ilişki türleridir, yani bir nesne başka bir nesneyi içerir.

- **Kompozisyon:** Daha güçlü bir "sahiptir" ilişkisidir. Alt nesne, üst nesneden bağımsız olarak var olamaz. Eğer üst nesne yok edilirse, alt nesne de yok edilir. Bu, bütünün parçası olan ve parçanın münhasıran bütüne ait olduğu bir bütün-parça ilişkisidir. İçerilen nesnenin yaşam döngüsü, içeren nesnenin yaşam döngüsüne bağlıdır.

  **Örnek:** Bir `Ev` sınıfının `Oda` sınıfından nesneleri içermesi. Eğer `Ev` nesnesi yok edilirse, içindeki `Oda` nesneleri de o bağlamda var olmaktan çıkar.

- **Agregasyon:** Daha zayıf bir "sahiptir" ilişkisidir. Alt nesne, üst nesneden bağımsız olarak var olabilir. Üst nesne alt nesneye "sahiptir", ancak alt nesne başka üst nesnelerle de ilişkilendirilebilir veya kendi başına var olabilir. İçerilen nesnenin, içeren nesneden bağımsız kendi yaşam döngüsü vardır.

  **Örnek:** Bir `Bölüm` sınıfının `Öğrenci` sınıfından nesneleri içermesi. Eğer `Bölüm` dağılırsa, `Öğrenci` nesneleri hala var olmaya devam eder ve başka bölümlere katılabilir.

**Temel Fark:** Bağımlılık ve yaşam döngüsüdür. Kompozisyonda, alt nesnenin yaşam döngüsü üst nesneye bağlıyken, agregasyonda bağımsızdır. Kompozisyon genellikle "parçasıdır" veya "sahibidir" gibi ifadelerle temsil edilen daha güçlü bir ilişkiyi ifade ederken, agregasyon "sahiptir" veya "kullanır" gibi bir ilişkiyi gösterir.

**Java Kod Örnekleri:**

**Kompozisyon:**

```java
class Adres {
    String cadde;
    String sehir;

    public Adres(String cadde, String sehir) {
        this.cadde = cadde;
        this.sehir = sehir;
    }
}

class Ev {
    Adres adres; // Kompozisyon: Evin bir Adresi olmalı ve Adres Ev olmadan anlamlı değil.

    public Ev(String cadde, String sehir) {
        this.adres = new Adres(cadde, sehir);
    }
}
```

**Agregasyon:**

```java
class Ders {
    String dersAdi;

    public Ders(String dersAdi) {
        this.dersAdi = dersAdi;
    }
}

class Ogrenci {
    String ogrenciAdi;
    Ders aldigiDers; // Agregasyon: Öğrencinin aldığı bir Ders olabilir, ancak Ders Öğrenciden bağımsız olarak var olabilir.

    public Ogrenci(String ogrenciAdi) {
        this.ogrenciAdi = ogrenciAdi;
    }

    public void dersAl(Ders ders) {
        this.aldigiDers = ders;
    }
}

public class Main {
    public static void main(Stringargs) {
        Ders matematik = new Ders("Matematik");
        Ogrenci ali = new Ogrenci("Ali");
        ali.dersAl(matematik); // Ali Matematik dersini alıyor. Matematik dersi Ali'den bağımsız olarak da var olabilir.
    }
}
```

**9 – Kohezyon ve Bağlanti ne anlama gelir ve aralarindaki farklar nelerdir? (Cohesion and Coupling means and differences?)**

**Kohezyon (`Cohesion`)** ve **Bağlantı (`Coupling`)**, iyi bir yazılım tasarımının önemli prensipleridir.

- **Kohezyon:** Bir modül (örneğin, bir sınıf) içindeki elemanların (metotlar, değişkenler) ne kadar bir arada ve birbiriyle ilişkili olduğunu ifade eder. **Yüksek kohezyon**, bir modülün tek bir, iyi tanımlanmış bir sorumluluğa odaklandığı anlamına gelir. Yüksek kohezyona sahip sınıfların anlaşılması, bakımı ve yeniden kullanılması daha kolaydır.

  **Örnek (Yüksek Kohezyon):** Yalnızca kullanıcı kimlik doğrulamasını (`user authentication`) işlemekten sorumlu bir sınıf.

  **Örnek (Düşük Kohezyon):** Hem kullanıcı kimlik doğrulamasını hem de veritabanı işlemlerini işleyen bir sınıf.

- **Bağlantı:** Farklı modüller (örneğin, sınıflar) arasındaki karşılıklı bağımlılık derecesini ifade eder. **Düşük bağlantı**, modüllerin birbirleriyle iyi tanımlanmış `interface`'ler aracılığıyla etkileşen nispeten bağımsız olduğu anlamına gelir. Düşük bağlantıya sahip sistemlerin değiştirilmesi ve bakımı daha kolaydır çünkü bir modüldeki bir değişiklik diğerlerini etkileme olasılığı daha düşüktür. **Yüksek bağlantı**, modüllerin birbirlerine sıkı sıkıya bağlı olduğu, genellikle birbirlerinin iç detaylarına doğrudan eriştiği anlamına gelir. Bu durum, sistemin bakımını ve değiştirilmesini zorlaştırır.

  **Örnek (Düşük Bağlantı):** İki sınıfın yalnızca birbirlerine parametreler aracılığıyla veri geçirmesi ve iyi tanımlanmış metotlar aracılığıyla iletişim kurması.

  **Örnek (Yüksek Bağlantı):** Bir sınıfın başka bir sınıfın iç değişkenlerine veya metotlarına doğrudan erişmesi.

**Temel Fark:** Kohezyon bir modülün içindeki elemanların ilişkisini ifade ederken, bağlantı farklı modüller arasındaki bağımlılık derecesini ifade eder. İyi bir yazılım tasarımında yüksek kohezyon ve düşük bağlantı hedeflenir.

**10 – Heap ve Stack ne anlama gelir ve aralarindaki farklar nelerdir? (Heap and Stack means and differences?)**

Java'da bellek yönetimi için kullanılan iki temel alan **Yığın (`Heap`)** ve **Bellek (`Stack`)**'tir.

| Özellik                     | Yığın (`Heap`)                                 | Bellek (`Stack`)                                                                  |
| :-------------------------- | :--------------------------------------------- | :-------------------------------------------------------------------------------- |
| Kullanım Amacı              | Dinamik bellek yönetimi                        | Statik bellek yönetimi                                                            |
| Depolanan Veri              | Nesneler (`objects`) ve örnek değişkenleri     | Yerel değişkenler (`primitive` ve referanslar), metot parametreleri, çağrı yığını |
| Yönetim                     | Çöp Toplayıcı (`Garbage Collector`) tarafından | JVM tarafından otomatik                                                           |
| Bellek Ayırma Hızı          | Yavaş                                          | Hızlı                                                                             |
| Bellek Serbest Bırakma Hızı | Otomatik                                       | Otomatik                                                                          |
| Boyut                       | Genellikle daha büyük                          | Genellikle daha küçük                                                             |
| Paylaşım                    | Tüm iş parçacıkları arasında paylaşılır        | Her iş parçacığı için özel                                                        |
| Yaşam Süresi                | Uygulama çalışana kadar                        | Metot çalışana kadar                                                              |

**Özet:**

- **Yığın:** Nesnelerin ve bunlara karşılık gelen verilerin saklandığı, tüm iş parçacıkları tarafından paylaşılan bir bellek alanıdır. Bellek yönetimi GC tarafından yapılır.
- **Bellek:** Her iş parçacığına özel olan, yerel değişkenlerin, metot parametrelerinin ve metot çağrılarının bilgisinin saklandığı bir bellek alanıdır. Bellek yönetimi hızlı ve otomatiktir (metotlar tamamlandığında bellek serbest bırakılır).

**11 – Exception ne anlama gelir? Exception türleri nelerdir? (Exception means? Type of Exceptions?)**

**İstisna (`Exception`)**, bir programın yürütülmesi sırasında normal talimat akışını bozan bir olaydır. Java, bu istisnai durumları ele almak için bir mekanizma sağlar.

**İstisna Türleri:**

1.  **Kontrollü İstisnalar (`Checked Exceptions`):** Derleyicinin ele almaya zorladığı istisnalardır. Bu istisnalar, programın normalde düzgün bir şekilde çalışmasını engelleyebilecek, ancak programcı tarafından öngörülebilir ve ele alınabilir durumları temsil eder (örneğin, dosya okuma/yazma sırasında oluşabilecek `IOException`, veritabanı işlemleri sırasında oluşabilecek `SQLException`). Bu tür istisnaları ele almak için `try-catch` blokları kullanılmalı veya metot imzasına `throws` anahtar kelimesi eklenerek sorumluluk çağıran metoda devredilmelidir.

    **Örnek:**

    ```java
    import java.io.FileReader;
    import java.io.IOException;

    public class CheckedExceptionOrnegi {
        public static void main(Stringargs) {
            try {
                FileReader file = new FileReader("olmayan_dosya.txt");
                // Dosya işlemleri...
                file.close();
            } catch (IOException e) {
                System.out.println("Bir G/Ç hatası oluştu: " + e.getMessage());
            }
        }
    }
    ```

2.  **Kontrolsüz İstisnalar (`Unchecked Exceptions` veya `Runtime Exceptions`):** Derleyicinin ele almaya zorlamadığı istisnalardır. Bu istisnalar genellikle programdaki mantık hatalarını veya programcının hatası olarak kabul edilen durumları gösterir (örneğin, `NullPointerException` (null bir nesneye erişmeye çalışma), `ArrayIndexOutOfBoundsException` (geçersiz bir dizi indeksine erişme), `ArithmeticException` (sıfıra bölme)). `Error`'lar (örneğin, `OutOfMemoryError`, `StackOverflowError`) da kontrolsüz istisna türüdür ancak genellikle kurtarılması zor veya imkansız olan daha ciddi sistem sorunlarını temsil ederler.

    **Örnek:**

    ```java
    public class UncheckedExceptionOrnegi {
        public static void main(Stringargs) {
            String metin = null;
            try {
                System.out.println(metin.length()); // NullPointerException oluşur
            } catch (NullPointerException e) {
                System.out.println("Bir null referans hatası oluştu: " + e.getMessage());
            }

            intsayilar = {1, 2, 3};
            try {
                System.out.println(sayilar[5]); // ArrayIndexOutOfBoundsException oluşur
            } catch (ArrayIndexOutOfBoundsException e) {
                System.out.println("Dizi sınırları dışı hatası: " + e.getMessage());
            }
        }
    }
    ```

**12 – 'Temiz Kod'u nasil olabildiğince kisa özetleyebiliriz? (How to summarize ‘clean code’ as short as possible?)**

'Temiz Kod', okunması, anlaşılması ve bakımı kolay, iyi yapılandırılmış ve anlamlı kod yazma pratiğidir. Temel prensipleri şunlardır:

- **Anlamlı İsimlendirme:** Açık ve açıklayıcı isimler kullanın.
- **Küçük Fonksiyonlar:** Fonksiyonları kısa ve tek bir işe odaklı tutun.
- **Tekrarı Önleyin (DRY):** Kodu tekrar etmeyin.
- **Test Yazın:** Kodunuzu test edin.
- **Kodlama Standartlarına Uyun:** Tutarlı olun.
- **Basit Tutun (KISS):** Karmaşıklıktan kaçının.
- **Yorumlar Neden'i Açıklamalı:** Kodun amacını açıklayın.
- **Tutarlı Biçimlendirme:** Okunabilirliği artırın.
- **Hataları Düzgün Yönetin:** İstisnaları ele alın.

**13 – Java'da gizleme metodu nedir? (What is the method of hiding in Java?)**

Java'da **metot gizleme (`Method Hiding`)**, bir alt sınıfın üst sınıfındaki aynı imzaya (isim ve parametre türleri) sahip `static` bir metodu bildirdiğinde meydana gelir. Alt sınıftaki metot, üst sınıftaki metodu gizler.

**Temel Farklar (Metot Gizleme vs. Metot Geçersiz Kılma (`Method Overriding`)):**

| Özellik          | Metot Gizleme (`Method Hiding`)                                                                 | Metot Geçersiz Kılma (`Method Overriding`)                                                                   |
| :--------------- | :---------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------- |
| Uygulanabilirlik | `static` metotlar için                                                                          | Örnek (`non-static`) metotlar için                                                                           |
| Çözümleme        | Derleme zamanında referans değişkeninin türüne göre çözülür                                     | Çalışma zamanında nesnenin gerçek türüne göre çözülür                                                        |
| İmza             | Aynı isim ve parametre türleri gereklidir; dönüş türü farklı olabilir                           | Aynı isim, parametre türleri ve (Java 5'ten beri covariant dönüş türleri izin verilir) dönüş türü gereklidir |
| Amaç             | Üst sınıf türünde bir referans üzerinden alt sınıfın `static` metodunun çağrılmasını engellemek | Alt sınıfın üst sınıftan miras aldığı bir metodun özel bir uygulamasını sağlamak                             |

**Örnek:**

```java
class UstSinif {
    public static void mesajYaz() {
        System.out.println("Üst sınıftan statik mesaj.");
    }
}

class AltSinif extends UstSinif {
    public static void mesajYaz() {
        System.out.println("Alt sınıftan statik mesaj.");
    }
}

public class Main {
    public static void main(Stringargs) {
        UstSinif ustReferans = new AltSinif();
        ustReferans.mesajYaz(); // Çıktı: Üst sınıftan statik mesaj. (Alt sınıfın metodu gizlenir)

        AltSinif altNesne = new AltSinif();
        altNesne.mesajYaz(); // Çıktı: Alt sınıftan statik mesaj.

        UstSinif.mesajYaz(); // Çıktı: Üst sınıftan statik mesaj.
        AltSinif.mesajYaz(); // Çıktı: Alt sınıftan statik mesaj.
    }
}
```

Bu örnekte, `AltSinif`'taki `mesajYaz()` metodu, `UstSinif`'taki aynı isim ve imzaya sahip `static` metodu gizler. `UstSinif` türünde bir referans üzerinden çağrıldığında, `UstSinif`'taki metot çalışır.

**14 – Java'da soyutlama ve çok biçimlilik arasindaki fark nedir? (What is the difference between abstraction and polymorphism in Java?)**

**Soyutlama (`Abstraction`)** ve **Çok Biçimlilik (`Polymorphism`)**, Nesne Yönelimli Programlamanın temel kavramlarıdır, ancak farklı amaçlara hizmet ederler.

- **Soyutlama:** Karmaşık uygulama detaylarını gizleme ve kullanıcıya yalnızca temel bilgileri gösterme sürecidir. Bir nesnenin "nasıl" yaptığı yerine "ne" yaptığına odaklanır. Java'da `abstract class`'lar ve `interface`'ler soyutlamayı gerçekleştirmenin temel yollarıdır.

  **Örnek:** `draw()` adında soyut bir metodu olan soyut bir `Shape` sınıfı. Çizimin özel uygulaması (örneğin, bir dairenin nasıl çizileceği, bir dikdörtgenin nasıl çizileceği) somut alt sınıflara (`Circle`, `Rectangle`) bırakılır.

- **Çok Biçimlilik:** Bir nesnenin birçok biçime bürünebilme yeteneğidir. Java'da bu genellikle metot geçersiz kılma (`runtime polymorphism`) ve metot aşırı yükleme (`compile-time polymorphism`) yoluyla elde edilir. Bir üst sınıf türündeki bir referans değişkeni, alt sınıflarından herhangi birinin bir nesnesine başvurabilir ve çalışma zamanında doğru (geçersiz kılınan) metot çağrılır.

  **Örnek:** `makeSound()` adında sanal (virtual) bir metodu olan bir `Animal` üst sınıfı ve bu metodu farklı sesler üretmek için geçersiz kılan `Dog` ve `Cat` gibi alt sınıflar. `Animal` türünde bir referansa bir `Dog` nesnesi atandığında `makeSound()` çağrıldığında köpeğin sesi duyulur, aynı şekilde bir `Cat` nesnesi atandığında kedinin sesi duyulur.

**Temel Farklar:**

| Özellik   | Soyutlama (`Abstraction`)                                        | Çok Biçimlilik (`Polymorphism`)                                                                                          |
| :-------- | :--------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------- |
| Odak      | Karmaşıklığı gizlemekle ilgilidir                                | Farklı biçimlere bürünebilme ve farklı davranışlar sergileme yeteneğiyle ilgilidir                                       |
| Mekanizma | `abstract class`'lar ve `interface`'ler aracılığıyla elde edilir | Kalıtım (`inheritance`) ve metot geçersiz kılma/aşırı yükleme (`method overriding/overloading`) aracılığıyla elde edilir |
| Amaç      | Temel özelliklere ve davranışlara odaklanır                      | Farklı sınıflardaki nesnelerin aynı metot çağrısına kendi yollarıyla yanıt verme yeteneğine odaklanır                    |
