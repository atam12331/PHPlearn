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
