# Tutorial Codeigniter 4 untuk Pemula | #6. Mengenal VIEW_CELL di Codigniter 4
## 15-02-2022

### View Set
Penggunaan view set hampir seperti fungsi pada umumnya hanya saja pembuatan filenya berada di folder library
file codingan dalam library conothnya :
```
<?php 
namespace App\Libraries;

class Lib_halaman
{
    function info()
    {
       return "Ditulis di Kategori : <b>Berita</b>, Penulis : <b>Atam</b>";
    }
}
```

sehingga pada menu halaman di view harus merujuk kepada libraries tersebut, uabhlah view menjadi seperti berikut :
```
<body>
    <h1>
        <?php echo $judul_halaman ?>
    </h1>
    <?php echo view_cell("\App\Libraries\Lib_halaman::info") ?>
    <div>
        <?php echo $isi_halaman ?>
    </div>
    <div>
        <ul>
            <?php
            foreach ($gerakan5m as $k => $v) {
                echo "<li>$v</li>";
            }
            ?>
        </ul>
    </div>
```

---

ketika ingin menambahkan parameter pada bagian folder library dan view maka codingannya akan menjadi :
```
<?php

namespace App\Libraries;

class Lib_halaman
{
    function info($parameter)
    {
        return "Ditulis di Kategori : <b>" . $parameter['kategori'] . "</b>, Penulis : <b>" . $parameter['penulis'] . "</b>";
    }
}
```
dan di halaman bagian folder view menjadi 
```
<body>
    <h1>
        <?php echo $judul_halaman ?>
    </h1>
    <?php echo view_cell("\App\Libraries\Lib_halaman::info", ['kategori' => 'Berita', 'penulis' => 'Bayi']) ?>
    <div>
        <?php echo $isi_halaman ?>
    </div>
    <div>
        <ul>
            <?php
            foreach ($gerakan5m as $k => $v) {
                echo "<li>$v</li>";
            }
            ?>
        </ul>
    </div>
```

---

Ada satu kasus saling melempar data pada detik terakhir, yang aku mengerti ini datanya ditulis di dalam folder library tapi dilembpar pembacaannya di views, dan views ini nanti ditamngkap oleh kontroller dengan parameter tertentu




