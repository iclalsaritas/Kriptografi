###### Merhaba! Kriptografi temeli atmak için nereden başlayacağını bilemiyor ve kaynak arıyor olabilirsin. Emin ol doğru yerdesin. Tarihsel süreçten, akan şifrelere doğru gidilecek bu yolda yeterli çalışma motivasyonuna sahipsen ve içeriğimi okumaya hazırsan daha fazla bekleme, hemen başla :) İlerlememiz şu başlıklar altında olacaktır :

#### 1) Kriptografi Tarihsel Serüveni
##### - Temel Kavramlar Hakkında Bilgi Kazandırmak
##### - Tarihî Şifreler 
##### - Frekans Analizi
##### - Enigma
##### - Colossus

#### 2) Blok Şifreler 
##### - Blok Şifre
##### - Blok Şifre Tasarımı
##### - Feistel Şifreler ve DES
##### - AES 
##### - Blok Şifre Çalışma Prensibi

#### 3) Akan Şifreler
##### - Vernam Şifresi
##### - Senkron Şifreler
##### - Asenkron Şifreler

#### 4) Özet(Hash) Fonksiyonlar
##### - Hash Fonksiyonlar
##### - Blok Şifreden Hash Fonksiyon Tasarlamak
##### - MD4, MD5
##### - SHA1, SHA2, SHA3
##### - Parola Kırmak

#### 5) Açık Anahtar Kriptografisi
##### - Diffie-Hellman Anahtar Değişimi
##### - RSA Şifreleme Algoritması
##### - El-Gamal Şifreleme Algoritması ve Dijital İmza 
______________________________________________________________________________________________________________________________________________________________________________________________________________________________
#### 1) Kriptografi Tarihsel Serüveni
##### - Temel Kavramlar Hakkında Bilgi Kazandırmak 
##### Kriptoloji : Güvenli olmadığını varsaydığımız bir iletişim kanalında güvenli iletişim ile ilgilenir. Bunu günlük hayatta kullandığınız iletişim yöntemleri olarak düşünebilirsiniz. Mektuplaşıyorsanız bir mektubu, hatta havada uçan güvercinden gelen postayı, telefon görüşmesi yapıyorsanız da bir telefonu düşünebilirsiniz. Burada asıl önemli olan, kullanılan iletişim aracının ne olduğu değildir. Güvende miyim? Birisi beni dinliyor mu? endişenizin şiddetinin ne olduğudur. Yani kriptoloji, yollayacağımız mesajı şifreli şekilde yollayıp deşifre edilmemizi engelleyen bir bilim dalıdır.
##### Kriptografi : Güvenli kriptosistem/şifre tasarımıyla ilgilenir.
##### Kriptanaliz : Kriptosistem/şifre analiziyle yani kırma işlemleriyle ilgilenir.
##### NOT ! İki terimi birbirinden ayrı düşünmek tam anlamıyla hata olacaktır. Çünkü sağlam bir tasarım için onu nasıl kırabileceğini de bilmek gerekir. 
##### [ Peki ben hala Kriptografi ve Kriptoloji terimlerini karıştırıyorum İclalciğim diyorsan, endişelenme. Günümüzde iki kavram da aynı anlamda kullanılıyor. ]

