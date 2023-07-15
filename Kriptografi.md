###### Merhaba! Kriptografi için nereden başlayacağını bilemiyor ve kaynak arıyor olabilirsin. Emin ol doğru yerdesin. Tarihsel süreçten, akan şifrelere doğru gidilecek bu yolda yeterli çalışma motivasyonuna sahipsen ve içeriğimi okumaya hazırsan daha fazla bekleme, hemen başla :) İlerlememiz şu başlıklar altında olacaktır :

#### 1) Kriptografi Tarihsel Serüveni
##### - Temel Kavramlar Hakkında Bilgi Kazandırmak
##### - Frekans Analizleri
##### - Tarihî Şifreler
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
##### Harika bir çizimle işi özetleyip Frekans Analizi konumuza geçiş yapıyorum.
![1](https://github.com/iclalsaritas/Kriptografi/assets/97543719/6f6c9da0-ee21-48b8-afa6-4d8adff2c068)

##### - Frekans Analizleri
