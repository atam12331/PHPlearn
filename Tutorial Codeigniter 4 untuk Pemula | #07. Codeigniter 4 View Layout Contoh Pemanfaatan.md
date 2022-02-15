# Tutorial Codeigniter 4 untuk Pemula | #07. Codeigniter 4 View Layout Contoh Pemanfaatan
## Section pada CI4
hubungkan 2 section header dan footer kemudian pada bagian konten tengah buka tag php dan masukkan code ini :

```
echo $this->renderSection("konten_utama")
```

pada file yang akan dituju untuj memasukkan konten utamanya (badan konten web) maka tuliskan :

```
<?php echo $this->extend("layout\layout_utama") ?>
<?php echo $this->section("konten_utama") ?>
  
  <code badan HTML>
    
<?php echo $this->endSection(); ?>
```

berbeda kasus ketika kita sudah memanggil konten utama namun, kita hendak menambahkan kembali komponen, contoh sidebar.
kita akan menambahkan sidebar pada konten utama dengan mengguanakan script
    
```
<Code badan HTML>
  <?php echo $this->include("component\sidebar") ?>
<code badan HTML
 ```
