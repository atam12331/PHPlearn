# Tutorial Codeigniter 4 untuk Pemula | #2. Cara Install Codeigniter 4 di Xampp dan Melalui Composer

## Poin poin penting

### installasi website
1. Pertama download melalui websitenya kemudian pastekan ke htdocs setelah itu buka melalui vs code
2. Hal pertama yang dilakukan adalah rename env menjadi .env
3. Ketika ada error :

        CodeIgniter\Exceptions\FrameworkException
        
    Maka bukalah php.ini kemudian cari bagian intl hapus titik koma depan intl
4. Restart untuk apache dan MySQLnya


### installasi composer
1. pastikan hapus titik ; di intl pada php.ini
2. kemudian masukan perintah install by composer (cek dokumentasi ci4 install by composer)