##### / Kriptografi Sayesinde Çözülen Güvenlik Problemleri /
##### * Şifreleme(Encryption) yöntemiyle verilerin(Depolanan veriler), iletilerin ve görüşmelerin güvenliğini sağlamak. 
##### * Integrity yani verinin kaynağında oluşturulduğu gibi korunduğu ve iletim veya depolama sürecinde manipülasyona uğramadığı şeklinde ifade edebileceğimiz bir bütünlüktür. Depolanan veri, mesaj ve yapılan görüşmelerin bütünlüğünü sağlamak. Bu bütünlük hash fonksiyonları ile sağlanır.
##### * Authentication kimlik doğrulama süreci de veri kimlik doğrulaması ve şahıs güvenliğini koruyan bir adımdır. Elektronik imza da bir çözümdür lakin bazen verinin de doğrulanması gerekir. .(Şahısların teyidi konusuna açık anahtar kısmında değineceğim.)
##### * Transaction non-repudiation dediğimiz işlem inkar edilememezliği yani elektronik imza diye örnek verebileceğimiz bir çözüm örneğidir. Bunun dışında kripto para işlemlerinizde de ben yaptım ben yapmadım diye kendinizi savunabileceğiniz bir private key e sahip olduğunuzdan mütevellit yetkinin sadece sizde olması durumudur.
##### Aramızda parolaya şifre diyen şifreye parola diyen ya da ikisini de söylemeyen kişiler bulunuyor olabilir. Hayatta her şey mümkün. Günlük hayatta, sosyal medya hesaplarımıza giriş yaparken kullandığımız arkadaşa parola diyoruz. Peki şifre nedir? Hadi bunu konuşalım :
##### Kriptosistem/Şifre nedir ?
##### Korumak istediğimiz şey düz bir metin olsun. İşte bizim şifre dediğimiz şifreli metin dediğimiz şey, düz metnin şifrelenmiş hali oluyor.
##### Düz metni şifreli metne, şifreli metni düz metne dönüştüren algoritma çiftine kriptosistem/şifre adını veriyoruz.
##### Şifreleme işlemi sırasında kullanılan gizli bilgiye de anahtar diyoruz. (İlerleyen bölümde anlatacağım.)
##### Harika bir çizimle işi özetleyip diğer konumuza geçiş yapıyorum.
![1](https://github.com/iclalsaritas/Kriptografi/assets/97543719/6f6c9da0-ee21-48b8-afa6-4d8adff2c068)

##### - Tarihî Şifreler
##### Teknolojinin pasif olduğu eski yıllarda elle yazma şeklinde yapılan yöntemdir. Bu yöntemde kağıt-kalem kullanıldığından kriptosistemin absürt bir karmaşıklığa sahip olmaması gerekir. Genelde harf değişim sistemi kullanılır. Bilgi sızdırmamak için şifreli metindeki noktalama işaretleri ve boşluklar genelde silinir. Enigma bölümüne geldiğimizde son cümlede bahsettiğim bilgi sızdırmama mevzusuna güzel bir örneğim olacak.
##### Sezar Şifresi : Julius Caesar MÖ 1. yüzyılda askerî mesajların güvenliğini korumak için özgün bir yöntem geliştirmiştir. Bu yöntemde her harf, alfabedeki kendisinden n önceki harf ile değiştirilir. Hemen örneğimiz gelsin :
![2](https://github.com/iclalsaritas/Kriptografi/assets/97543719/f99e9a0a-c511-488f-8b04-1777bd1943ab)
##### Şimdi şöyle bir gerçek vardır ki Sezar şifresi, alfabe 26 harf olduğuna göre sadece 25 farklı kaydırma yöntemi olduğu için kolayca kırılabilir. Modern bilgisayarlar ve şifre kırma yöntemleri, brute force saldırıları, frekans analizi ve dilbilgisi özelliklerini kullanarak Sezar şifresini hızlı bir şekilde kırabilirler. Sonuç olarak, Sezar şifresi kullanıldığında güvenlik düzeyi çok düşüktür. Biz buna anahtar uzayı çok küçük diyoruz. Yani anahtarı tahmin etmek çok kolay.
##### Basit Monoalphabetic Değişim : Her harf bir harf ile yer değiştirir. A harfi artık K, B harfi artık U harfi gibiymiş gibi davranılır. Örnek :
![3](https://github.com/iclalsaritas/Kriptografi/assets/97543719/1cb906b3-3cf9-4598-8aaa-405905c526a6)
##### Peki İclalciğim madem bu kadar çok olasılığın mümkün olduğu bir şifreleme yönteminden bahsediyorsun. Öyleyse neden brute force ataklarından korunmak için Monoalphabetic değişim kullanmayalım? Çünkü arkadaşım, dildeki tekrar ve frekans analizi yöntemiyle bu 26! olasılıklı şifre kolayca kırılabiliyor. Frekans Analizi nedir hemen sırası gelmişken anlatayım.

##### - Frekans Analizi 
##### 9.yy.'da  Al-Kindi tarafından önerilmiştir. Dildeki tekrara dayanmaktadır. Bu alan hakkında kitabı da mevcuttur hatta bir kopyası Topkapı Müzesinde bulunuyor. Belli bir ücret karşılığı sayfaların fotoğrafını çekebiliyoruz diye hatırlıyorum. Dildeki tekrar derken ne demek istiyoruz? Mesela Al-Kindi diyor ki, herhangi bir dil için o dilde yazılmış olan uzun bir yazı bul ve o yazıda en çok hangi harf geçiyor notunu al. Bu dil Türkçe ise uzun bir metinde en çok A harfinin tekrarladığını görürsün. Bu şekilde en çok tekrarlanan ikinci, üçüncü, dördüncü... harf diye gittiğinizde, bu harfleri listede yerine koyduğunuz harflerle eşleştirip şifreyi kırabilirsiniz. Frekans Analizinde işin özü bu şekildedir.

##### Playfair : Yıl 1854, Viktorya Döneminden Charles Wheatstone tarafından kullanılması tavsiye ediliyor, dönemin İngiliz bilimcisi ve siyasetçisi olan Lord Playfair tarafından da destekleniyor. Şu ana kadarki anlattığım şifrelerin daha karmaşık olmasını burada deneyebiliriz. Bu şifrelemede, anahtarın ve alfabenin geri kalanının yer aldığı 5x5 tablo kullanılıyor. Eğer anahtarı ve kuralını ezberlerseniz(4 adet kural var) sistemi rahatlıkla kullanabilirsiniz. Neden 5x5 tablo kullanıyoruz gibi bir soru işareti belirebilir belki zihninizde. Esasında en başında dönem ve İngiliz diye belirtmemdeki amaç sadece genel kültür kazanmanız değil, aynı zamanda İngiliz diye belirtirsem İngilizlerin 26 harf kullandığı ve böylece 5x5 tablo kullanılması gerektiği kültürünü ezbere olarak değil de mantıksal olarak sizlere kattığımdan emin olmuş olurum diye düşündüm. Şimdi hemen örneğimi gösteriyorum : 
![4](https://github.com/iclalsaritas/Kriptografi/assets/97543719/1e61b8a5-c9ed-4be7-ad58-dbdcaf3fec3c)

##### Önce anahtar yazılır. Aynı harfler bir kez kullanılır. 5x5 tablonun geri kalanı kalan harflerle doldurulur. I ve J harfi 25 harfe inmek için aynı kutuya konur. Sık kullanılan harf olmadığından biraz kurban harf oldu diyebiliriz. 
##### Şimdi gelelim sistemi kullanabilmek için bilmemiz gerekiyor dediğim 4 kuralı anlatmaya.
##### 1- Eğer iki harf de aynıysa ya da en son tek bir harf kaldıysa, ilk harften sonra bir X harfi eklenir.
##### 2- Eğer iki harf aynı satırdaysa, her harf sağındaki harfle değiştirilir. Peki ya satır sonundaysa? Bir harf satır sonundaysa satır başındakiyle değiştirilir.
##### 3- Eğer iki harf aynı sütundaysa, her half altındaki harfle değiştirilir. Peki ya  sütun sonundaysa? Bir harf sütun sonundaysa sütun başıdakiyle değiştirilir.
##### 4- Eğer harfler aynı sütun veya satırda değilse, harfler bir dikdörtgenin 2 köşesi olarak düşünülür ve harfler karşılarındaki köşede yer alan harf ile değiştirilir. 
##### Biraz karmaşık mı geldi ? Hemen harika çizimlerime devam ediyorum :
![5](https://github.com/iclalsaritas/Kriptografi/assets/97543719/be7a379f-bb8d-4bb2-9022-058cac0794da)
##### Frekans Analizi için bazı önlemleri konuşalım.
##### Birden fazla harf değişimi kullanımı, Mantıken baktığımızda Playfair gibi bir yöntemin de iki harfli frekans analizine dayanıklı olmadığını görüyoruz ki günümüzde bilgisayarlar ile kısa uzunluktaki harf değişimlerini kırmak hiç de zor değil. Uzun harf dönüşümlerinde anahtarı kaydetmek, pratikte kullanmak ve şifreleme-deşifreleme yapmak çok çok zordur. Doğruya doğru dediğimiz bir konu varsa o da şu ki, aslında çoklu harf dönüşümleriyle uğraşıp durmak bunları türetmek günün sonunda Block şifre fikrinin oluşmasına yol açmıştır. 

##### - Enigma 
##### Bunca zaman elle yazmak dedik, kağıt-kalem yöntemi dedik durduk. Artık makinelerden konuşmanın zamanı geldi. Teknolojik gelişmelerle kağıt-kalemlere veda ettiğimiz zamana giriş yaptık. En popüler örnek olarak Enigma örneğini verebiliriz. 
![6](https://github.com/iclalsaritas/Kriptografi/assets/97543719/17814bd7-62d4-4de4-8cce-fd39378889cb)
##### Bu gördüğümüz Enigma, elektrik-mekanik çarklı şifreleme makinesidir. 20. yüzyılda askeri,bankacılık gibi alanlarda kullanılmıştır. Çoklu harf değişim şifresi olarak çalışmaktadır. Çarkların durumu ne olursa olsun bir harfin hiçbir zaman kendisine şifrelenmiyor olma özelliği yüzünden -ki bu özellik kasıtlı eklenmiştir- Enigma kolayca kırılmıştır. İngilizler Enigma'yı kırınca 2. Dünya Savaşı seyri de değişmiştir. Almanların ifşalanması mevzusunu biraz daha açmak istiyorum aslında. Hangi karakter hangi karaktere denk gelir konusunu konuşup duruyoruz. Enigma'yı değersiz yapan, ifşalayan ne oldu ? Almanlar her iletişim öncesi "Heil Hitler!" yazdığı için kullanılan anahtarın tespit edilmesi Almanları ifşalayan şey oldu.

##### - Colossus 
##### Dünyanın ilk programlanabilir elektronik dijital bilgisayarıdır. İngiliz uzmanlar tarafından Lorenz şifresinin kriptanalizi için geliştirilmiştir. Alan Turing tasarımlarıyla katkıda bulunmuştur. 2. Dünya Savaşı bitiminde İngilizler, başka ülkeler bu teknolojiyi öğrenmesin diye bilgisayarı parçalamışlardır.
![7](https://github.com/iclalsaritas/Kriptografi/assets/97543719/b79b7989-65f8-4d53-baf3-95ad1f2efcf8)
____________________________________________________________________________________________________________________________________________________________________________________________________________________________

#### 2) Blok Şifreler
##### Bu bölümde şifre tasarımlarına geçmeden önce ufak bir muhabbet gerçekleştirelim. Encoding, algoritmalar ve kriptosistemlerden konuşalım biraz.
##### Biz biliyorduk ki eski şifreler genellikle harf değişimleri kullanılarak kağıt-kalem işleriyle yapılıyordu. Günümüze doğru yaklaştığımızda durum değişti çünkü teknolojinin gelişmesiyle dijitalleşme başladı. E haliyle veriler bitlerden yani 0 ve 1 lerden oluşur vaziyete geldi. 
##### Encoding kısacası insanların ya da makinelerin aynı dili konuşması için seçtiği bir karakter tablosu şeklinde düşünebiliriz. En bilindik encoding tablosu ASCII tablosudur. Bu tabloda bazı Türkçe karakterler bulunmadığından utf-8 gibi encodingler kullanmamız gerekiyor.
![1](https://github.com/iclalsaritas/Kriptografi/assets/97543719/e3ecb4ae-c872-474e-b565-84bca6048f3e)

##### Kriptografik algoritmalar anahtarlı ve anahtarsız olmak üzere ikiye ayrılır. Anahtarsız algoritmalar özet (Hash) fonksiyonlarıdır. Anahtarlı algoritmalar ise simetrik ve asimetrik olmak üzere ikiye ayrılır.
##### Simetrik Anahtar/Gizli Anahtar : Bir tane gizli anahtarım var. Bu anahtarımı hem şifreleme hem de deşifreleme için kullanıyorum.
##### Asimetrik Anahtar/Açık Anahtar : Şifreleme ve deşifreleme anahtarlarım farklı. İlerleyen kısımda detayları konuşulacak.

##### Gizli Anahtar Algoritmaları
##### Bu algoritmada şifreleme ve deşifreleme için aynı anahtarımı kullanıyorum demiştim. Bu yüzden simetrik anahtar ismiyle de kullanırız. Bu kategori üç ana başlıktan oluşur :
##### Blok Şifreler
##### Akan Şifreler
##### Mesaj Doğrulama Kodları (MAC)
##### NOT ! MAC in Blok ve Akan şifrelerden farkı, kodların şifreleme amaçlı değil de mesajın doğruluğunun kontrol edilmesi amaçlı oluşudur. Mesajı şifrelemeden yollayıp mesajın sonuna kısa bir etiket ekliyoruz. Bu etiketi üretirken gizli anahtar kullanıyoruz.

##### Simetrik kriptosistemler : Blok şifreler ve akan şifreler şifreleme işlemi için kullanılmaktadır. MAC verinin ya da mesajı yollayan kaynağını doğrulamak için kullanılmaktadır.
##### Asimetrik kriptosistemler : Asimetrik kriptografi anahtar paylaşımı , açık anahtar şifreleme ve dijital imza gibi değişik türden algoritmalardan oluşmaktadır.

##### - Blok Şifre
##### Blok şifreler b bit uzunluğundaki veri üzerinde çalışır.
##### Düz metim b bit uzunluğundaki bloklara bölünür.
##### Her blok k bit uzunluğundaki anahtar yardımıyla şifrelenerek b bit uzunluğunda çıktı oluşturur.
##### Çıktı bloklarından şifreli metin elde edilir.
##### Bir blok şifre ve seçilen anahtar , 2^b elemanlı bir kümenin elemanlarını aynı 2^b elemanlı kümeye gönderen bir permütasyon olarak düşünülebilir.
##### Günümüzde b= 64 ya da 128 bit ve |k| = 128 ,192 ya da 256 bit olarak seçilir. Ne kadar yüksek bit seçersen o kadar sağlam bir güvenliğe sahip olursun. Bu yüzden bitini uzun tutmanda fayda var.

##### - Blok Şifre Tasarımı
##### Blok şifre tasarlarken neye dikkat etmek gerekir? 
##### Claude Shannon
##### Bilgi Teorisinin babası olarak kabul edilir.
##### 2. Dünya Savaşında kriptanaliz alanına katkı sağlamıştır.
##### Communication Theory of Secrecy Systems  başlıklı makalesinde şifre tasarımı için karmaşa (Confusion) ve yayılım (Diffusion) fikirlerini önermiştir.
##### Karmaşa : Şifreli metin ve anahtar arasındaki ilişkinin son derece kompleks ve kapsayıcı olması.
##### Yayılım : Düz metindeki istatistiksel zafiyetler (Tekrarlar) şifreleme sırasında şifrenin her yanına nüfuz ederek yok olmalıdır.

##### NOT ! Bu karmaşa ve yayılım fikirleri ölçülebilir kavramlar değildir. Soyutturlar. Haliyle tasarım sırasında tercih ettiğimiz parametreler, fonksiyonlar ve işlemler bu kavramlar açısından en iyi olacak şekilde seçilmeye çalışılmaktadır.

##### Bir şifre birçok karmaşık operasyon kullanılarak tasarlanmak yerine, genellikle döngü ismini verdiğimiz bir fonksiyonun r kez tekrarlanması şeklinde tasarlanır. Çünkü buradaki anafikir şu, eğer son derece karmaşık bir tasarım yaparsanız bu tasarımın iyi olup olmadığını test etmemiz zor olacaktır. Dolayısıyla tasarladığımız şeyin güvenli olup olmadığını kontrol etmek zorlaşacaktır.
##### Anahtar kullanımı : Her döngüde gizli anahtarı direkt olarak kullanmak yerine, bir anahtar kullanma algoritması ile gizli anahtardan her döngüde kullanılmak üzere ayrı bir döngü anahtarı oluşturulur.


##### Blok şifre tasarımını iki alana ayırabiliriz : 
##### Değişim Permütasyon Ağı : Bir döngü 3 katmandan oluşur. Anahtar ekleme, değişim ve permütasyon. Anahtar ekleme kısmında anahtar düz metin ile işleme sokulur. Değişim kısmında karmaşıklık sağlanır. Permütasyon kısmında dağılım sağlanır. Bu yapıya örnek şifreler AES ve PRESENT verebiliriz. AES şu an dünyada en çok kullanılan şifreleme algoritmasıdır. PRESENT  hafif uygulamalar hafif şifreler için önerilir. Söylediklerimin özetini şekil üzerinden gösterirsem : 
![1](https://github.com/iclalsaritas/Kriptografi/assets/97543719/3a8b712d-944c-4273-a2ad-b538a8a48a0c)
##### Bakın aslında işlemler gayet göz önünde. Ne yaptığım gayet ortada. Öyleyse güvende miyim? Bence güvendesin. Çünkü kötü bir senaryoda şifreli metin bloğuna ulaşılmış olsa bile, işlemi geri sardığında ne düz metin bloğuna ulaşabiliyorsun ne de anahtarı görebiliyorsun. Karşına anahtar ekleme gibi engeller çıkmaya başlıyor. Bir ihtimal şfreli metinden düz metni tahmin etseler yine de anahtarı bulmak için yeterli olmayacaktır. Kısacası tam anlamıyla olmasa da güvendesin.

##### - Feistel Şifreler ve DES

##### Feistel Ağı : Horst Feistel tarafından önerilmiştir. Bir döngü iki aşamadan oluşur. döngü fonksiyonu ve yer değiştirme işlemi.
##### B bitlik girdi iki parçaya bölünür. Döngü fonksiyonu önce bir parçaya uygulanır ve elde edilen çıktı diğer parça ile işleme sokulur. Daha sonra iki parça yer değiştirir. Bu sayede bir sonraki döngüde bu sefer işleme koyulmamış parça döngü fonksiyonundan etkilenir. Görselle daha iyi anlaşılabilir :
![2](https://github.com/iclalsaritas/Kriptografi/assets/97543719/410763b1-287b-4a49-8582-1f4abd301632)
##### Bakın burada şifreli metni ele geçiren kişi, sağ parçayı gizli anahtarı bildiğinden dolayı döngü fonksiyonuna katarak yukarıya doğru çıkar ve düz metne ulaşmış olur. 
##### SPN ve Feistel artılarını inceleyecek olursak : 
##### / Artılar /
##### Feistel : Şifreleme ve deşifreleme algoritmaları tamamen aynıdır. Sadece döngü anahtarlarının sırası değiştirilir.
##### SPN : Tek döngü girdinin tamamını etkilemektedir. 
##### / Eksiler /
##### Feistel : Tek döngü girdinin sadece yarısını etkilemektedir.
##### SPN : Deşifreleme işlemi değişim ve permütasyon tabakalarının tersini de gerektirmektedir. 

##### - DES (Data Encryption Standard) 
##### IBM tarafından 1970 zamanlarında tasarlanmıştır. Önceki tasarımlar Feistel tarafından yapılmıştır. 1976 yılında NSA değişim kutularını (S-box) değiştirerek şifreyi değiştirmiştir. Bu esasında olumlu bir harekettir ancak anahtar uzunluğunun kısalmasına sebep olduğu için güvenliğini azaltmıştır. 1990 zamanlarından sonra anahtar uzunluğunun kısa olması sebebiyle kullanılamaz hale gelmiştir.
##### Blok uzunluğu : 64 bit
##### Anahtar uzunluğu : 56 bit
##### Döngü sayısı : 16
![3](https://github.com/iclalsaritas/Kriptografi/assets/97543719/4427dd74-1183-4e5e-a3cb-e0398d4971cb)

##### - AES 
##### Baktılar DES kolay kırılıyor, AES ortaya çıkıyor. AES (Advanced Encryption Standard)/Rijndael. 2001 yılında NIST tarafından standart yapılmıştır (AES yarışması kazananı). Diğer finalistler SERPENT,TWOFISH, RC6 ve MARS.
##### Blok uzunluğu : 128 bit
##### Anahtar uzunluğu : 128, 192, 256 bit
##### Döngü sayısı : 10, 12, 14 (Anahtar uzunluğuna bağlıdır.)
##### Bilinen ataklar etkisizdir.




