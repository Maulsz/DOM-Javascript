# Belajar Dasar DOM JavaScript

Repository ini berisi catatan pembelajaran dasar **DOM (Document Object Model)** pada JavaScript, khususnya tentang pemilihan elemen, perubahan konten, serta manipulasi atribut dan style.

## Pengertian DOM

DOM atau **Document Object Model** adalah representasi dokumen HTML dalam bentuk objek yang dapat diakses oleh JavaScript.

Saat browser membaca halaman HTML, setiap elemen seperti `<h1>`, `<p>`, `<button>`, `<div>`, dan `<img>` direpresentasikan sebagai objek di dalam DOM. JavaScript dapat menggunakan objek tersebut untuk membaca, menambah, mengubah, atau menghapus bagian halaman secara dinamis.

Dengan DOM, JavaScript dapat melakukan hal-hal seperti:

- Mengambil elemen HTML berdasarkan `id`, `class`, nama tag, atau selector CSS lainnya.
- Mengubah teks pada halaman.
- Menambahkan elemen HTML baru.
- Mengubah atribut HTML.
- Mengubah tampilan CSS.
- Merespons interaksi pengguna, seperti klik tombol atau input pada form.

## 1. querySelector dan querySelectorAll

### `querySelector()`

`querySelector()` adalah method untuk memilih **satu elemen pertama** yang sesuai dengan selector CSS.

Sintaks:

```javascript
document.querySelector("selector");
```

Contoh:

```javascript
const judul = document.querySelector("#judul");
```

Kode tersebut mencari elemen pertama yang memiliki `id="judul"`.

Contoh selector yang dapat digunakan:

```javascript
document.querySelector("#id-elemen");
document.querySelector(".nama-class");
document.querySelector("p");
document.querySelector("button");
document.querySelector("input[type='text']");
```

Jika elemen ditemukan, hasilnya berupa objek elemen HTML. Jika tidak ditemukan, hasilnya adalah `null`.

Contoh pengecekan:

```javascript
const tombol = document.querySelector("#tombol-simpan");

if (tombol) {
  console.log("Tombol ditemukan");
}
```

`querySelector()` digunakan ketika hanya membutuhkan satu elemen tertentu, misalnya:

- Satu judul halaman.
- Satu tombol simpan.
- Satu input pencarian.
- Satu area notifikasi.
- Satu elemen menu.

`querySelector()` mengembalikan elemen pertama yang cocok dengan selector yang diberikan. [2]

### `querySelectorAll()`

`querySelectorAll()` adalah method untuk memilih **semua elemen** yang sesuai dengan selector CSS.

Sintaks:

```javascript
document.querySelectorAll("selector");
```

Contoh:

```javascript
const semuaParagraf = document.querySelectorAll("p");
```

Kode tersebut mengambil semua elemen `<p>` yang terdapat pada halaman.

Contoh lain:

```javascript
const semuaTombol = document.querySelectorAll(".btn");
```

Kode tersebut mengambil semua elemen yang memiliki class `btn`.

Hasil dari `querySelectorAll()` berupa `NodeList`, yaitu kumpulan elemen yang dapat diakses menggunakan perulangan seperti `forEach()`.

```javascript
const semuaTombol = document.querySelectorAll(".btn");

semuaTombol.forEach((tombol) => {
  console.log(tombol);
});
```

Contoh mengubah teks semua elemen:

```javascript
const semuaItem = document.querySelectorAll(".item");

semuaItem.forEach((item) => {
  item.textContent = "Data telah diperbarui";
});
```

`querySelectorAll()` cocok digunakan ketika ingin memanipulasi banyak elemen, misalnya:

- Semua card produk.
- Semua tombol.
- Semua item daftar.
- Semua gambar.
- Semua elemen dengan class yang sama.

`querySelectorAll()` menghasilkan `NodeList` statis, sehingga daftar hasil yang sudah diambil tidak otomatis berubah ketika elemen baru ditambahkan setelah method dipanggil. [1][3]

### Perbedaan `querySelector()` dan `querySelectorAll()`

| Aspek | `querySelector()` | `querySelectorAll()` |
|---|---|---|
| Jumlah elemen yang diambil | Satu elemen pertama | Semua elemen yang cocok |
| Hasil | `Element` atau `null` | `NodeList` |
| Cocok untuk | Satu tombol, satu judul, satu input | Banyak item, banyak tombol, banyak card |
| Contoh | `document.querySelector("#judul")` | `document.querySelectorAll(".item")` |

## 2. innerHTML, textContent, dan innerText

`innerHTML`, `textContent`, dan `innerText` adalah properti yang digunakan untuk mengambil atau mengubah isi sebuah elemen HTML.

Walaupun terlihat mirip, ketiganya memiliki fungsi yang berbeda.

### `innerHTML`

`innerHTML` digunakan untuk membaca atau mengubah isi elemen dalam bentuk **HTML**.

Contoh:

```javascript
const container = document.querySelector("#container");

container.innerHTML = "<h2>Judul Baru</h2><p>Ini adalah paragraf baru.</p>";
```

Pada contoh tersebut, string HTML akan diproses oleh browser dan ditampilkan sebagai elemen `<h2>` serta `<p>`.

Contoh hasil:

```html
<div id="container">
  <h2>Judul Baru</h2>
  <p>Ini adalah paragraf baru.</p>
</div>
```

`innerHTML` dapat digunakan ketika ingin:

- Menambahkan struktur HTML baru.
- Menampilkan card atau daftar item.
- Membuat tombol atau elemen secara dinamis.
- Mengganti seluruh isi suatu container.

Contoh:

```javascript
const daftar = document.querySelector("#daftar");

daftar.innerHTML = `
  <li>Item pertama</li>
  <li>Item kedua</li>
  <li>Item ketiga</li>
`;
```

Perlu berhati-hati ketika menggunakan `innerHTML` dengan input dari pengguna. Data yang tidak divalidasi dapat memasukkan kode HTML yang tidak diinginkan. Untuk menampilkan teks biasa dari pengguna, gunakan `textContent`.

### `textContent`

`textContent` digunakan untuk membaca atau mengubah isi elemen sebagai **teks biasa**.

Contoh:

```javascript
const pesan = document.querySelector("#pesan");

pesan.textContent = "Data berhasil disimpan.";
```

Jika nilai yang dimasukkan berisi tag HTML, tag tersebut tidak akan dijalankan sebagai HTML.

```javascript
pesan.textContent = "<strong>Data berhasil disimpan.</strong>";
```

Hasil yang tampil pada halaman:

```text
<strong>Data berhasil disimpan.</strong>
```

`textContent` cocok digunakan untuk:

- Menampilkan notifikasi.
- Menampilkan status.
- Mengubah judul.
- Menampilkan jumlah data.
- Menampilkan teks dari input pengguna.
- Mengubah isi tombol.

Contoh:

```javascript
const jumlahData = document.querySelector("#jumlah-data");

jumlahData.textContent = "Jumlah data: 10";
```

### `innerText`

`innerText` juga digunakan untuk mengambil atau mengubah teks dari sebuah elemen.

Contoh:

```javascript
const judul = document.querySelector("h1");

console.log(judul.innerText);
```

Perbedaan utama `innerText` dan `textContent` adalah bahwa `innerText` berfokus pada teks yang benar-benar terlihat pada halaman.

Jika suatu elemen disembunyikan menggunakan CSS, misalnya:

```css
display: none;
```

teks di dalam elemen tersebut biasanya tidak akan ikut terbaca oleh `innerText`. Sebaliknya, `textContent` tetap dapat membaca teks tersebut.

### Perbedaan `innerHTML`, `textContent`, dan `innerText`

| Properti | Fungsi | HTML diproses | Memperhatikan elemen tersembunyi |
|---|---|---:|---:|
| `innerHTML` | Membaca atau mengubah isi dalam bentuk HTML | Ya | Tidak menjadi fokus |
| `textContent` | Membaca atau mengubah teks biasa | Tidak | Ya, teks tetap terbaca |
| `innerText` | Membaca atau mengubah teks yang terlihat | Tidak | Tidak, hanya teks yang terlihat |

Contoh sederhana:

```html
<p id="contoh">
  Teks terlihat
  <span style="display: none;">Teks tersembunyi</span>
</p>
```

```javascript
const contoh = document.querySelector("#contoh");

console.log(contoh.innerHTML);
console.log(contoh.textContent);
console.log(contoh.innerText);
```

Secara konsep:

```text
innerHTML    : Teks terlihat <span style="display: none;">Teks tersembunyi</span>
textContent  : Teks terlihat Teks tersembunyi
innerText    : Teks terlihat
```

`textContent` merepresentasikan isi teks sebuah node dan turunannya, sedangkan `innerText` merepresentasikan teks yang dirender atau terlihat pada halaman. [6][7]

## 3. Manipulasi Atribut dan Style

### Pengertian atribut

Atribut adalah informasi tambahan yang terdapat pada elemen HTML.

Contoh:

```html
<img src="gambar.jpg" alt="Contoh gambar" />
<a href="[https://example.com](https://example.com)">Kunjungi Website</a>
<input type="text" placeholder="Masukkan nama" />
<button disabled>Kirim</button>
```

Beberapa contoh atribut HTML:

| Atribut | Fungsi |
|---|---|
| `id` | Memberikan identitas unik pada elemen |
| `class` | Memberikan nama class CSS pada elemen |
| `src` | Menentukan sumber file, biasanya pada gambar atau video |
| `href` | Menentukan tujuan link |
| `alt` | Menentukan teks alternatif untuk gambar |
| `disabled` | Menonaktifkan input atau tombol |
| `placeholder` | Menampilkan petunjuk pada input |
| `title` | Menampilkan informasi tambahan saat elemen diarahkan cursor |

