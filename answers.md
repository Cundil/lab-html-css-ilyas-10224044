# Jawaban Praktikum: Ilyas Rahman Hakim (10224044)

## Bagian 1: Pemanasan

1. Pada aturan `nav a.active:hover { color: red; }`:
   - **Selector**: `nav a.active:hover`
   - **Deklarasi**: `{ color: red; }`
   - **Property**: `color`
   - **Value**: `red`
   - **Pseudo-class**: `:hover` (dan `.active` adalah class selector, `:hover` adalah pseudo-class).

2. Sifat default display element:
   - **Block**: `<p>`, `<li>`, `<h2>`
   - **Inline**: `<span>`, `<a>`, `<strong>`

3. Paragraf yang menjadi hijau: **A dan B**.
   - Penjelasan: `.box p` menargetkan semua elemen `<p>` yang berada di dalam elemen ber-class `box` (berlaku descendant selector, baik child langsung maupun nested child).

4. Warnanya adalah **Merah (red)**.
   - Penjelasan: ID selector (`#title`) memiliki nilai specificity yang paling tinggi `(1,0,0)` dibandingkan Class selector (`.heading` = `0,1,0`) dan Type selector (`h1` = `0,0,1`).

5. Kesalahan HTML: Tag tidak ditutup secara berurutan (_improper nesting_). Tag `<strong>` dibuka di dalam `<p>`, sehingga `</strong>` harus ditutup sebelum `</p>`.
   - Perbaikan: `<p>Hello <strong>world</strong></p>`

---

## Bagian 3: Prediksi Selector Golf

P1. Prediksi awal:
(a) "Weekly hack nights." -> **green** (karena `section p` lebih spesifik dibanding `p`)
(b) "Bring your own laptop." -> **orange** (karena class `.note` spesifik)
(c) "© 2026 Student Affairs" -> **blue** (hanya cocok dengan selector `p`)

P2. Urutan Specificity dari TERTINGGI ke TERENDAH:

1.  `#tech p` (Specificity: 1, 0, 1)
2.  `.club p` (Specificity: 0, 1, 1)
3.  `main section p` (Specificity: 0, 0, 3)
4.  `p` (Specificity: 0, 0, 1)

Setelah diuji (hasil sebenarnya):

- P1: (a) hijau (green), (b) oranye (orange), (c) biru (blue). Prediksi 100% akurat.
- P2: `#tech p` > `.club p` > `main section p` > `p`. Prediksi 100% akurat.

---

## Bagian 4: Box model

Q1 (content-box):

- Lebar Tampak (border-to-border) = width + padding-left + padding-right + border-left + border-right
- Perhitungan: 300px + 16px + 16px + 1px + 1px = **334px**.

Q2 (border-box):

- Elemen tetap memiliki lebar total border-to-border sebesar **300px**.
- Lebar area konten (_content width_) otomatis menyusut menjadi: 300px - (16px _ 2) - (1px _ 2) = **266px**.

Pengecekan DevTools:

- Content: 926px x 180px (tergantung viewport)
- Padding: 16px (top, right, bottom, left)
- Border: 1px (top, right, bottom, left)
- Margin: 0px top/bottom, 0px left/right (atau 24px bottom)

---

## Bagian 5: Tabel debug

| #   | Baris | Bug                                                                 | Perbaikan                                  | Cara menemukannya                 |
| --- | ----- | ------------------------------------------------------------------- | ------------------------------------------ | --------------------------------- |
| 1   | 8     | Property CSS salah eja `colour: #333;`                              | `color: #333;`                             | DevTools (Invalid property name)  |
| 2   | 11    | Kurang titik koma `;` setelah `#dbe7f3`                             | `background: #dbe7f3;`                     | DevTools / Membaca kode           |
| 3   | 14    | Nama class di CSS `.Card` kapital, sedangkan di HTML `class="card"` | `.card`                                    | Membaca kode & pencocokan class   |
| 4   | 19    | Ada spasi pada nilai unit `18 px`                                   | `18px`                                     | DevTools (Invalid property value) |
| 5   | 22    | Property CSS salah eja `centre`                                     | `center`                                   | DevTools (Invalid property value) |
| 6   | 27    | Tag penutup `<h1>` tidak cocok (`</h2>`)                            | `<h1>Campus News</h1>`                     | W3C Validator                     |
| 7   | 30    | Atribut `href` kurang tanda petik penutup `href="about.html>`       | `href="about.html">`                       | Membaca kode / Syntax Highlighter |
| 8   | 35    | Elemen `<img>` tidak memiliki atribut `alt`                         | `<img src="..." alt="Campus News Banner">` | W3C Validator                     |
| 9   | 36    | ID di HTML `newsList` beda dengan di CSS `#news-list`               | `id="news-list"`                           | Membaca kode / DevTools           |

