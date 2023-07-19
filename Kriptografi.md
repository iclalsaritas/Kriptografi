###### Merhaba! Kriptografi temeli atmak için nereden başlayacağını bilemiyor ve kaynak arıyor olabilirsin. Emin ol doğru yerdesin. Tarihsel süreçten, akan şifrelere doğru gidilecek bu yolda yeterli çalışma motivasyonuna sahipsen ve içeriğimi okumaya hazırsan daha fazla bekleme, hemen başla :) Defterimin Kriptografi-101 kısmı senindir. İlkokul Hocam görmesin ama .d İlerlememiz şu başlıklar altında olacaktır :

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
____________________________________________________________________________________________________________________________________________________________________________________________________________________________
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

![90](https://github.com/iclalsaritas/Kriptografi/assets/97543719/b0121869-ad1c-43b5-8845-245be36d6547)

##### - Tarihî Şifreler
##### Teknolojinin pasif olduğu eski yıllarda elle yazma şeklinde yapılan yöntemdir. Bu yöntemde kağıt-kalem kullanıldığından kriptosistemin absürt bir karmaşıklığa sahip olmaması gerekir. Genelde harf değişim sistemi kullanılır. Bilgi sızdırmamak için şifreli metindeki noktalama işaretleri ve boşluklar genelde silinir. Enigma bölümüne geldiğimizde son cümlede bahsettiğim bilgi sızdırmama mevzusuna güzel bir örneğim olacak.
##### Sezar Şifresi : Julius Caesar MÖ 1. yüzyılda askerî mesajların güvenliğini korumak için özgün bir yöntem geliştirmiştir. Bu yöntemde her harf, alfabedeki kendisinden n önceki harf ile değiştirilir. Hemen örneğimiz gelsin :
![10](https://github.com/iclalsaritas/Kriptografi/assets/97543719/4c46e0cc-70ef-4fb6-9822-b008408b3ebe)

##### Şimdi şöyle bir gerçek vardır ki Sezar şifresi, alfabe 26 harf olduğuna göre sadece 25 farklı kaydırma yöntemi olduğu için kolayca kırılabilir. Modern bilgisayarlar ve şifre kırma yöntemleri, brute force saldırıları, frekans analizi ve dilbilgisi özelliklerini kullanarak Sezar şifresini hızlı bir şekilde kırabilirler. Sonuç olarak, Sezar şifresi kullanıldığında güvenlik düzeyi çok düşüktür. Biz buna anahtar uzayı çok küçük diyoruz. Yani anahtarı tahmin etmek çok kolay.
##### Basit Monoalphabetic Değişim : Her harf bir harf ile yer değiştirir. A harfi artık K, B harfi artık U harfi gibiymiş gibi davranılır. Örnek :
![11](https://github.com/iclalsaritas/Kriptografi/assets/97543719/8eafd602-6b75-4335-a47d-422b8dd9091d)

##### Peki İclalciğim madem bu kadar çok olasılığın mümkün olduğu bir şifreleme yönteminden bahsediyorsun. Öyleyse neden brute force ataklarından korunmak için Monoalphabetic değişim kullanmayalım? Çünkü arkadaşım, dildeki tekrar ve frekans analizi yöntemiyle bu 26! olasılıklı şifre kolayca kırılabiliyor. Frekans Analizi nedir hemen sırası gelmişken anlatayım.

##### - Frekans Analizi 
##### 9.yy.'da  Al-Kindi tarafından önerilmiştir. Dildeki tekrara dayanmaktadır. Bu alan hakkında kitabı da mevcuttur hatta bir kopyası Topkapı Müzesinde bulunuyor. Belli bir ücret karşılığı sayfaların fotoğrafını çekebiliyoruz diye hatırlıyorum. Dildeki tekrar derken ne demek istiyoruz? Mesela Al-Kindi diyor ki, herhangi bir dil için o dilde yazılmış olan uzun bir yazı bul ve o yazıda en çok hangi harf geçiyor notunu al. Bu dil Türkçe ise uzun bir metinde en çok A harfinin tekrarladığını görürsün. Bu şekilde en çok tekrarlanan ikinci, üçüncü, dördüncü... harf diye gittiğinizde, bu harfleri listede yerine koyduğunuz harflerle eşleştirip şifreyi kırabilirsiniz. Frekans Analizinde işin özü bu şekildedir.

##### Playfair : Yıl 1854, Viktorya Döneminden Charles Wheatstone tarafından kullanılması tavsiye ediliyor, dönemin İngiliz bilimcisi ve siyasetçisi olan Lord Playfair tarafından da destekleniyor. Şu ana kadarki anlattığım şifrelerin daha karmaşık olmasını burada deneyebiliriz. Bu şifrelemede, anahtarın ve alfabenin geri kalanının yer aldığı 5x5 tablo kullanılıyor. Eğer anahtarı ve kuralını ezberlerseniz(4 adet kural var) sistemi rahatlıkla kullanabilirsiniz. Neden 5x5 tablo kullanıyoruz gibi bir soru işareti belirebilir belki zihninizde. Esasında en başında dönem ve İngiliz diye belirtmemdeki amaç sadece genel kültür kazanmanız değil, aynı zamanda İngiliz diye belirtirsem İngilizlerin 26 harf kullandığı ve böylece 5x5 tablo kullanılması gerektiği kültürünü ezbere olarak değil de mantıksal olarak sizlere kattığımdan emin olmuş olurum diye düşündüm. Şimdi hemen örneğimi gösteriyorum : 
![12](https://github.com/iclalsaritas/Kriptografi/assets/97543719/e090c9bd-170b-4071-985a-57633fd2f15d)

##### Önce anahtar yazılır. Aynı harfler bir kez kullanılır. 5x5 tablonun geri kalanı kalan harflerle doldurulur. I ve J harfi 25 harfe inmek için aynı kutuya konur. Sık kullanılan harf olmadığından biraz kurban harf oldu diyebiliriz. 
##### Şimdi gelelim sistemi kullanabilmek için bilmemiz gerekiyor dediğim 4 kuralı anlatmaya.
##### 1- Eğer iki harf de aynıysa ya da en son tek bir harf kaldıysa, ilk harften sonra bir X harfi eklenir.
##### 2- Eğer iki harf aynı satırdaysa, her harf sağındaki harfle değiştirilir. Peki ya satır sonundaysa? Bir harf satır sonundaysa satır başındakiyle değiştirilir.
##### 3- Eğer iki harf aynı sütundaysa, her half altındaki harfle değiştirilir. Peki ya  sütun sonundaysa? Bir harf sütun sonundaysa sütun başıdakiyle değiştirilir.
##### 4- Eğer harfler aynı sütun veya satırda değilse, harfler bir dikdörtgenin 2 köşesi olarak düşünülür ve harfler karşılarındaki köşede yer alan harf ile değiştirilir. 
##### Biraz karmaşık mı geldi ? Hemen harika çizimlerime devam ediyorum :
![13](https://github.com/iclalsaritas/Kriptografi/assets/97543719/0f30131e-cfe4-4b99-af98-6f01fcb6d05e)

##### Frekans Analizi için bazı önlemleri konuşalım.
##### Birden fazla harf değişimi kullanımı, Mantıken baktığımızda Playfair gibi bir yöntemin de iki harfli frekans analizine dayanıklı olmadığını görüyoruz ki günümüzde bilgisayarlar ile kısa uzunluktaki harf değişimlerini kırmak hiç de zor değil. Uzun harf dönüşümlerinde anahtarı kaydetmek, pratikte kullanmak ve şifreleme-deşifreleme yapmak çok çok zordur. Doğruya doğru dediğimiz bir konu varsa o da şu ki, aslında çoklu harf dönüşümleriyle uğraşıp durmak bunları türetmek günün sonunda Block şifre fikrinin oluşmasına yol açmıştır. 

##### - Enigma 
##### Bunca zaman elle yazmak dedik, kağıt-kalem yöntemi dedik durduk. Artık makinelerden konuşmanın zamanı geldi. Teknolojik gelişmelerle kağıt-kalemlere veda ettiğimiz zamana giriş yaptık. En popüler örnek olarak Enigma örneğini verebiliriz. 
![m](https://github.com/iclalsaritas/Kriptografi/assets/97543719/47d14932-d78a-4565-be90-b64ca5931b25)

##### Bu gördüğümüz Enigma, elektrik-mekanik çarklı şifreleme makinesidir. 20. yüzyılda askeri,bankacılık gibi alanlarda kullanılmıştır. Çoklu harf değişim şifresi olarak çalışmaktadır. Çarkların durumu ne olursa olsun bir harfin hiçbir zaman kendisine şifrelenmiyor olma özelliği yüzünden -ki bu özellik kasıtlı eklenmiştir- Enigma kolayca kırılmıştır. İngilizler Enigma'yı kırınca 2. Dünya Savaşı seyri de değişmiştir. Almanların ifşalanması mevzusunu biraz daha açmak istiyorum aslında. Hangi karakter hangi karaktere denk gelir konusunu konuşup duruyoruz. Enigma'yı değersiz yapan, ifşalayan ne oldu ? Almanlar her iletişim öncesi "Heil Hitler!" yazdığı için kullanılan anahtarın tespit edilmesi Almanları ifşalayan şey oldu.

##### - Colossus 
##### Dünyanın ilk programlanabilir elektronik dijital bilgisayarıdır. İngiliz uzmanlar tarafından Lorenz şifresinin kriptanalizi için geliştirilmiştir. Alan Turing tasarımlarıyla katkıda bulunmuştur. 2. Dünya Savaşı bitiminde İngilizler, başka ülkeler bu teknolojiyi öğrenmesin diye bilgisayarı parçalamışlardır.
![n](https://github.com/iclalsaritas/Kriptografi/assets/97543719/1efc6a8e-f1b1-4df0-a15b-40254a46fb5e)

____________________________________________________________________________________________________________________________________________________________________________________________________________________________

#### 2) Blok Şifreler
##### Bu bölümde şifre tasarımlarına geçmeden önce ufak bir muhabbet gerçekleştirelim. Encoding, algoritmalar ve kriptosistemlerden konuşalım biraz.
##### Biz biliyorduk ki eski şifreler genellikle harf değişimleri kullanılarak kağıt-kalem işleriyle yapılıyordu. Günümüze doğru yaklaştığımızda durum değişti çünkü teknolojinin gelişmesiyle dijitalleşme başladı. E haliyle veriler bitlerden yani 0 ve 1 lerden oluşur vaziyete geldi. 
##### Encoding kısacası insanların ya da makinelerin aynı dili konuşması için seçtiği bir karakter tablosu şeklinde düşünebiliriz. En bilindik encoding tablosu ASCII tablosudur. Bu tabloda bazı Türkçe karakterler bulunmadığından utf-8 gibi encodingler kullanmamız gerekiyor.
![111](https://github.com/iclalsaritas/Kriptografi/assets/97543719/ef385b90-50d9-4dba-a7a1-bcf55e474211)

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
![14](https://github.com/iclalsaritas/Kriptografi/assets/97543719/9c154909-0709-4172-8e09-4132f5f1d2da)

##### Bakın aslında işlemler gayet göz önünde. Ne yaptığım gayet ortada. Öyleyse güvende miyim? Bence güvendesin. Çünkü kötü bir senaryoda şifreli metin bloğuna ulaşılmış olsa bile, işlemi geri sardığında ne düz metin bloğuna ulaşabiliyorsun ne de anahtarı görebiliyorsun. Karşına anahtar ekleme gibi engeller çıkmaya başlıyor. Bir ihtimal şfreli metinden düz metni tahmin etseler yine de anahtarı bulmak için yeterli olmayacaktır. Kısacası tam anlamıyla olmasa da güvendesin.

##### - Feistel Şifreler ve DES

##### Feistel Ağı : Horst Feistel tarafından önerilmiştir. Bir döngü iki aşamadan oluşur. döngü fonksiyonu ve yer değiştirme işlemi.
##### B bitlik girdi iki parçaya bölünür. Döngü fonksiyonu önce bir parçaya uygulanır ve elde edilen çıktı diğer parça ile işleme sokulur. Daha sonra iki parça yer değiştirir. Bu sayede bir sonraki döngüde bu sefer işleme koyulmamış parça döngü fonksiyonundan etkilenir. Görselle daha iyi anlaşılabilir :
![15](https://github.com/iclalsaritas/Kriptografi/assets/97543719/8fa7730a-7c33-480e-8aee-ad2e5d7d2f25)

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
![16](https://github.com/iclalsaritas/Kriptografi/assets/97543719/01bc53e0-e818-426c-a6cc-71d41208a3ad)


##### - AES 
##### Baktılar DES kolay kırılıyor, AES ortaya çıkıyor. AES (Advanced Encryption Standard)/Rijndael. 2001 yılında NIST tarafından standart yapılmıştır (AES yarışması kazananı). Diğer finalistler SERPENT,TWOFISH, RC6 ve MARS.
##### Blok uzunluğu : 128 bit
##### Anahtar uzunluğu : 128, 192, 256 bit
##### Döngü sayısı : 10, 12, 14 (Anahtar uzunluğuna bağlıdır.)
##### Bilinen ataklar etkisizdir.

##### / Bazı Problemler /
##### Anahtar Yönetimi | Anahtarlar haberleşecekler arasında önceden güvenli şekilde ulaştırılması gerekmektedir. n kişiyle haberleşmek için n anahtarın üretilip ulaştırılması gerekir.
##### Çözüm | Açık anahtar şifreleme algoritmaları ama daha yavaşlar (performans, yüksek data transferi sorunları). Açık anahtar kriptografisinin anahtar değişimi algoritmaları kullanılabilir (tavsiye edilen çözüm).

##### Anahtar Depolama | Anahtarı HDD'de ya da RAM'de direkt depolamak sorun olabilir. Virüs, Trojan vb. sisteme girerse ayvayı yeriz.
##### Mesaj Uzunluğu Saklama | Düz metin ve şifreli metin uzunluğu aynıdır. Dolayısıyla iletişimin ana konusunu bilen ve iletişimi dinleyen birisi şifreli metin uzunluklarına bakarak düz metnin ne olduğunu tahmin edebilir.
##### Anahtar Üretimi | k bitlik güvenlik için kullanılacak k bitlik anahtarın rastgele üretilmiş olması lazım.
##### Çözüm | Kriptografik açıdan güvenli rastgele sayı üreteçleri ve parola tabanlı anahtar üretim algoritmaları.



##### - Blok Şifre Çalışma Prensibi
##### Bir önceki bölümde blok şifreleri tanımlarken verdiğim bütün şifre örneklerinde verdiğim algoritmalar belli bir blok uzunluğunda girdi alıp aynı blok uzunluğunda çıktı alıyordu. Dolayısıyla blok uzunluğu 16 bit olan bir blok şifrenin sanki girdisi hep 16 bit mış gibi bütün bu örnekleri vermiştim. Ama pratikte kullanırken şifreleyeceğimiz veri, çok daha kısa ya da çok daha uzun olabilir. 2-3 bit gibi kısa bir veriyi de şifreleyecek olabiliriz ama 1 terabayt gibi veriyi de şifreleyecek olabiliriz. Dolaysıyla pratikte bir yöntem seçmek gereklidir. Blok şifre kullanırken 2 sorun ortaya çıkar :
##### Blok şifreler blok uzunluğu kadar girdi aldıkları için, 2 bayt gibi blok uzunluğundan kısa düz metinler nasıl şifrelenmelidir? Blok uzunluğundan daha uzun düz metinler nasıl şifrelenmelidir?
##### Bu iki problemin pratikte nasıl yanlış sonuçlar doğurabileceğini görebilmek için motivasyonu açıklamak gerekiyor. 1. motivasyon, eğer düz metin blok uzunluğundan kısaysa, kalan boşlukları 0 bitleriyle doldurabiliriz (Dolgu/Padding).
##### Problem | Şifreli metni deşifre eden kişi düz metnin sonundaki 0 bitlerinin dolgudan mı kaynaklandığını yoksa düz metnin kendisinin mi olduğunu ayırt edemez. Örneğin, 64 bitlik AB12F3955CDD2F00 bloğunu düşünelim. Sondaki 0 baytının dolgudan mı kaynaklandığını bilemeyiz.
##### Klasik Şifrelerde Dolgu
##### Dolgu yöntemi klasik şifrelerde mesajın başında ve sonunda uygulanmaktadır. Resmi mesajların başını ya da sonunu tahmin etmek zor değildir. Dolayısıyla şifreli metni ele geçirenler aynı zamanda düz metnin de bir kısmını bilir hale gelmektedir. Bunu engellemek için düz metnin başına ve sonuna rastgele kelimeler eklenir. Bu fazladan kelimeler deşifre işleminden sonra ayıklanır.

##### Şimdi sıra geldi ikinci problem için konuşmaya. Önce iki kavramdan bahsedeyim. Başlangıç Vektörleri ve Nonce. Başlangıç Vektörleri; blok şifre, özet fonksiyon ya da mesaj doğrulama kodu gibi kriptografik algoritmaların ilk çalıştırıldığı anda girdi olarak kullanılan değerlerdir. Başlangıç vektörleri gizli değildir ve standart dokümanlarından ulaşılabilir.
##### Rastgele üretilmiş ve tek bir sefer kullanılacak değerlere nonce adı verilmektedir. Kriptografik algoritmaların güvenliği için Nonce ve Vektörel Algoritmaların rastgele üretilmiş olmaları gerekmektedir.
##### NIST'in Blok Şifre Çalışma Yöntemleri
##### 1) Electronic Codebook(ECB)
##### 2) Cipher Block Chaining(CBC)
##### 3) Cipher Feedback(CFB)
##### 4) Output Feedback(OFB)
##### 5) Counter(CTR)
##### 6) XTS(2010 yılında 800-38E dokümanında eklenmiştir.)
##### Çalışma yöntemi seçimi : Çalışma yöntemi seçilirken şifreleme işleminin yapılacağı koşullar, güvenlik ve performans dikkate alınmalıdır.
____________________________________________________________________________________________________________________________________________________________________________________________________________________________

#### 3) Akan Şifreler
##### Simetrik anahtarlı şifreleme algoritmaları genellikle iki grupta incelenir demiştik. Neydi o ikisi? Blok şifreler ve Akan şifrelerdi.
##### Blok Şifreler : Düz metin bloklarına sabit bir dönüşüm uygular.
##### Akan Şifreler : Düz metin bit/bayt bloklarına zaman göre değişen bir dönüşüm uygular.
##### Bu kısa hatırlatmadan sonra Akan şifrelere devam edelim.
##### Akan şifrelerin doğmasının sebebi one time pad den kaynaklanmaktadır. Diğer ismiyle Vernam şifresidir. Tarihsel serüven kısmında ufak bir değinmiştim. One time pad rastgele bitlerden oluşan uzun bir anahtar dizisi kullanır. Anahtar dizisi uzunluğu en az düz metin kadar olmalıdır ve sadece 1 kez kullanılmalıdır. Şifreleme, anahtar dizisinin düz metin bitleriyle XOR'lanmasıdır. Shannon one time pad in kırılamaz olduğunu ispatlamıştır. Çok fazla anahtar dizisine ihtiyaç duyulacağından pratik değildir. Bir örnek :
![k](https://github.com/iclalsaritas/Kriptografi/assets/97543719/fcaf25af-530f-41ff-a7d0-e63921c47570)


##### - Senkron Akan Şifreler
##### Kısa bir anahtardan uzunca bir anahtar dizisi üreterek one time pad gibi çalışmayı hedeflemektedir. Gizli anahtar rastgele seçilir. Üretilen anahtar dizisi artık sözde rastgeledir çünkü kısa bir bilgiden çook daha uzun bir bilgi üreteceğimizden mütevellit böyle söyleriz. Dolayısıyla akan şifre alanındaki çalışmaların büyük kısmı ne tür dizilerin rastgelelik özellikleri gösterdiğini tespit etmek üzerinedir. Birçok teknik vardır en güzel örneklerden birisi Linear Feedback Shift Register :
![09](https://github.com/iclalsaritas/Kriptografi/assets/97543719/3fa11d53-1347-4ec8-84f2-3cd46583c0a2)

##### Akan şifreler düz metni küçük parçalar halinde işliyor. Akan şifrelerin blok şifrelerden ennn temel farkı iç durum dediğimiz bir tür hafızalarının olmasıdır. Bu tür iç durum hem şifreleme üzerinde kullanılmak üzere anahtar dizisi üretir hem de kendisini günceller. Bu üretilen anahtar dizisiyle de düz metinle işleme sokma gerçekleştirilerek şifreli metin üretilir. Dolayısıyla şifreleme işlemindeki iç durum, deşifreleme yapacak kişi için de aynı olmalıdır. Başka bir söyleyişle, haberleşecek kişilerin aynı anahtar dizisini üretebilmeleri için senkron olmaları gerekir.
##### ! NOT ! Bazı akan şifreler bir sonraki iç durumu oluştururken düz metni kullanmayabilirler. Bu durumlarda çıktı fonksiyonu anahtar dizisi (keystream) dediğimiz bitleri üretir. Şifreleme fonksiyonuysa anahtar dizisini düz metin ile birleştirir. Bu türdeki akan şifrelere anahtar dizisi üreten şifreler denir.

##### Senkron akan şifrelere son bir özet geçecek olursam :
##### Senkron akan şifrelerin aynı iç durumda olmaları gerekmektedir. Aynı anahtarı kullanmaları gerekmektedir. Senkron bozulursa da deşifreleme başarısız olur haliyle. Senkron nasıl bozulabilir ?
##### Cihazlarda hataların olması en basitinden telefonun yere düşmesi bile buna sebep olabilir. Haberleşme kanalındaki problemler mesela bulunduğun binada çok metal varsa ya da Everest zirvelerinde takılmaca yapıyorsan, fazladan şifreli metin bitlerinin eklenmesi, şifreleri metin bitlerinin silinmesi gibi gibi nedenler başarısızlığa örnek olarak gösterilebilir. 
##### Peki bu bozulmuş senkronu nasıl düzeltirim :
##### En klasik Türk yöntem yeniden başlatma, Belirli aralıklarla özel işaretler yerleştirmek, Tüm anahtar dizilerini tek tek denemek...

##### Aktif bir saldırgan neler yapabilir ?
##### Haberleşme kanalına etki edebilenlere aktif saldırgan ismini veriyoruz. Bu şahıslar iletilmek istenen şifreli metin bitlerini silebilir, değiştirebilir ya da yeni bitler ekleyebilir. Şimdi bahsedeceğim kritik durumu dikkatli okuyun lütfen. Bir şifreli metin bitini değiştirmek diğer bitlerin deşifrelenmesine etki etmez arkadaşlar. E haliyle eğer saldırgan hangi şifreli metin bitini değiştirince düz metinde ne tür bir etki yaratacağını biliyorsa, bu etkiyi yarattığında deşifre eden kişi bundan habersiz olacaktır :( Ama şu da varki, değiştirmek yerine silmek ya da yenileri ekleme hamlesine giriştiyse işler değişir. Yani şifreli metin bitlerini silmek ya da yenilerini eklemek o noktadan sonraki bitlerin deşifrelenmesini etkileyeceği için deşifre eden kişi tarafından aktif saldırganın varlığı anlaşılabilir. Dolayısıyla verinin bütünlüğü ve veri kaynağının doğrulanması için ek önlemler alınmalıdır. Doğrulanmış kriptografi algoritmaları bu problemlere çözümler sunar.

##### - Asenkron Akan Şifreler
##### Asenkron akan şifreler senkron bozulduğunda kendi kendine senkronu geri sağlayabilmektedirler. Bu şifreler bir sonraki iç durumu belirlerken anahtar bitlerini ve daha önce ürettikleri şifreli metin bitlerinin son t tanesini kullanırlar. Aktif bir saldırgan şifreli metin bitlerini değiştirse, silse ya da ekleme yapsa bile deşifre eden kişi t adet şifreli metin bitini düzgün şekilde aldığı anda senkron tekrar sağlanmış olur. Aktif saldırganın yaptığı değişiklikler sadece t adet bitin düzgün deşifre edilmesini engeller. Bu tür akan şifrelerde de verinin bütünlüğü ve veri kaynağının doğrulanması için ek önlemler alınmalıdır. 
____________________________________________________________________________________________________________________________________________________________________________________________________________________________

#### 4) Özet (Hash) Fonksiyonlar
##### Farklı uzunluklarda girdi alabilip hep aynı n bit uzunlukta çıktı veren fonksiyonlara özet fonksiyon değil. 
##### Kriptografik özet fonksiyonların şu özellikleri sağlamasını bekleriz :
##### Ön görüntü dayanıklılığı, ikinci ön görüntü dayanıklılığı ve çakışma dayanıklılığı. Ayrıca çıktıların rastgelelik özellikleri göstermesini bekliyoruz.

##### 1. Ön Görüntü Dayanıklılığı : Bir y çıktısı verildiğinde, bu çıktıyı verecek bir x girdisi bulmak zor olmalıdır h(x)=y . Bir kaba kuvvet saldırısı 2^n deneme gerektirmelidir. Örnek :
##### Bir veritabanında parolaları (Kullanıcıadı,parola) şeklinde tutmak yerine (Kullanıcıadı,h(parola)) şeklinde tutmak gerekir. Veritabanını çalan bir saldırgan kullanıcı parolasını ele geçirebilmek için kullanılan özet fonksiyonda ön görüntü bulması gerekmektedir. 
##### 2. Ön Görüntü Dayanıklılığı : Bir y çıktısı h(x1)=y eşitliği sağlayan x1 girdisi verildiğinde, h(x2)=y eşitliğini sağlayacak ikinci bir x2 girdisi bulmak zor olmalıdır. Bir kaba kuvvet saldırısı 2^n deneme gerekirmelidir. Örnek :
##### Bilgisayarlarınızdaki ya da bulut dosyalarınızın özet değerlerini tutun. Eğer saldırgan dosyalarınıza zararlı bir yazılım yüklediğinde hala aynı özet değerini veriyorsa, saldırgan sizi ya da bulut hizmeti sunucusunu kandırabilir.
##### 3. Çakışma Dayanıklılığı : h(x1)=h(x2)= y eşitliğini sağlayacak iki x1 ve x2 girdisini bulmak zor olmalıdır. Bir kaba kuvvet saldırısı doğum günü paradoksu nedeniyle 2^n/2 deneme gerektirmelidir. Örnek :
##### Hacker hazırladığı x1 sürücü dosyası için eğer çakışma güvenliği yoksa bu sürücünün içine zararlı kodlar ekleyip oluşturduğu x2 sürücü dosyası ile aynı y değerini elde edebilir. Hacker işletim sistemi firmasına x1 analiz için gönderir. x1 zararsız olduğu için işletim sistemi firması h(x1)= y değerini elektronik olarak imzalar. Hacker zararlı kod içeren x2 sürücüsünü kullanıcılara ulaştırdığında h(x2)= y olduğu için işletim sistemi bu sürücüyü imzaladığını düşünecek ve zararsız olduğunu zannedecek :(
##### Ha bu arada doğum günü paradoksu ne ola ki ?
##### Bir odada en az kaç kişi olduğunda, aynı doğum gününe sahip iki insanın o odada bulunma ihtimali 1/2'den fazla olur? Bu sorunun cevabı daha fazla beklendiğinden paradoks olarak isimlendirilmiştir. Çünkü cevap 23.

##### - Blok Şifreden Hash Fonksiyon Tasarlamak
##### Özet fonksiyonlar kriptografide çok yoğun şekilde kullanıldığı için kriptografinin İsviçre Çakısı olarak bilinir. Bazı örnekler :
##### Dijital imza, mesaj doğrulama kodları, rastgele sayı üreteçleri, anahtar üretme fonksiyonları...
![zz](https://github.com/iclalsaritas/Kriptografi/assets/97543719/d18bf776-74ec-449d-a98b-986ff6f087fb)

##### - MD4 
##### Blok şifre kullanmayıp kendimiz tasarlamak istersek buna en eski örnek şüphesiz MD4 olur. Ronald Rivest tarafından 1990'da tasarlanmıştır. Blok uzunluğu 512 bit, özet uzunluğu 128 bit, döngü sayısı 48 dir.
##### Çakışma Dayanıklılığı : Çakışma üretme mikrosaniye sürüyor. 
##### Ön Görüntü Dayanıklılığı : 2^95 işlem.
![jjj](https://github.com/iclalsaritas/Kriptografi/assets/97543719/50e38edd-e6ca-44c7-87e6-c580cfb82385)

##### 2011'e kadar IETF standardıydı ve kendisinden sonraki birçok tasarımı etkiledi. MD5, SHA1...
##### - MD5
##### Yine Ronald Rivest tarafından 1991'de MD4'ün yerine geçmesi için tasarlanmıştır. Blok uzunluğu 512 bit, özet uzunluğu 128 bit, döngü sayısı 64.
##### Çakışma Dayanıklılığı : Çakışma üretmek için 2^18 işlem yetiyor yani 1 saniyeden kısa. 
##### Ön Görüntü Dayanıklılığı : 2^123.4
![qqq](https://github.com/iclalsaritas/Kriptografi/assets/97543719/93d97b46-b5a7-4138-8dd6-229144e135cb)

##### 2004 yılında aynı MD5 özeti verecek iki farklı dosyanın nasıl yaratılacağı gösterildi. 2008 yılında sahte SSL sertifikası oluşturmanın mümkün olduğu gösterilmiş ve sertifika otoritelerinin MD5 kullanmayı bırakmaları tavsiye edildi. 2012 yılında Flame zararlı yazılımı MD5 çakılmalarını kullanarak sahte Windows kod imzalama sertifikası kullanıldı. Kriptografik açıdan kabul edilmesi imkansız bir çakışma örneği :
![ççç](https://github.com/iclalsaritas/Kriptografi/assets/97543719/bcfc9e10-7421-4c57-a34d-37350610eec5)

##### Özellikle de bulut hizmetlerinde MD5 kullanılması sistemin darmadağın olmasını kaçınılmaz kılacaktır. Kullanıcıların dosyaları bekledikleri gibi çalışmayacaktır çünkü bazı parçalar başka dosyalarla aynı özet değerlerini vereceği için dosyalar bir noktadan sonra bozulacaktır.

##### - SHA1
##### 1993 yılında NSA tarafından tasarlandı. Blok uzunluğu 512 bit, özet uzunluğu 160 bit, döngü sayısı 80 dir.
![cvc](https://github.com/iclalsaritas/Kriptografi/assets/97543719/1704bcde-09ad-4795-a8ea-a46620f8bdaf)

##### 2017 yılında Google ekibi tarafından çakışma örneği tespit edilmiştir.

##### - SHA2
##### 2001 yılında yine NSA tarafından tasarlandı. Blok uzunluğu 512 veya 1024 bit, Özet uzunluğu 224, 256, 384 ve 512 bit, döngü sayısı 64 veya 80 bit. Kırılmamış özet fonksiyonu olarak SHA2 örnek verebiliriz.
![ııı](https://github.com/iclalsaritas/Kriptografi/assets/97543719/347af279-41e9-4daf-b5c1-bc66298a6c4b)

##### - SHA3
##### MD4, MD5 ve SHA1 kırıldı ve geriye sağlam kalan SHA2 kaldı ve önceki tasarımlara benzeyen bir yapısı var. O yüzden eşeği sağlam kazığa bağlama niyetiyle SHA3 yarışması düzenlendi NIST tarafından (2007-20012).
##### SHA3 blok uzunluğu 1152, 1088, 836, 576 bit, özet uzunluğu 224, 256, 384, veya 512 bit, Döngü sayısı 64 veya 80 bit. Yarışmayı Keccak kazandı ve SHA3 ismini aldı. SHA2 ve SHA3 dışında kullanımlardan kaçınılmalı.
![bbbbbbbbb](https://github.com/iclalsaritas/Kriptografi/assets/97543719/d70c21f9-091f-48ca-8555-0c40a0800173)

##### - Parola Kırmak
##### Parolalarınızı asla kaydetmemelisiniz. Onun yerine özetlerini tutmalısınız. Bu sayede sızan veritabanınlarındaki veritabanları güvende kalır. Bunun için özet fonksiyonunun ön görüntü dayanıklılığının olması gerekir.
##### Sözlük Saldırısı : Bir sözlükteki kelimelerin, birbirleriyle ve sayılarla kombinasyonlarının özetleri önceden hesaplanır. Bu değerler sıralı bir şekilde bir tabloda tutulur. Saldırgan ele geçirdiği veritabanında kendi tablosunda da olan özet değerleri bulursa o parolaları elde eder.
##### Çözüm : Parola özeti yerine rastgele üretilmiş bir salt değeri parola sonuna eklenerek parola|salt özeti veritabanında tutulur. Dolayısıyla sözlük saldırısı yapacak saldırganın her salt değeri için önceden ayrı bir tablo oluşturması gerekir lakin bu işlem ve hafıza gereklilikleri nedeniyle mümkün değildir.
##### Kaba Kuvvet Saldırısı : Özet değeri ele geçirildikten sonra her parola tek tek denenir. Kullanıcıların kısa ve kolay hatırlanır parolalar seçtiği durumlarda işe yarar.
##### Çözüm : Bir parolanın özetini kullanmak yerine, o özet çıktısını tekrar tekrar özet fonksiyonuna sokarak en son elde edilen özet değerini kullanabiliriz. Mesela bu işlemi 10000 kez yaparsak saldırganın işi 10000 kat zorlaşacaktır.
____________________________________________________________________________________________________________________________________________________________________________________________________________________________

#### 5) Açık Anahtar Kriptografisi
##### Esas hedefler güvenli mesaj transferi, kimlik doğrulama (Dijital imza) ve anahtar değişimidir (Bu sayede güvensiz bir haberleşme kanalı üzerinden simetrik anahtar transferi mümkün olmuştur)

##### - Diffie-Hellman Anahtar Değişimi
##### Ayrık Logaritma Problemi : Önceden belirlenen g ve p sayıları için a bilindiğinde g^a = b (mod p) hesaplamak kolaydır. b verildiğinde g^a = b mod eşitliğini sağlayan a sayısını bulmak zordur. Örnek :
##### 3^x = 7376884875361470534 (mod 18446744073709551615) cevap 127002 . X yerine 1'den başlayıp yazmaya başlasak 127002 denemeden sonra sonucu bulacağımız anlamına gelir saldırı yaparken. Lakin pratikte sayılar daha büyük olduğundan kaba kuvvet saldırısı biraz daha uzun sürecektir.
##### A kişisi rastgele bir a sayısı seçip B'ye g^a (mod p) sayısını yollasın. B kişisi rastgele bir  b sayısı sçeip A'ya g^b (mod p) sayısını yollasın. A kişisi (g^a)^b = g^ab (mod p) sayısını hesaplasın. B kişisi (g^a)^b = g^ab (mod p) sayısını hesaplasın.
##### ![zzz](https://github.com/iclalsaritas/Kriptografi/assets/97543719/206d0bd3-cd3a-4789-9473-8be0d0b3689b)

#####  - RSA Şifreleme Algoritması
##### En temel haliyle, iki büyük rastgele asal sayı seçeriz. p ve q diyelim bunlara. n = pq hesaplanır. e sayısı seçilir 2 < e < n-1  ((p-1)(q-1) = 1) . d = e^-1 mod ((p-1)(q-1)) hesaplarız. 
##### Açık anahtarımız (n,e) , Gizli anahtarımız d ( p ve q sayılarını da gizli tutman lazım aklında olsun.) 
##### Şifreleme 0 < m < n -1 mesajı için c = m^e mod(n) hesaplanır. Deşifreleme m = c^d mod(n)
![ööö](https://github.com/iclalsaritas/Kriptografi/assets/97543719/8039f12a-bf95-4e28-85aa-7451554761cf)

##### - El-Gamal Şifreleme Algoritması
##### El Gamal Şifreleme için anahtar üretimi yaparken rastgele bir x seçeriz. y = g^x hesaplarız. Burada açık anahtar y, gizli anahtar x dir. Şifreleme işleminde şifreleme için rastgele r seçeriz (u=g^r, v=my^r) ve yollarız. Deşifreleme için vu^-x = m işlemiyle mesaj m yi elde ederiz.
![hhh](https://github.com/iclalsaritas/Kriptografi/assets/97543719/fd1fee99-293c-4ed9-9a97-2bb413eafe3d)


##### - Dijital İmza Standardı
#####  Parametre üretimi yapmak söz konusuysa özen göstermemiz gereken mevzular vardır. Bunlar :
##### İyi bir hash fonksiyonu seçmek (SHA2-SHA3 gibi) imzalarken hiçbir zaman mesajı değil özetini imzalarsın çünkü , anahtar uzunlukları L ve N (3072,256) , n bitlik q asal sayısı seçmek, L bitlik asal p modu seçmek öyle ki p-1 sayısı q sayısının bir katıdır. g sayısı seçmek lakin seçerken de çarpma grubu eleman sayısı mod p'de q olacak şekilde seçmelisin. Son olarak parametreler (p,q,g) kullanıcılar arasında paylaşılabilir. Kullanıcı anahtarı üretimine gelirsek,  rastgele bir x gizli anahtarı seçilir öyle ki 0 < x < q , açık anahtar y hesaplanır y = g^x mod p . Son olarak da imzalama işlemine bakalım. İmzalama işlemi için her mesaj için rastgele k sayısı seçilir öyle ki 0 < k < q ,  r = (g^k mod p) mod q hesaplanır. m mesajı için  s = k^-1(hash(m)+xr) mod q hesaplanır. Sonuç olarak (r,s) ikilisi imzadır. Doğrulama işlemi için ise : w = s^-1 mod q hesaplanır. u1 = hash(m).w mod q hesaplanır. u2 = r.w mod q hesaplanır. v = (g^u1 x y^u2 mod p) mod q hesaplanır. Eğer v = r ise imza geçerlidir.
![ççç](https://github.com/iclalsaritas/Kriptografi/assets/97543719/89e38792-c6f8-468e-a992-4deec122a77d)

____________________________________________________________________________________________________________________________________________________________________________________________________________________________

##### | Bu içerik umarım temel bir bakış kazanmanıza yardımcı olmuştur. Sorularınız olursa çekinmeden yazın. Teşekkürler |
