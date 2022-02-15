# Tutorial Codeigniter 4 untuk Pemula | #3. Codeigniter Folder Structure

## Poin poin penting

### Penjelasan dari struktur index.php
1. berisi apa yang akan ditampilkan bisa dikoneksikn asset, javascript dll

### File konfigurasi env 
1. ubah kode berikut (pilih salah satu)      
        CI_ENVIRONMENT = <production, development, testing>
2. app.baseURL merupakan base dari URL kita ketika sudah di upload
3. konfigurasi databse samakan dengan configurasi xampp kita

### File writable
1. file yang menyimpan session

### Vendor
1. vendor akan berisi ketika menggunakan dependency atau library

### Folder app
1. Folder inti untuk mengatur dari code igniternya

### Routes
1. penjabaran : $routes->setDefaultController('Home');
merupakan routes pengambilan dari class Home
class home ada di controller, ketika masuk ke class Home maka yang akan dijalanakna telebiuh dahulu adalah index

### Controller Home
1. ketika dibuka file ini maka ada index. index tersebut mengawah kpenampilan views


### Views 
1. merupakan tempat untuk menmapilkna user interface kepada pengguna

### Models
1. Pengambilan database
        
                