---

## Bagian 6: Tabel Code Review

| #   | Baris | Masalah                                                                                                | Mengapa penting                                                               | Perbaikan saya                                                       |
| --- | ----- | ------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| 1   | 1     | Menggunakan `<html>` tanpa `<!DOCTYPE html>` dan atribut `lang="id"`                                   | Memicu quirks mode pada browser dan buruk untuk SEO/Aksesibilitas             | Tambahkan `<!DOCTYPE html>` dan `<html lang="id">`                   |
| 2   | 4     | Fixed width pada layout (`width: 1200px;`)                                                             | Merusak tampilan di layar mobile (tidak responsif)                            | Gunakan `max-width: 100%` atau container responsive                  |
| 3   | 5     | Menggunakan `!important` pada CSS selector                                                             | Merusak spesifisitas CSS dan menyulitkan maintenance                          | Hapus `!important` dan perbaiki selector                             |
| 4   | 10-28 | Tidak ada tag semantik (`<header>`, `<main>`, `<nav>`, `<article>`, `<footer>`), semua memakai `<div>` | Buruk untuk screen reader, SEO, dan struktur dokumen                          | Ganti `<div>` dengan tag HTML5 semantik                              |
| 5   | 11    | Judul utama memakai `<div><b>STT Cipasung</b></div>` bukan `<h1>`                                      | Mengabaikan hirarki heading dan merusak struktur dokumen                      | Ganti dengan `<h1>STT Cipasung</h1>`                                 |
| 6   | 17,23 | Inline style (`style="font-size: 24px;..."`) & tag `<br>` berulang                                     | Menyulitkan perbaikan style dan merusak layout responsive                     | Pindahkan style ke CSS eksternal/internal dan gunakan spacing margin |
| 7   | 20    | Tag `<img>` tanpa atribut `alt`                                                                        | Mengurangi aksesibilitas bagi pengguna penyandang disabilitas (screen reader) | Tambahkan atribut `alt="Gedung Kampus STT Cipasung"`                 |
| 8   | 24,25 | Input form tanpa elemen `<label>`                                                                      | Pengguna screen reader tidak tahu fungsi input tersebut                       | Bungkus/hubungkan dengan `<label for="...">`                         |
| 9   | 26    | Inline event handler JS (`onclick="alert('Sent!')"`)                                                   | Melanggar prinsip Separation of Concerns                                      | Pindahkan JavaScript ke file terpisah / hapus inline handler         |

Refleksi:

1. Masalah yang paling sulit disadari hanya dari browser adalah penggunaan `<div>` non-semantik dan hilangnya `<label>`/`alt` pada form & image, karena tampilan visualnya terlihat sama persis walau kode HTML-nya buruk.
2. Meskipun "berfungsi" secara visual, kode tersebut tidak aksesibel untuk pengguna penyandang disabilitas (screen reader), sangat buruk untuk SEO search engine, dan sulit diperbaiki/dikembangkan di masa depan (unmaintainable).
3. Kebiasaan yang akan saya lakukan adalah selalu memvalidasi HTML menggunakan W3C Validator dan melakukan tes navigasi keyboard/DevTools sebelum melakukan pengumpulan kode.

---

## Bagian 7: Exit ticket

1. Anatomi aturan CSS terdiri dari **Selector** (menentukan elemen mana yang ditargetkan), dibuka dengan kurung kurawal `{}` yang berisi satu atau lebih **Deklarasi**. Setiap deklarasi memiliki pasangan **Property** (sifat yang ingin diubah) dan **Value** (nilai perubahan) yang dipisahkan titik dua `:` serta diakhiri titik koma `;`.
2. Konsep yang perlu pendalaman lebih lanjut adalah perhitungan spesifisitas (_specificity calculator_) pada selector bertumpuk yang sangat kompleks.
3. Mengatur layout horizontal menggunakan CSS Flexbox (`display: flex; gap: 1rem; align-items: center;`) tanpa harus melihat dokumentasi lagi.
