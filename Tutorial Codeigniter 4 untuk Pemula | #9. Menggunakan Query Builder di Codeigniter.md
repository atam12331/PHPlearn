# Data Base

### Code Construct (pembangun utama)
ketika ingin membuat database utamakan code construct dan connect terlebih dahulu dengan format seperti berikut :
```
<?php 
namespace App\Models;
use CodeIgniter\Database\ConnectionInterface;
class ModelKustom
{
    public function __construct(){
        $this->db = \Config\Database::connect();

    }

   <codedatabselainnya>

}


?>
```

---

### Pemanggilan melalui controller
Ketika ingin memanggil model pada controller diwajibkan untuk menambah syntaks jembatan kepada letak file tersebut. contohnya :
```
use CodeIgniter\Model;
use App\Model\ModelKustom; //harus dipanggil dulu supaya bisa diakses
```

kemudian tambahkan ke bagian bawah nya di file ModelKustom dengan kode sebagai berikut :
```
public function halaman_cek()
    {
        $halamanKustom = new ModelKustom();
        $data = $halamanKustom->getData();
        print_r($data);
    }
```
---

### Database Generate Web
Dengan belajar di channel ini saya mendapatkan kesempatan untuk belajar dummy database dengan ontohnya. bisa kunjungi websitue
http://filldb.info/
kemudian klik generate. bisa diubah tablenya. ada udah perbedaan besar yang sudah saya pahami, antara author dan post. kalo author uini merujuk kepada data-data subjek atau orang sedangkan  post merujuk kepada post itu sendiri (objek)

---

### Show SQL
Ketika ingin menambahkan data, tetapikita ingin melihat sintaksnya bukan datanya didalam browser, maka jalankanlah code berikut :
```
 $sql = $builder->getCompiledSelect(); //menjalankan query apa yang akan ditampilkan
        return $sql;
```

---

### Query : Limit
Limit menggunakan query builder, ini sangat berguna ketika kita ingin membatasi data yang ingin ditampilkan didalam browser. codenya sebagai berikut 
```
public function getData()
    {
        $builder = $this->db->table("authors");
        $data = $builder->get(10, 0)->getResult(); //10 itu jumlah, 0 itu awalan data yang ditampilkan
        // select * from autho limit 0,1
        $sql = $builder->getCompiledSelect(); //menjalankan query apa yang akan ditampilkan
        return $data;
    }
```

---

### Query : Select
Select beberapa tabel pada database sql tapi disini kita menggunakan query builder yang langsung disediakan oleh CI4. kodenya sebagai berikut :
```
public function getData()
    {
        $builder = $this->db->table("authors");
        $builder->select("id,first_name,last_name,email");
        $data = $builder->get(10, 0)->getResult(); //10 itu jumlah, 0 itu awalan data yang ditampilkan
        // select * from autho limit 0,1
        $sql = $builder->getCompiledSelect(); //menjalankan query apa yang akan ditampilkan
        return $data;
    }
```

---

### Query : Where
Menggunakan query builder untuk kondisi, dalam kodingan dibawah kondisinya berupa menampilkan data pada urutan kedua, maka kodenya sebagai berikut :
```
  public function getData()
    {
        $builder = $this->db->table("authors");
        $builder->select("id,first_name,last_name,email");
        $data = $builder->getWhere(['id' => 2])->getResult(); //10 itu jumlah, 0 itu awalan data yang ditampilkan
        // select * from autho limit 0,1
        $sql = $builder->getCompiledSelect(); //menjalankan query apa yang akan ditampilkan
        return $data;
    }
```
---

### Query : Max
dalam kasus selanjutnya kita akan diarahkan untuk mencoba mencari tanggal maksimal dari datan tabel posts. pada bagian tanggal derngan code sebagai berikut :
```
public function getData()
    {
        $builder = $this->db->table("posts");
        $builder->selectMax("date");
        $data = $builder->get()->getResult(); //10 itu jumlah, 0 itu awalan data yang ditampilkan
        // select * from autho limit 0,1
        return $data;
    }
```
---

### Query : Name Modifier
Kemudian, ada juga query builder untuk merubah nama pada tabel aslinya menjadi berbeda pada yang kan kita tampilkan pada browser. contoh disini date akan diubah menjadi tanggal sehingga codenya menjadi sebafai berikut :
```
public function getData()
    {
        $builder = $this->db->table("posts");
        $builder->selectMax("date", "tanggal");
        $data = $builder->get()->getResult(); //10 itu jumlah, 0 itu awalan data yang ditampilkan
        // select * from autho limit 0,1
        return $data;
    }
```

---
### Query : Join Table
Pada kasus selanjutnya kita ankan mencoba men joinkan atribut antar authors_id di post dan id di author. sehingga code yang dibuat sebagai berikut :
```
public function getData()
    {
        $builder = $this->db->table("posts");
        $builder->select("*");
        $builder->join("authors", "authors.id = posts.author_id");
        $data = $builder->get()->getResult(); //10 itu jumlah, 0 itu awalan data yang ditampilkan
        // select * from autho limit 0,1
        return $data;
    }
```

---

### Query : Where Nesterd
Where bertingkat, dalam kasus ini kita akan memberi data posts dengan dua kondisi, yaitu kondisi yang pertama id = 1 dan author_id = 1 juga sehingga datanya kodenya sebagai berikut :
```
 public function getData()
    {
        $builder = $this->db->table("posts");
        $builder->select("*");
        $builder->where("id", "1");
        $builder->where("author_id", "1");
        //opsi lainnya adalah : $builder->where("id = '1' and author_id = '1' ");
       
        //opsi lain ketika menggunakan or
        
        //$builder->where("id", 1);
        //$builder->orwhere("id", 2);

        $data = $builder->get()->getResult(); 
        return $data;
    }
```
### Query Builder : Where In
kode diatas bisa kombinasikan dengan and or untuk menadpatkan data yang diinginkan

---

where In adalah kondisi untuk menampilakn kondisi yang memenuhi pada variable sebelumnya yang diberikan, sehingga kodenya menjadi seperti ini :
```
public function getData()
    {
        $builder = $this->db->table("posts");
        $builder->select("*");
        $idPilihan = ['1', '2', '3', '4'];
        $builder->whereIn('id',$idPilihan);
        $data = $builder->get()->getResult(); //10 itu jumlah, 0 itu awalan data yang ditampilkan
        // select * from autho limit 0,1
        $sql = $builder->getCompiledSelect(); //menjalankan query apa yang akan ditampilkan
        return $data;
    }
```    

---

### Query : Like
Kasus selanjutnya adalah menggunakan fungsi like yang dimanafungsi ibi bekeerja ketika ingin mencari suatu kata, contohnya disini saya membuat kasus, like yaitu mencari kata aut disemua atribut title
```
public function getData()
    {
        $builder = $this->db->table("posts");
        $builder->select("*");
        $builder->like("title", "aut");
        $data = $builder->get()->getResult(); //10 itu jumlah, 0 itu awalan data yang ditampilkan
        // select * from autho limit 0,1
        $sql = $builder->getCompiledSelect(); //menjalankan query apa yang akan ditampilkan
        return $data;
    }
```
