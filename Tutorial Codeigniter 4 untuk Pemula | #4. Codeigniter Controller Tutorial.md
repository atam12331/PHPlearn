# Tutorial Codeigniter 4 untuk Pemula | #4. Codeigniter Controller Tutorial

## Penjelasan

Ketika mengakses halaman maka utamakan class dulu baru kemudian beralih ke function. function akan memberikan ke folder views untuk ditampilkan di user.
Struktur penjelasan dari alamat 
            
            public/siswa/siswa_detail/Bahasa
            <alamat_base>/<class>/<function>/<parameter>
            
 Catatan setelah parameter mengikuti parameter lagi dan seterusnya
 
 ___
 
             protected function validasi()
    {
        echo "Saya adalah fungsi protected untuk validasi";
    }



Apabila terdapat strucutur kelas dengan tipe protected maka ketika kelas dipanggil di URL itu tidak akan muncul, melainkan ara memanggilnya adlah memberikan perintah

        $this -> <namafunction>()
        
Baru bisa muncul.

---

Ketika ada kasus 2 penampil dalam satu kelas di controller maka akan di eksekusi untuk penampil yang paling atas. contohnya :

          function siswa_detail($kelas, $idsiswa)
        {
            echo "<h1>Saya fungsi siswa detail dengan kelas $kelas dengan id $idsiswa</h1> ";
            return view("siswa");
            $this->validasi();
        }

Dari potongan kode diatas ada 2 penampil yaitu return view, dan $this->... supaya CI tidak bingung maka harusdihapus salah satunya

---

Apabila ingin membuat folder dalam controoler bisa saja dilakukan untuk berbeda mengakses filenya, pada code class diatas terdapat namespace maka ubah directorynta :

        namespace App\Controllers\admin;
        <library> <directoryApp>\<directoryControllers>\<DirectoryAdmin>
        
Namun, setelah paste bisanya akan ada error di bagian basecontrooler. maka harus ditambahkan code ini dibawah dari namespace

        use App\Controllers\BaseController;
        
---   
   
untuk mengakses controller lain yang berada **berbeda folder** maka inisiasikan dulu directory menjadi objek, taruh di head file 

        use App\Controllers\admin\Siswa as Adminsiswa;
        <syntax> <dir>\<dir>\<dir>\<dir> <syntax> <objek_bebas>;
        
Kemudian pada class yang digunakan untuk menampilkan isikan kode 

         $Adminsiswa = new Adminsiswa();
         <objek> = new <objek_dari_directory>
         
         $Adminsiswa->index();
         <objek> -> <class_dalam_objek>;