### `getAttribute()`

`getAttribute()` digunakan untuk mengambil nilai dari suatu atribut.

Sintaks:

```javascript
element.getAttribute("nama-atribut");
```

Contoh:

```javascript
const gambar = document.querySelector("img");

const sumberGambar = gambar.getAttribute("src");

console.log(sumberGambar);
```

Kode tersebut mengambil nilai atribut `src` dari elemen gambar.

### `setAttribute()`

`setAttribute()` digunakan untuk menambahkan atribut baru atau mengubah nilai atribut yang sudah ada.

Sintaks:

```javascript
element.setAttribute("nama-atribut", "nilai-atribut");
```

Contoh:

```javascript
const tombol = document.querySelector("button");

tombol.setAttribute("disabled", "true");
```

Kode tersebut menambahkan atribut `disabled` pada tombol, sehingga tombol tidak dapat diklik.

Contoh mengubah atribut gambar:

```javascript
const gambar = document.querySelector("img");

gambar.setAttribute("src", "gambar-baru.jpg");
gambar.setAttribute("alt", "Gambar baru");
```

Contoh mengubah placeholder input:

```javascript
const input = document.querySelector("input");

input.setAttribute("placeholder", "Masukkan email");
```

### `removeAttribute()`

`removeAttribute()` digunakan untuk menghapus atribut dari sebuah elemen.

Sintaks:

```javascript
element.removeAttribute("nama-atribut");
```

Contoh:

```javascript
const tombol = document.querySelector("button");

tombol.removeAttribute("disabled");
```

Kode tersebut menghapus atribut `disabled`, sehingga tombol dapat diklik kembali.

### Manipulasi style langsung

JavaScript dapat mengubah tampilan CSS elemen menggunakan properti `style`.

Contoh:

```javascript
const kotak = document.querySelector(".box");

kotak.style.backgroundColor = "blue";
kotak.style.color = "white";
kotak.style.padding = "15px";
kotak.style.borderRadius = "8px";
```

Perubahan tersebut setara dengan CSS berikut:

```css
.box {
  background-color: blue;
  color: white;
  padding: 15px;
  border-radius: 8px;
}
```

Namun, ketika menulis CSS melalui JavaScript, nama properti menggunakan format `camelCase`.

| CSS | JavaScript |
|---|---|
| `background-color` | `backgroundColor` |
| `font-size` | `fontSize` |
| `text-align` | `textAlign` |
| `border-radius` | `borderRadius` |
| `margin-top` | `marginTop` |

Contoh lain:

```javascript
const judul = document.querySelector("h1");

judul.style.color = "darkblue";
judul.style.fontSize = "32px";
judul.style.textAlign = "center";
```

### Manipulasi class dengan `classList`

Selain menggunakan `style` secara langsung, cara yang lebih rapi untuk mengubah tampilan adalah menggunakan `classList`.

Method yang sering digunakan:

| Method | Fungsi |
|---|---|
| `classList.add()` | Menambahkan class |
| `classList.remove()` | Menghapus class |
| `classList.toggle()` | Menambah atau menghapus class secara bergantian |
| `classList.contains()` | Memeriksa apakah elemen memiliki class tertentu |

Contoh:

```javascript
const kotak = document.querySelector(".box");

kotak.classList.add("aktif");
```

Jika terdapat CSS berikut:

```css
.aktif {
  background-color: green;
  color: white;
}
```

Maka elemen `kotak` akan memiliki tampilan sesuai class `aktif`.

Contoh menghapus class:

```javascript
kotak.classList.remove("aktif");
```

Contoh toggle class:

```javascript
kotak.classList.toggle("aktif");
```

`toggle()` berguna untuk fitur seperti:

- Mode gelap dan mode terang.
- Menampilkan atau menyembunyikan menu.
- Memberi tanda elemen yang aktif.
- Mengubah status tombol.
- Membuka dan menutup modal.

## Kesimpulan

DOM memungkinkan JavaScript berinteraksi dengan elemen HTML secara dinamis.

Materi penting yang dipelajari adalah:

- `querySelector()` digunakan untuk memilih satu elemen pertama yang sesuai dengan selector.
- `querySelectorAll()` digunakan untuk memilih seluruh elemen yang sesuai dengan selector.
- `innerHTML` digunakan untuk memasukkan atau mengambil isi dalam bentuk HTML.
- `textContent` digunakan untuk memasukkan atau mengambil teks biasa.
- `innerText` digunakan untuk mengambil teks yang terlihat pada halaman.
- `getAttribute()` digunakan untuk mengambil nilai atribut.
- `setAttribute()` digunakan untuk menambah atau mengubah atribut.
- `removeAttribute()` digunakan untuk menghapus atribut.
- `style` digunakan untuk mengubah CSS secara langsung melalui JavaScript.
- `classList` digunakan untuk menambah, menghapus, atau mengatur class CSS elemen.