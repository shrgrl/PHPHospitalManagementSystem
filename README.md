# PHPHospitalManagementSystem
## PhP ile MySQL Veritabanı Bağlantısı Yapma
Php kullanarak yazdığımız projelerde genellikle veritabanı yönetim işleri MySQL üzerinden gerçekleştirilir. PHP ile bir SQL veritabanına bağlanmanın iki yöntemi bulunuyor, MySQLi ve PDO. Öncelikle bir MySQL veri tabanı oluşturmamız gerekli. Daha önce başka bir projede veri tabanı oluşturma hakkında bilgi vermiştik. Buradan ulaşabilirsiniz: <strong> "https://github.com/shrgrl/JavaHospitalManagementSystem#mysql-veri-taban%C4%B1" </strong><br> 
Veri tabanını oluşturduktan sonra php kodlarını yazmaya başlayabiliriz.<br>
Veri tabanı bağlantısı değişken bir obje oluşturarak sağlanır:
```php
$my_Object = new Object();
```
Örnek bir php kodu üzerinde inceleme yapalım:
```php
$conn = mysqli_connect("localhost", "my_user", "my_password", "my_database");
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}
echo "Connected successfully";
mysqli_close($conn);
```
Bu script’de kullanılan ana yöntem mysqli_connect() metodudur. Mysqli_connect() metodu, MySQL sunucusuna yeni bir bağlantı açar.<br> 
Sözdizimi: <strong> "mysqli_connect (host, username, password, dbname, port, socket); </strong> şeklindedir.<br>
Projenin ana sayfasına sekmeler ekleyerek diğer projeyle benzer şekilde doktor, hasta ve admin girişleri ile işlemler sağlamayı düşünüyorum. Admin, bütün işlemleri kontrol edebilir olacak.<br>
İlk etapta bir veri tabanı oluşturmam gerekecek. Bu veri tabanına ekleyeceğim elemanların taslağını oluşturdum. Admin, randevu, doktor bilgilerini içeren bir doktor tablosu, giriş yapabilmeleri için kullanıcı adı ve parola içeren farklı bir doktor tablosu, branşlarına göre ayırabilmek için bir doktor tablosu ve herhangi bir kullanıcının giriş yapması için ve bilgilerini tutmak için tablolar oluşturacağım.
<br>Hastane yönetim sistemi projemin ilk etabı veri tabanı oluşturmaktı. Projemin veri tabanı 7 adet tablodan oluşuyor:

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/image1.jpg)

<br>Tabloların her birine birkaç içerik ekledim. Örnek olarak:
<br><strong> Doktor tablosu: </strong>

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/image2.jpg)

<br><strong> Kullanıcılar tablosu: </strong>

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/image3.jpg)

## Projenin Çalıştırılması
Projeyi çalıştırmak için ilk önce bilgisayarımızda yüklü bulunan XAMPP programını açıp, <i>Apache</i> ve <i>MySQL</i> seçeneklerini <strong>Start</strong> etmemiz gerekiyor.

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/img1.JPG)

<br>Ardından web tarayıcımıza <strong>localhost</strong> yazıyoruz ve önceden veritabanına eklemiş olduğumuz projemizi seçiyoruz.

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/img2.JPG)

<br>Son olarak src seçeneği, tıkladığımızda bizi ana sayfaya yönlendirecektir.

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/img3.JPG)
## Site Tasarımı
Projenin ana sayfa tasarımında sekmeler ekledim ve ulaşmak istediğimiz sayfalara bağlantıları buradan sağlayacağız.

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/image4.jpg)

<br>Şu an bulunduğumuz sayfa Ana Sayfa. İletişim’e tıklayıp iletişim bilgilerini görebiliriz. Hastalar sekmesinde hasta girişi, diğerlerinde de aynı şekilde doktor girişi ve admin girişi olarak giriş yapabiliriz. Ayrıca ana sayfada html kodda slider ile görüntü efekti kullanarak modern bir tasarım elde etmeye çalıştım ve onun için hazır <strong> responsiveslides.min.js </strong> kullandım:

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/image5.jpg)

