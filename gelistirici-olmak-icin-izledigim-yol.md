# Geliştirici olmak için izlediğim yol

title: "Geliştirici olmak için izlediğim yol"\
source: https://www.gurkanucar.com/java-gelistirici-olmak-icin-izledigim-yol/\
date: 2025-05-11 12:51\
tags:\
description:

[source](https://www.gurkanucar.com/java-gelistirici-olmak-icin-izledigim-yol/)

## Geliştirici olmak için izlediğim yol

By [gurkanucar](https://www.gurkanucar.com/author/gurkanucar/) --- 30 Mar 2025

![image](https://lh7-rt.googleusercontent.com/slidesz/AGV_vUfbA-ajbOkPXOJEg00ji6URu6DoAhE1NIWRQ1-oTFmwuOe_u-ZmE3wg9gubOUV-67U5TVrvaI8DOXkBWzzxcL0sbfad-aazOYBnFrFfvyqxz5S1t7ebGP0NGQca-Leh4xoVg_O77DLfdlj8rxxerlGfnTW7n3rX=s2048?key=7ILbDBUGZmjGymoNg9zu8g)

Zaman zaman birileriyle sohbet ederken "Nasıl geliştirici olunur?", "Zaten geliştiriciyim ama kendimi nasıl daha iyi bir noktaya taşırım?" gibi sorular geliyor. Bu yazıda doğrudan bu sorulara cevap vermektense, kendi yolculuğumu, yaptığım hataları, doğruları ve yanlışları paylaşmak istiyorum. Anlatacaklarım bu konu hakkında fikir edinmenize yardımcı olacaktır diye umuyorum.

‼️

**Ufak bir not:** Burada paylaştığım şeyler **kesinlikle bir tavsiye değil**. Sadece kendi deneyimlerimi ve düşüncelerimi anlatıyorum. Lütfen söylediklerimi mantık süzgecinden geçirip, sadece **sana uygun olanları ciddiye al**. Bir şekilde hayatını olumsuz etkilemek beni gerçekten üzer.

***

**Asıl amacım yazılımı öğrenmek değil, yazılım ile sorun çözebilmekti**

Öncelikle yazılıma başlama amacım, **yazılımcı olmak değil** de aklımdaki bir **sorunu bilgisayar yardımı ile çözüp hayata geçirebilmekti**. Yazılım; bunu yapabilmem için sadece bir araç görevi görüyordu. Örnek olarak **Visual Basic 6.0** ile yaptığım ilk uygulamalardan birisi, fizik dersindeki formülleri hesaplamaya yarıyordu.

![](https://www.gurkanucar.com/content/images/2025/03/image-6.png)

![](https://www.gurkanucar.com/content/images/2025/03/image-7.png)

![](https://www.gurkanucar.com/content/images/2025/03/image-8.png)

Daha sonra öğrendiğim Arduino ve C# ile geliştirdiğim uygulamalar da, uzaktan kumandalı aracı bilgisayardan kontrol etmeye yarıyordu.

https://www.youtube.com/embed/4sOEtwX8lOw?feature=oembed"\[]%%\
Dolayısıyla, yazılım öğrenmedeki motivasyonumuz problem çözebilmek üzerine olmalı. Aksi takdirde yazılımı sırf öğreneyim, para kazanayım kafasıyla öğrendiğinizde hem ilerlemek çok sancılı oluyor hem de gerekli özeni göstermediğinizden süreç uzuyor.

Kendi günlük hayatınızda kullanabileceğiniz basit yazılım projeleri:

* Url Kısaltıcı
* Doğumgünü, özelgün vs hatırlatıcı
* Komik paylaşımları, capsleri tutabileceğiniz bir veritabanı
* Şifrelerinizi saklayabileceğiniz bir platform

***

**Her şeyden azar azar ama hiçbirinden tam değil**

Bu süreçte yaptığım yanlışlardan ilki, birşeyi tam öğrenmeden yeni bir dile geçmekti. Örneğin Visual Basic de for-while döngüsü, if-else'i vs öğrenir hemen yeni bir dile geçerdim. Sonra da yine başka bir dile. OOP, class falan hak getire. Daha da vahim olanı, ben if-else, for-while döngüsü yazabildiğim her dili bildiğimi kabul ederdim. Frameworkler vs hakkında en ufak bir fikrim yoktu. En fazla yapabildiğim; txt, SQLite veya AccessDB ye veri yazıp okumaktı.

Şu an geriye dönü baktığımda önce X dilinin her şeyini, ayrıntılarını öğrenir daha sonra başka dillere/platformlara geçerdim. Bir alanda uzman olmak, diğer alanlarda da nasıl ilerlemeniz gerektiği hakkında hem size fikir vermekte hem de daha kolay platform değiştirmenize olanak sağlamakta.

***

**Yazılım araba sürmek gibidir. Hangi marka olursa olsun direksiyon, gaz, fren hep vardır. Sadece yerleri, konforu ya da tasarımı değişir.**

Frontend/mobil alanında kariyerlerinde ilerleyen arkadaşların bunu nispeten gözlemlemesi zor olsa da, backend geliştiren arkadaşlar bir süre sonra şunu farkedecekler:

Siz java da yazsanız, node js de yazsanız, python da yazsanız istisnasız hepsinde:

* CRUD (create, read, update, delete) işlemleri var. Zaten yazılımın büyük çoğunluğu business rules (iş kuralı) a göre değişen crud operasyonları. Bunu da öğrenmek için yapılabilecek en mantıklı şey içerisinde 1-1, 1-n, n-m tablo ilişkileri bulunan bir proje yapmak.
* Controller (route, api), istekleri karşılayan ana yapı. GET, POST, PUT, DELETE methodlarının kod syntaxı olarak yazılışı farklı sadece. Hepsinde path variable, request parameter vs ortak olarak var.
* Api validations yine tüm dillerde mevcut. Bazılarında şema objesi (node js express) üzerinden oluyor, bazılarında anotasyon (java) ile.
* Loglama, Swagger/OpenAPI (koddaki yazdığınız apileri tarayıp bulan ve deneme yapmanızı kolaylaştıran dokuman aracı) hepsinde mevcut.
* Exception handling de yine tüm platformlarda ortak, olması gereken bir yapı.
* Authentication-Authorization (Kimliklendirme ve Rol Yetkisi), JWT token artık defacto olmuş ve projelerin yüzde 90'ı bu standartı kullanıyor. Ek olarak OAUTH2 gibi standartları kullananlar da oldukça yaygınlaştı. Neredeyse tüm diller/platformlar için kütüphanesi var.

Buradan çıkartacağımız sonuç; bir dil için yukarıdaki özelliklere sahip full+full paket bir proje yaptığınızda herhangi bir X platformuna geçip aynı şeyleri orada da uygulamanız çok basit.

***

**Öğrenciyken paranın miktarını önemsemek**

Geriye dönüp baktığımda gözlemlediğim bir diğer hatam; paraya, deneyim kazanmaktan daha fazla öncelik vermekti. Üniversite 1. sınıfta pandeminin de araya girip okulların uzaktana dönmesi sebebiyle evde iyice canım sıkılmaya başlamıştı. Yine yukarıda belirttiğim döngüdeki gibi azıcık ondan azıcık şundan, for döngüsü, if-else falan yazar sonra da yeni dile geçerdim. Bu da bana her şeyi biliyormuşum ve işe hazırmışım gibi bir özgüven vermişti. Üniversiteden hocam ile tanıştıktan sonra kendisine staj yapabileceğim bir yer arayışında olduğumu söylemiştim. O da sağolsun tanıdığı tecrübeli ve startup sahibi olan bir abi ile tanışmama ve sonrasında staja başlamama vesile olmuştu.

Staja başladığımda düşük bir ücretle başlamıştım ve çevremden bazı staja başlayan arkadaşlardan da benden yüksek farklı rakamlar duyuyordum. Bu motivasyonumu çok düşürüyordu. Halbuki çok şey öğreniyordum bir de üstüne para alıyordum fakat bunu o zaman için akıl edemiyordum. Aslında işletme açısından düşünecek olursak da ortada haksız bir durum yoktu. Şu an kendimi sorguluyorum ve diyorum ki acaba kendi iş yerim olsa, yalnızca ufak bir kaç bişey bilen bir üniversite 1. sınıf öğrencisini alsam ne kadar para verirdim diye. Bence öğrenci/stajyer iken düşük ücretlere morali bozulan arkadaşlar kendilerini işletmenin sahibi yerine koymalı ve tekrar düşünmeli. **Para yerine edindiği tecrübeden motive olmalı.** Fakat **mezun olduktan ve 1,2 sene tecrübe kazandıktan sonra** kendinizi elbetteki **piyasanın altında konumlandırmamalı** ve hakkınızı aramalsınız. Çünkü o işi artık profesyonel olarak icra ediyorsunuz.

![Staj yapmaya başladığım 2021 senesinden günümüze net maaşlarım - 2023 ilk maaşım (gerçek rakamlar arasında ufak farklar mevcuttur - son maaşlarımı içermemektedir)](https://www.gurkanucar.com/content/images/2025/04/image-2.png)

***

**İşverenlerin gözünde topluluklarda rol almak çok da önemli olmayabilir**

Üniversitede okurken bazı topluluklarda yer aldım, eğitim verdim. Bunlardan üniversiteye ait topluluklar da vardı, üniversite dışından olan da. Aralarında en çok verim ardığım şüphesiz ki üniversite dışından olan, Hollanda ve Almanyadaki Türk yazılımcı abilerin kurmuş olduğu **FolksDEV** topluluğu idi.

Topluluklardan bazı arkadaşlar, üniversiteden mezun olup iş hayatına girdğinde konuşmacı olarak etkinliklere katılırlardı. Çoğunun söylediği, **toplulukta idari görev yapmanın iş hayatında pek bir karşılığı olmadığı**ydı. Burada geriye dönüp baktığımda mantıklı bulduğum konu; **sırf topluluğa girmiş olmak için girmek yerine o toplulukta kendi mesleki gelişimimi artıracak roller almak ve o topluluğu network aracı olarak kullanmak** oldu\*\*.\*\* Tavsiyem, bu topluluklarda **boşa vakit harcamayın**. Eğer size bir şey katmıyorsa boşuna idari roller almayın, teknik roller üstlenin, mesleki anlamda kendinizi projeler/staj yaparak geliştirin veya okul dışında sektörden insanların oluşturduğu topluluklara katılıp gerçek network edinin.

Önerebileceğim bazı topluluklar: **FolksDEV**, Turkey Java Community, Devnot, Java Users Group

***

**Hiç bir zaman, çok çalıştım ve bunun kesinlikle karşılığı olacak diye bir yanılgıya düşmedim**

Linkedin'de bazı serzeniş postları görüyorum. Adam paylaşıyor, youtube daki tutorial dan bakarak html-css-js website tasarlamış ve diyor ki "Aylardır proje yapıyorum hala iş yok". Başka birisi; react ile inmemory çalışacak, api bile çağırmayan proje yapmış yine aynı serzenişi söylüyor. Kendi fikrimce buradaki en büyük yanılgı, sektörün ihtiyacı olmayan bir şeyi öğrenmeye vakit ayırıp karşılık aramak. Eğer millet react ile next js ile api'ye istek atıp işlemler yapıyor, login logout jwt mekanizması ekliyor, next js, supabase vs ile uçup kaçarken; sen gidip de html-css-js ile 6 aydır proje yapıyorum iş yok dersen sana "..... git" derler.

Burada kilit konu sektörden arkadaşlar edinip veya üniversiteden hocalara danışıp hangi teknolojinin sektörde tercih edildiğini öğrenmek. Ek olarak hocalara danışma meselesinde de dikkat etmek gerek. Çünkü akademi ile gerçek hayattaki durumlar çoğu zaman birbiri ile örtüşmüyor. Aksi takdirde halen visual basic yazan bir hoca sektörde java kullanılmıyor diyebilir ve hayatınızı yanlış etkileyebilir.

Sonuç olarak çalışmanın her zaman karşılığını alacağını beklemek yerine yaptığımız çalışma doğru mu diye sorgulayıp ilerlemek daha güzel bir yöntem olabilir.

***

**Yetiştirilmek üzere iş arıyorum**

Bir diğer mantıksız bulduğum olay Linkedin'de **"Selam X üniversitesi mezunuyum, Y alanında yetiştirilmek üzere iş/staj arıyorum."** diyerek yapılan paylaşımlar.

Sevgili arkadaşım, kendini bir işveren yerine koy ve birinin sana gelip "abi/abla ben sana muhtacım, **yetiştirilmek üzere** iş arıyorum ama bana para da vermelisin, üstüne ben işi öğrendikten 1 sene sonra maaşı beğenmeyip seni bırakıp gideceğim ve tecrübe ile kazandığım para da yanıma kar kalacak" dese, nasıl cevap verirdiniz? Adama sorarlar 4 sene boyunca okulda ne yaptın diye. Böyle bir durumdaki arkadaşın iş bulma olasılığı çok düşük.

> **Almadan vermek, Allah'a mahsustur**\
> (bir işveren atasözü)

Burada kendimce yapılabilecek en mantıklı hareket öncelikle bir çok proje geliştirip **işverenin karşısına dolu dolu çıkabilmek.** Bir şeyler yapabildiğinizi göstermek. Elbetteki **işveren yeni mezundan çok bir şey bekleyemez** ama hiç bir şey bilmeyen bir adama da para vermek sizce ne kadar doğru?

**İlk işe/staja girmeyi kolaylaştırmak için alınabilecek aksiyonlar:**

* İş/Staj deneyimi olmasa bile sürekli **projeler yapıp** **github** da paylaşmak. Eğer proje geliştirme konusunda eksiğiniz var ise **youtube dan tutorial** izleyip aynılarını yapmak. Eğer biraz kendinizi geliştirdiyseniz X Clone, Y Clone gibi projeler yapıp bunlara **kendinizden bir şeyler katmak**.
* Üniversite boş diyenlere aldırmayıp; üniversitedeki arkadaşlarınızın, üst dönemlerin, topluluktan tanıştığınız kişilerin veya hocalarınızın networkü aracılığı ile iş aramak.
* İlk işleriniz için maaş beklentinizi düşük tutmak. **Bu demek değil ki ileride de maaşım düşük olacak.** Çoğunluğun 35-40 bin istedigi yerde 25-30 civari isterseniz işe girme olasılığınız artabilir.
* Üniversite birinci sınıftan itibaren staja başlayıp deneyim kazanmak.
* Eğer Linkedin'den iş arayışınızı paylaşacaksanız kesinlikle ilgilenene cv mi iletirim falan yazmayın. Direkt cv nizi, bilgilerinizi paylaşıma ekleyin. **İnsan kaynaklarının size ulaşmasını kolaylaştırın.** İnsan kaynakları ve müdür poziyonundaki kişileri ağınıza ekleyin. Asla "yetiştirilmek üzere" ifadesini kullanıp kendinizi işverene karşı güçsüz göstermeyin.
* İnternetten mülakat sorularına çalışmanız mülakatın iyi geçme olasılığını artırır. Ek olarak her mülakattan çıktıktan sonra bilmediğiniz konuları, soruları vs not alın.
* Direkt firmalarin bünyesine girmektense dış kaynak olarak işe başlayıp zaman içerisinde firmaya geçmeyi deneyin. Burada önerebileceğim daha önce çalıştığım iki firma var. Biri **metasis** diğeri **experilabs**. Çalışmadığım fakat adını sıkça duyduğum yerler ise: RDC, OBSS, Infonal, Mirsis. (not: reklam degildir, benim iyi deneyim yasamam sizin de iyi deneyim yasayacaginizi garanti etmez.)
* Medium da öğrendiğiniz bilgileri makale şeklinde paylaşın. Yaptığınız projeleri, yazdığınız makaleleri Linkedin'de paylaşın.

***

**Kurumsalda değil, startup da işe başlamak**

Geriye dönüp baktığımda yaptığım en mantıklı hareket neydi diye soracak olursanız, muhtemelen bu derdim. **İlk işinize startup da başladığınızda**; production ortamının database şifresi de dahil olmak üzere bir çok konuda bilgi sahibi olur, bir **çok farklı alanda çalışmalar yaparsınız.** Bu sayede **büyük resmi görebilme imkanı**nız da olur.

![image](https://www.gurkanucar.com/content/images/2025/04/image-1.png)

Eğer **ilk işinize kurumsalda başlarsanız** muhtemelen çok **büyük bir organizasyonun ufak bir parçası** olacaksınız. Gidip de X, Y, Z ihtiyacınız olduğunda bunu siz değil bunun için özel olarak ayrılan ekipler yapacak ve siz **arkada ne olup bittiğinin farkına bile varmayacaksınız**.

> ölümü gösterip sıtmaya razı etmek (!)

Startup da ilk işe başlamanın bir diğer artısı da; yoğun tempoya alışıp kurumsal firmaya geçtiğinizde rahatlama yaşayacak olmanız. Diyeceksiniz ki adamlar ne basit tasklara kaç günlük eforlar veriyor. O taskları havada karada yapacaksınız. Farkınızı emin olun göstereceksiniz. Bir de olduğunuz yerden çok yüksek ihtimalle memnun olup bir daha startup a geçmeyi falan düşünmeyeceksiniz. Ama ilk defa kurumsalda işe başlayan arkadaşlar muhtemelen sahip oldukları nimetin farkında olmadığından mutsuz olacaklar. Belki de daldan dala ufak paralar için atlayacaklar.

***

**Bunları her geliştirici alanından bağımsız olarak temel bir şekilde bilmeli**

Aşağıda yazacağım konulara bu yazıda değinmeyeceğim. Alttaki konuların gerek mobil, gerekse backend, frontend vs herkesin bilmesi gerektiğini düşünüyorum.

* Temel Network bilgisi, IP, Domain, DNS, HTTP, HTTPS, SSL
* Backend, frontend vs kavramlar
* MySQL veya SQLite
* 1-1, 1-n, n-m ilişkilerin olduğu çok basit backend crud uygulaması (ister java ister python veya node js)
* html + css (div ortalayabilecek kadar) + js (api ye istek atacak kadar)
* react, angular, vue gibi frameworkleri kullanarak backend api ye istek atan basit bir frontend
* JWT token, hem server tarafında hem de client tarafında implementasyonu
* RestAPI
* NGINX
* Docker
* Postman kullanımı
* Linux işletim sistemi temel komutları
* Git Versiyon sistemi
* readme.md dokumentasyon, markdown formatı

***

**Sektördeki son gelişmelerden haberdar olmak**

Bunu yapabilmek için aşağıdaki yöntemleri tercih edebilirsiniz:

* O dil/platform hakkında özelleşmiş toplulukları ve topluluktaki kişileri LinkedIn, Twitter gibi mecralardan takip etmek
* LinkedIn'de ilgili gruplara katılmak
* Youtube da paylaşım yapan o platform ile alakalı kanalları takip etmek

***

**Java özelinde tavsiye edebileceğim youtube kanalları, web siteler, kişiler, topluluklar vs.**

\[https://javagyansite.com]\[]\
\[https://www.vinsguru.com]\[]\
\[https://javarevisited.blogspot.com]\[]\
[">https://www.java67.com](https://www.java67.com/?ref=gurkanucar.com)

Robert C. Martin\
Martin Fowler\
Venkat Subraminam\
Lemi Orhan ([">https://speakerdeck.com/lemiorhan](https://speakerdeck.com/lemiorhan?ref=gurkanucar.com))\
Devoxx ([">https://www.youtube.com/@DevoxxForever](https://www.youtube.com/@DevoxxForever?ref=gurkanucar.com))\
Çağkan kantarcı ([">https://www.youtube.com/@cagkankantarci](https://www.youtube.com/@cagkankantarci?ref=gurkanucar.com))\
FolksDEV ([">https://www.youtube.com/@FolksDev](https://www.youtube.com/@FolksDev?ref=gurkanucar.com))\
Turkey Java Community ([">https://www.youtube.com/@TurkiyeJavaCommunity](https://www.youtube.com/@TurkiyeJavaCommunity?ref=gurkanucar.com))\
Java Users Group ([">https://www.youtube.com/@IstanbulJavaUserGroup](https://www.youtube.com/@IstanbulJavaUserGroup?ref=gurkanucar.com))\
Bouali Ali ([">https://www.youtube.com/@BoualiAli](https://www.youtube.com/@BoualiAli?ref=gurkanucar.com))\
Daily Code Buffer ([">https://www.youtube.com/@DailyCodeBuffer](https://www.youtube.com/@DailyCodeBuffer?ref=gurkanucar.com))\
Amigos Code ([">https://www.youtube.com/@amigoscode](https://www.youtube.com/@amigoscode?ref=gurkanucar.com))\
Dan Vega ([">https://www.youtube.com/@DanVega](https://www.youtube.com/@DanVega?ref=gurkanucar.com))\
Siva Labs ([">https://www.youtube.com/@sivalabs](https://www.youtube.com/@sivalabs?ref=gurkanucar.com))\
Programming Techie ([">https://www.youtube.com/@ProgrammingTechie](https://www.youtube.com/@ProgrammingTechie?ref=gurkanucar.com))

\[ Previous issue]

**Coming soon**

Next issue

**Spring Boot In Memory Cache - Caffeine**
