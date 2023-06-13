# Pemrograman Web 02 - Labweb11

## note :
mohon maaf file **ci4** tidak dapat di upload ke git hub

## Profil
| #               | Biodata           |
| --------------- | ----------------- |
| **Nama**        | Muhammad Farhan   |
| **NIM**         | 312110128         |
| **Kelas**       | TI.21.A.1         |
| **Mata Kuliah** | Pemrograman Web 2 |

## Upload File Gambar

### Langkah-langkah Praktikum

#### Upload Gambar pada Artikel
Menambahkan fungsi unggah gambar pada tambah artikel.
Buka kembali Controller Artikel pada project sebelumnya, sesuaikan kode pada method
add seperti berikut:

```php
public function add()
{
// validasi data.
$validation = \Config\Services::validation();
$validation->setRules(['judul' => 'required']);
$isDataValid = $validation->withRequest($this->request)->run();
if ($isDataValid)
{
$file = $this->request->getFile('gambar');
$file->move(ROOTPATH . 'public/gambar');
$artikel = new ArtikelModel();
$artikel->insert([
'judul' => $this->request->getPost('judul'),
'isi' => $this->request->getPost('isi'),
'slug' => url_title($this->request->getPost('judul')),
'gambar' => $file->getName(),
]);
return redirect('admin/artikel');
}
$title = "Tambah Artikel";
return view('artikel/form_add', compact('title'));
}
```

Kemudian pada file views/artikel/form_add.php tambahkan field input file seperti
berikut.

```html
<p>
<input type="file" name="gambar">
</p>
```

Dan sesuaikan tag form dengan menambahkan ecrypt type seperti berikut.

```html
<form action="" method="post" enctype="multipart/form-data">
```

Ujicoba file upload dengan mengakses menu tambah artikel.

![Screenshot (219)](https://github.com/farhanz17/labwebs11/assets/92637117/e336da95-3086-44db-9454-11a1438dd45f)

## Pertanyaan dan Tugas

Selesaikan programnya sesuai Langkah-langkah yang ada. Anda boleh melakukan
improvisasi.

## Laporan Praktikum

1. Melanjutkan praktikum sebelumnya pada repository dengan nama Lab11Web.
2. Kerjakan semua latihan yang diberikan sesuai urutannya.
3. Screenshot setiap perubahannya.
4. Update file README.md dan tuliskan penjelasan dari setiap langkah praktikum
beserta screenshotnya.
5. Commit hasilnya pada repository masing-masing.
6. Kirim URL repository pada e-learning ecampus

# Terima kasih..