<br>Bu fonksiyon ile sliderin maksimum genişliğini ve hızını belirttik:
```javascript
<script>
    $(function () {
        $("#slider1").responsiveSlides({
        maxwidth: 1600,
        speed: 600
        )};
    )};
```
<br>Aşağıdaki kod parçası ise sliderin kaç tane resimden oluşup onların sıralaması belirtiyor :
```javascript
<div class="image-slider">
    <ul class="rslides" id="slider1">
        <li><img src="images/slider-image1.jpg" alt=""></li>
        <li><img src="images/slider-image2.jpg" alt=""></li>
        <li><img src="images/slider-image1.jpg" alt=""></li>
    </ul>
</div>
```
## İletişim
Bir sitenin olmazsa olmazlarından biri de kişilerin muhataplarına direk ulaşabilme olanağıdır. Bütün sitelerde olmazsa olmaz “İletişim” sekmesine tıkladığımızda karşımıza çıkan sayfa şu şekilde;

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/image6.jpg)

## Hastalar
Projenin “Hastalar” sayfasına giriş için tıkladığımızda karşımıza bir giriş sayfası çıkıyor.

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/image7.jpg)

<br>İlk etapta daha önce veri tabanında belirlediğim hasta bilgileri ile giriş yapabiliyorum. Veri tabanına bilgi ekleyebilmenin yanı sıra hastaların bu sayfa yolu ile üyelik hesabı oluşturulabilir. Aşağıda bulunan “Hesap oluştur” kısmına basmak bunun için yeterli. 

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/image8.jpg)

<br>Tıkladığımızda karşımıza kayıt sayfası çıkacak. Bu sayfada istenilen bilgileri girip “Gönder” butonuna tıkladığımızda veri tabanına bir üye daha eklemiş oluyoruz ve eklediğimiz üyelik kullanıcı adı ve şifresi ile giriş yapabiliyoruz. Giriş yaptıktan sonra karşımıza çıkan sayfa aşağıdaki gibidir. Sağ üst köşedeki isme tıkladığımızda profil görüntüleme, şifre değiştirme ve çıkış yapma seçeneklerimiz olacak. Karşımıza çıkan ilk sayfa “Kontrol Paneli” sayfası. Diğer sekmelerde de randevu oluşturma ve oluşturulan randevuları görüntüleme seçeneklerimiz mevcut. Ayrıca sayfalarda hazır bootstrap modülleri mevcut: sidebar, toolbar vs.

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/image9.jpg)

## Doktor Girişi
Projede hastaların yanı sıra doktorlar için de geçmiş randevularını görüntüleme ihtiyaçları duyduklarında veya mevcut profillerini güncellemek istediklerinde ihtiyaçlarını karşılamak için imkan sunuluyor. Hastalar gibi doktorlar da şifrelerinde değişiklik yapabiliyor.

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/image10.jpg)

<br>Profili güncelle seçeneğine tıkladığımızda aşağıda görünen sayfa karşımıza çıkıyor. Değişiklik yapmak istediğimiz kısımlara uyguladığımız değişikliklerden sonra “Güncelle” seçeneğine tıkladığımızda bilgilerimiz güncellenmiş oluyor.

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/image11.jpg)

## Admin Girişi
Admin sayfasında diğerlerine kıyasla çok daha fazla özellik mevcut. Sonuç olarak sitenin yöneticisi konumunda olduğu için her olaya, veriye müdahale edebilecek bir pozisyonda olmalı. Giriş yaptıktan sonra karşımıza çıkan sayfa şu şekilde;

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/image12.jpg)

<br>Burada admin, doktor, hasta ve randevu bilgilerini görüp müdahale edebiliyor. Örneğin hastaneye yeni gelen bir doktor için kayıt oluşturabiliyor.

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/image13.jpg)

<br>“Doktor Uzmanlığı” seçeneğinde sağlamasını düşündüğüm avantaj, hastaneye mevcut olmayan bir bölüm açıldığı zaman direkt olarak buradan yeni bir bölüm ekleyebileceğiz. “Doktor Ekle” seçeneği ile de bölümün doktorunun kaydını yaparak hastaların hizmetine sunacağız.

![](https://github.com/shrgrl/PHPHospitalManagementSystem/blob/master/images/image14.jpg)

<br>Burada yaptığımız değişiklikler veri tabanında aynı şekilde güncellenecek.
