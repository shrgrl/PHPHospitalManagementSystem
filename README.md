# PHPHospitalManagementSystem
## PhP ile MySQL Veritabanı Bağlantısı Yapma
Başka bir projede veri tabanı oluşturma hakkında bilgi vermiştik. Buradan ulaşabilirsiniz: <strong> "https://github.com/shrgrl/JavaHospitalManagementSystem#mysql-veri-taban%C4%B1" </strong>
Php kullanarak yazdığımız projelerde genellikle veritabanı yönetim işleri MySQL üzerinden gerçekleştirilir. PHP ile bir SQL veritabanına bağlanmanın iki yöntemi bulunuyor, MySQLi ve PDO. Öncelikle bir MySQL veri tabanı oluşturmamız gerekli. Daha önce MySQL’den bahsederken yeni bir veri tabanını nasıl oluşturacağımı öğrenmiştim. Veri tabanını oluşturduktan sonra php kodlarını yazmaya başlayabiliriz.<br>
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
İlk etapta bir veri tabanı oluşturmam gerekecek. Bu veri tabanına ekleyeceğim elemanların taslağını oluşturdum. Admin, randevu, doktor bilgilerini içeren bir doktor tablosu, giriş yapabilmeleri için kullanıcı adı ve parola içeren farklı bir doktor tablosu, branşlarına göre ayırabilmek için bir doktor tablosu ve herhangi bir kullanıcının giriş yapması için ve bilgilerini tutmak için tablolar oluşturacağım.<br>
Hastane yönetim sistemi projemin ilk etabı veri tabanı oluşturmaktı. Projemin veri tabanı 7 adet tablodan oluşuyor:
SAYFA31 RESİM1
Tabloların her birine birkaç içerik ekledim. Örnek olarak:
<strong> Doktor tablosu: </strong> RESİM2
<strong> Kullanıcılar tablosu: </strong> RESİM3
## Site Tasarımı
Projemin ana sayfa tasarımında sekmeler ekledim ve ulaşmak istediğimiz sayfalara bağlantıları buradan sağlayacağız. RESİM4
Şu an bulunduğumuz sayfa Ana Sayfa. İletişim’e tıklayıp iletişim bilgilerini görebiliriz. Hastalar sekmesinde hasta girişi, diğerlerinde de aynı şekilde doktor girişi ve admin girişi olarak giriş yapabiliriz. Ayrıca ana sayfada html kodda slider ile görüntü efekti kullanarak modern bir tasarım elde etmeye çalıştım ve onun için hazır <strong> responsiveslides.min.js </strong> kullandım : RESİM5
Bu fonksiyon ile sliderin maksimum genişliğini ve hızını belirttik:
```javascript
<script>
    $(function () {
        $("#slider1").responsiveSlides({
        maxwidth: 1600,
        speed: 600
        )};
    )};
```
Aşağıdaki kod parçası ise sliderin kaç tane resimden oluşup onların sıralaması belirtiyor :
```javascript
<div class="image-slider">
    <ul class="rslides" id="slider1">
        <li><img src="images/slider-image1.jpg" alt=""></li>
        <li><img src="images/slider-image2.jpg" alt=""></li>
        <li><img src="images/slider-image1.jpg" alt=""></li>
    </ul>
</div>
```
