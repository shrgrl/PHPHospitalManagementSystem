# PHPHospitalManagementSystem
## PhP ile MySQL Veritabanı Bağlantısı Yapma
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
Sözdizimi: <strong> mysqli_connect(host,username,password,dbname,port,socket); </strong> şeklindedir.


