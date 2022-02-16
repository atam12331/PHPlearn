# Data Base
### ketika ingin membuat database utamakan code construct dan connect terlebih dahulu dengan format seperti berikut :
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

Ketika ingin memanggil model pada controller diwajibkan untuk menambah syntaks jembatan kepada letak file tersebut. contohnya :
```
use CodeIgniter\Model;
use App\Model\ModelKustom; //harus dipanggil dulu supaya bisa diakses
```
