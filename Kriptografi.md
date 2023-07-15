###### Merhaba! Kriptografi için nereden başlayacağını bilemiyor ve kaynak arıyor olabilirsin. Emin ol doğru yerdesin. Tarihsel süreçten, akan şifrelere doğru gidilecek bu yolda yeterli çalışma motivasyonuna sahipsen ve içeriğimi okumaya hazırsan daha fazla bekleme, hemen başla :) İlerlememiz şu başlıklar altında olacaktır :

#### 1) Kriptografi Tarihsel Serüveni
##### - Temel Kavramlar Hakkında Bilgi Kazandırmak
##### - Tarihî Şifreler 
##### - Frekans Analizi
##### - Enigma
##### - Blok Şifreler

#### 2) Blok Şifreler 
##### - Şifre Tasarımı
##### - Feistel Şifreler ve DES
##### - AES ve Brute Force Saldırısı
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


