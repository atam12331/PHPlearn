# Routes

Ada beberapa aturan mendasar ketika hendak mengatur routes dalam ci 4. routes sendiri bertujuan untuk mengakses erb supaya lebih ringkas tanpa harus melhat dan mengetikkan kelasnya di dalam url.
contoh codingan untuk routes yang membara variable
```
$routes->add('halaman/detail/(:any)', 'Halaman::halaman_detail/$1');
```

ada beberapa catatan tambahan untuk pengaturan any. salah satunya adalah
* :any => apasaja
* :num => nama
* :alpha => alphabet(hanya huruf)
* :alphanum => angka dan huruf

untuk bagian belakang $1 dan $2 itu harus berurutan sesuai denganinputan jumlahnya

> Poin Penting, routes bentuk dari khusus dulu baru umum, untuk urutannya.

contoh :
```
$routes->add("halaman/detail/(:num)", "Halaman::halaman_detail_by_id/$1");
$routes->add("halaman/detail/(:any)", "halaman::halaman_detail_by_judul/$1");
```
code diatas merupakan dari sempit ke umum dengan aturan num dulu baru any(umum)

---
## Aturan get, add
ketika ingin membuat routes sesuaikan aturan routes dengan perintah dari kelas dan function. mengapa demikian? karena ketika di dalam functionnya tersebut meminta get maka di dalam routes juga harus diganti menjadi get

---
## Aturan Grouping di dalam routes
membuat routes merupakan hal yang wajib ketika ingin mempercantik tampilan url dari ci4. nah dalam ci 4 kali ini udah disediakan fitur grouping yang dimana dari grouping ini mempermudah ketika ada file controller di dalam file lagi. contohnya disini saya akan membuat routes ari file controller di folder admin yang didalamnya ada file :
1. foto.php
2. portofolio.php
codenya :
```
$routes->group('admin', function ($routes) {
    $routes->add("gallery", "Admin\Foto::index");
    $routes->add("karya", "Admin\Portofolio::index");
```
penjelasan :
dalam code tersebut dijelaskan bahwa 2 routes dibawahnya dapat diakses setelah url admin. dan dapat di ubah. ini lebih efektif dari pada :

```
$routes->add("admin\gallery", "Admin\Foto::index");
$routes->add("admin\karya", "Admin\Portofolio::index");
```
