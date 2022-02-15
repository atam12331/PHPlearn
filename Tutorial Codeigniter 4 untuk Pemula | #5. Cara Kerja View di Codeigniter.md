# Tutorial Codeigniter 4 untuk Pemula | #5. Cara Kerja View di Codeigniter
### 15-02-2022

## Penjelasan View
 Biasakan pemecahan antara header body dan footer
 
 Ketika ingin membuat segmen yang harus diperhatikan adalah di controller tidak serta merta me return semua melainkan harus di echo.
 contoh yang benar :
 ```
 class Halaman extends BaseController
{
    public function index()
    {
        echo view('header');
        echo view('halaman');
        echo view('footer');
    }
}
 ```
 
 contoh yang salah :
 ```
 class Halaman extends BaseController
{
    public function index()
    {
        returm view('header');
        return view('halaman');
        return view('footer');
    }
}
 ```
 ---
 
 Contoh penggunakan foreach pada php untuk memunculkan data didalam view :
 pada controller :
 ```
 $data['title'] = 'Pengiriman Data Waspada';
        $data['judul_halaman'] = 'Tetap waspada ya atam';
        $data['isi_halaman'] = 'Semoga sehat sealau';
        $data['gerakan5m'] = ['Memakai Masker', 'Mencuci Tangan', 'Menjaga Jarak', 'Menjauhi Kerumunan', 'Membatasi mobilisasi'];

        echo view('header', $data);
        echo view('halaman', $data);
        echo view('footer');
 ```
 
 Pada view :
 ```
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
 
 Masih mengacu pada code yang sama, apabila ingin mengelompokkan view di folder konten berbeda maka sintaksnya :
 ```
  echo view('header', $data);
        echo view('content/halaman', $data);
        echo view('footer');
 ```
