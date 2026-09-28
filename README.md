# DOM-Javascript

# Belajar Dasar DOM JavaScript

Proyek latihan sederhana untuk memahami manipulasi **DOM (Document Object Model)** menggunakan JavaScript murni.

---

## 1. `querySelector` & `querySelectorAll`

- **`querySelector`**: Mengambil **1 elemen pertama** yang cocok dengan CSS selector.
- **`querySelectorAll`**: Mengambil **semua elemen** yang cocok dalam bentuk daftar (`NodeList`).
- **Contoh**: Mengambil elemen judul (`#main-title`) dan daftar item (`.list-item`).

---

## 2. `innerHTML`, `textContent`, & `innerText`

- **`innerHTML`**: Mengubah isi elemen **beserta tag HTML** di dalamnya.
- **`textContent`**: Mengambil atau mengubah **semua teks** (termasuk teks tersembunyi).
- **`innerText`**: Mengambil atau mengubah teks yang **tampak di layar** saja.
- **Contoh**: `innerHTML` untuk menyisipkan elemen baru, `textContent` untuk mengganti teks biasa.

---

## 3. Manipulasi Atribut & Style

- **Atribut**: Mengubah atau menambah atribut HTML seperti `disabled`, `id`, atau `class` pakai `setAttribute()`.
- **Style**: Mengubah tampilan CSS secara langsung lewat JavaScript via `element.style`.
- **Contoh**: Mengubah warna latar belakang kotak atau membuat tombol menjadi non-aktif (`disabled`).
