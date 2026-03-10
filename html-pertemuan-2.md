# HTML - Pertemuan 2: Media, Form Lanjutan, dan Best Practices

## Daftar Isi
1. [Review Pertemuan 1](#review-pertemuan-1)
2. [Inline vs Block Element](#inline-vs-block-element)
3. [Elemen Media](#elemen-media)
4. [Form Lanjutan](#form-lanjutan)
5. [Meta Tags & SEO Dasar](#meta-tags--seo-dasar)
6. [HTML Entities](#html-entities)
7. [Atribut Global](#atribut-global)
8. [Aksesibilitas HTML (A11y)](#aksesibilitas-html-a11y)
9. [Latihan](#latihan)
10. [Tugas Mandiri](#tugas-mandiri)

---

## Review Pertemuan 1

Pada pertemuan sebelumnya kita sudah belajar:
- ✅ Struktur dasar dokumen HTML
- ✅ Heading, paragraf, dan text formatting
- ✅ Link dan gambar
- ✅ List (ul, ol, dl)
- ✅ Tabel (table, thead, tbody, colspan, rowspan)
- ✅ Form dasar (input, textarea, select, button)
- ✅ Semantic HTML (header, nav, main, article, section, aside, footer)

Pada pertemuan ini kita akan **memperdalam** HTML dengan topik yang lebih lanjut untuk membuat halaman web yang lebih lengkap, terstruktur, dan profesional.

---

## Inline vs Block Element

Sebelum melangkah lebih jauh, penting untuk memahami perbedaan dasar antara dua jenis elemen HTML.

### Block Element

Block element selalu **dimulai dari baris baru** dan mengambil **lebar penuh** yang tersedia.

```html
<div>Ini adalah div (block)</div>
<p>Ini adalah paragraf (block)</p>
<h1>Ini adalah heading (block)</h1>
<ul>
    <li>List item (block)</li>
</ul>
```

**Tag block yang umum:**
`<div>`, `<p>`, `<h1>`–`<h6>`, `<ul>`, `<ol>`, `<li>`, `<table>`, `<form>`, `<header>`, `<section>`, `<article>`, `<footer>`, `<blockquote>`

### Inline Element

Inline element **tidak memulai baris baru** dan hanya mengambil **lebar sebesar kontennya**.

```html
<p>
    Ini teks biasa, lalu ada <strong>teks tebal</strong>, lalu ada
    <a href="#">link</a>, dan <span>span</span> — semuanya dalam satu baris.
</p>
```

**Tag inline yang umum:**
`<span>`, `<a>`, `<strong>`, `<em>`, `<img>`, `<input>`, `<label>`, `<button>`, `<mark>`, `<small>`, `<sub>`, `<sup>`

### `<div>` vs `<span>`

| Tag | Tipe | Kegunaan |
|-----|------|----------|
| `<div>` | Block | Wadah/container untuk mengelompokkan elemen block |
| `<span>` | Inline | Wadah untuk mengelompokkan elemen inline dalam teks |

```html
<!-- div: mengelompokkan bagian halaman -->
<div class="kartu">
    <h2>Judul Kartu</h2>
    <p>Deskripsi kartu ini.</p>
</div>

<!-- span: menandai bagian tertentu dalam teks -->
<p>
    Harga produk ini adalah
    <span style="color: red; font-weight: bold;">Rp 150.000</span>
    dan stok masih tersedia.
</p>
```

### `<blockquote>` vs `<q>`

```html
<!-- blockquote: kutipan panjang (block) -->
<blockquote cite="https://react.dev">
    <p>React is the library for web and native user interfaces.</p>
    <footer>— React Documentation</footer>
</blockquote>

<!-- q: kutipan pendek (inline) -->
<p>Steve Jobs pernah berkata, <q>Stay hungry, stay foolish.</q></p>
```

---

## Elemen Media

### Video

Tag `<video>` digunakan untuk menyematkan video langsung di halaman HTML.

```html
<!-- Video dasar -->
<video src="video.mp4" controls></video>

<!-- Video dengan pengaturan lengkap -->
<video
    width="640"
    height="360"
    controls
    autoplay
    muted
    loop
    poster="thumbnail.jpg"
>
    <!-- Sumber alternatif untuk kompatibilitas browser -->
    <source src="video.mp4" type="video/mp4" />
    <source src="video.webm" type="video/webm" />
    <!-- Teks fallback jika browser tidak mendukung -->
    <p>Browser kamu tidak mendukung video HTML5.
        <a href="video.mp4">Download video di sini</a>.
    </p>
</video>
```

**Atribut `<video>`:**

| Atribut | Fungsi |
|---------|--------|
| `controls` | Menampilkan kontrol putar (play, pause, volume) |
| `autoplay` | Video otomatis diputar (butuh `muted` di Chrome) |
| `muted` | Menonaktifkan suara |
| `loop` | Video diulang terus |
| `poster` | Gambar thumbnail sebelum video diputar |
| `width` / `height` | Ukuran video |
| `preload` | Cara memuat video (`auto`, `metadata`, `none`) |

### Audio

Tag `<audio>` digunakan untuk menyematkan file audio.

```html
<!-- Audio dasar -->
<audio src="musik.mp3" controls></audio>

<!-- Audio dengan multiple source -->
<audio controls>
    <source src="musik.mp3" type="audio/mpeg" />
    <source src="musik.ogg" type="audio/ogg" />
    <p>Browser kamu tidak mendukung audio HTML5.</p>
</audio>
```

**Atribut `<audio>`:**

| Atribut | Fungsi |
|---------|--------|
| `controls` | Menampilkan kontrol audio |
| `autoplay` | Audio otomatis diputar |
| `muted` | Menonaktifkan suara |
| `loop` | Audio diulang terus |
| `preload` | Cara memuat audio |

### Figure & Figcaption

`<figure>` digunakan untuk membungkus media (gambar, video, kode) beserta keterangannya. `<figcaption>` adalah keterangan/caption-nya.

```html
<!-- Gambar dengan caption -->
<figure>
    <img src="gunung-bromo.jpg" alt="Pemandangan Gunung Bromo saat matahari terbit" width="600" />
    <figcaption>Gambar 1: Gunung Bromo, Jawa Timur - salah satu destinasi wisata terpopuler di Indonesia.</figcaption>
</figure>

<!-- Bisa juga untuk video -->
<figure>
    <video src="tutorial.mp4" controls width="600"></video>
    <figcaption>Video: Tutorial membuat halaman web sederhana.</figcaption>
</figure>

<!-- Bisa juga untuk kode -->
<figure>
    <pre><code>console.log("Hello, World!");</code></pre>
    <figcaption>Contoh kode JavaScript "Hello, World!"</figcaption>
</figure>
```

### Iframe

`<iframe>` (Inline Frame) digunakan untuk menyematkan halaman atau konten lain di dalam halaman HTML.

```html
<!-- Menyematkan halaman lain -->
<iframe
    src="https://www.wikipedia.org"
    width="800"
    height="500"
    title="Wikipedia"
></iframe>

<!-- Menyematkan Google Maps -->
<iframe
    src="https://www.google.com/maps/embed?pb=!1m18!1m12!..."
    width="600"
    height="450"
    style="border:0;"
    allowfullscreen=""
    loading="lazy"
    title="Lokasi Kantor"
></iframe>

<!-- Menyematkan video YouTube -->
<iframe
    width="560"
    height="315"
    src="https://www.youtube.com/embed/dQw4w9WgXcQ"
    title="Video YouTube"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen
></iframe>
```

> **Catatan Keamanan:** Selalu tambahkan atribut `title` pada iframe untuk aksesibilitas. Tidak semua website mengizinkan untuk di-embed dalam iframe.

### Picture (Gambar Responsif)

Tag `<picture>` memungkinkan browser memilih gambar yang paling sesuai berdasarkan ukuran layar atau format yang didukung.

```html
<picture>
    <!-- Untuk layar besar: gambar resolusi tinggi -->
    <source media="(min-width: 800px)" srcset="gambar-besar.jpg" />
    <!-- Untuk layar sedang -->
    <source media="(min-width: 400px)" srcset="gambar-sedang.jpg" />
    <!-- Fallback: jika browser tidak mendukung picture -->
    <img src="gambar-kecil.jpg" alt="Deskripsi gambar" />
</picture>
```

---

## Form Lanjutan

Di pertemuan 1 kita sudah belajar form dasar. Sekarang kita akan mempelajari input types tambahan, fitur validasi bawaan HTML5, dan cara mengelompokkan form.

### Input Types HTML5 Tambahan

```html
<form>
    <!-- Range / Slider -->
    <label for="volume">Volume: <span id="volLabel">50</span></label>
    <input type="range" id="volume" name="volume" min="0" max="100" value="50" />

    <!-- Color Picker -->
    <label for="warna">Warna Favorit:</label>
    <input type="color" id="warna" name="warna" value="#4f46e5" />

    <!-- Search -->
    <label for="cari">Cari:</label>
    <input type="search" id="cari" name="cari" placeholder="Ketik pencarian..." />

    <!-- URL -->
    <label for="website">Website:</label>
    <input type="url" id="website" name="website" placeholder="https://contoh.com" />

    <!-- Telepon -->
    <label for="telp">No. Telepon:</label>
    <input type="tel" id="telp" name="telp" placeholder="+62812345678" />

    <!-- Waktu -->
    <label for="waktu">Waktu:</label>
    <input type="time" id="waktu" name="waktu" />

    <!-- Bulan -->
    <label for="bulan">Bulan:</label>
    <input type="month" id="bulan" name="bulan" />

    <!-- Week -->
    <label for="minggu">Minggu:</label>
    <input type="week" id="minggu" name="minggu" />

    <!-- File Upload -->
    <label for="berkas">Upload File:</label>
    <input type="file" id="berkas" name="berkas" accept=".pdf,.jpg,.png" />

    <!-- Multiple File Upload -->
    <label for="foto">Upload Foto:</label>
    <input type="file" id="foto" name="foto" accept="image/*" multiple />

    <!-- Hidden Input (tidak terlihat, untuk data tersembunyi) -->
    <input type="hidden" name="user_id" value="12345" />
</form>
```

### Datalist (Autocomplete)

`<datalist>` memberikan saran pilihan pada input, seperti autocomplete.

```html
<label for="kota">Kota Asal:</label>
<input type="text" id="kota" name="kota" list="daftar-kota" placeholder="Ketik nama kota..." />

<datalist id="daftar-kota">
    <option value="Jakarta" />
    <option value="Bandung" />
    <option value="Surabaya" />
    <option value="Yogyakarta" />
    <option value="Medan" />
    <option value="Makassar" />
    <option value="Semarang" />
    <option value="Palembang" />
</datalist>
```

> `<datalist>` berbeda dengan `<select>`: pengguna tetap bisa mengetik bebas, datalist hanya memberikan saran.

### Fieldset & Legend

`<fieldset>` digunakan untuk mengelompokkan elemen form yang saling berkaitan. `<legend>` adalah judul dari kelompok tersebut.

```html
<form action="/daftar" method="POST">

    <fieldset>
        <legend>Informasi Pribadi</legend>

        <div>
            <label for="nama">Nama Lengkap:</label>
            <input type="text" id="nama" name="nama" required />
        </div>
        <div>
            <label for="ttl">Tanggal Lahir:</label>
            <input type="date" id="ttl" name="ttl" required />
        </div>
        <div>
            <p>Jenis Kelamin:</p>
            <input type="radio" id="pria" name="gender" value="pria" />
            <label for="pria">Pria</label>
            <input type="radio" id="wanita" name="gender" value="wanita" />
            <label for="wanita">Wanita</label>
        </div>
    </fieldset>

    <fieldset>
        <legend>Informasi Akun</legend>

        <div>
            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required />
        </div>
        <div>
            <label for="pass">Password:</label>
            <input type="password" id="pass" name="pass" minlength="8" required />
        </div>
        <div>
            <label for="konfirmasi">Konfirmasi Password:</label>
            <input type="password" id="konfirmasi" name="konfirmasi" required />
        </div>
    </fieldset>

    <fieldset>
        <legend>Minat & Ketertarikan</legend>

        <p>Pilih minat kamu (boleh lebih dari satu):</p>
        <input type="checkbox" id="coding" name="minat" value="coding" />
        <label for="coding">Coding</label>

        <input type="checkbox" id="desain" name="minat" value="desain" />
        <label for="desain">Desain</label>

        <input type="checkbox" id="bisnis" name="minat" value="bisnis" />
        <label for="bisnis">Bisnis</label>

        <input type="checkbox" id="data" name="minat" value="data" />
        <label for="data">Data Science</label>
    </fieldset>

    <button type="submit">Daftar</button>
</form>
```

### Validasi Form HTML5

HTML5 menyediakan validasi bawaan tanpa JavaScript.

```html
<form>
    <!-- required: field wajib diisi -->
    <input type="text" name="nama" required />

    <!-- minlength / maxlength: panjang teks minimum/maksimum -->
    <input type="text" name="username" minlength="3" maxlength="20" />

    <!-- min / max: nilai minimum/maksimum (untuk number, date, range) -->
    <input type="number" name="umur" min="17" max="60" />
    <input type="date" name="tanggal" min="2024-01-01" max="2024-12-31" />

    <!-- pattern: validasi menggunakan regex -->
    <!-- Contoh: hanya boleh huruf dan angka -->
    <input type="text" name="kode" pattern="[A-Za-z0-9]+" title="Hanya boleh huruf dan angka" />

    <!-- Contoh: format nomor telepon Indonesia -->
    <input
        type="tel"
        name="telp"
        pattern="(\+62|08)[0-9]{8,12}"
        title="Format: 08xx atau +62xx, 10-14 digit"
    />

    <!-- step: interval nilai (untuk number dan range) -->
    <input type="number" name="harga" min="0" max="1000000" step="1000" />

    <!-- novalidate: menonaktifkan validasi HTML5 di seluruh form -->
    <!-- (biasanya digunakan jika pakai validasi JavaScript sendiri) -->
    <!-- <form novalidate> -->

    <button type="submit">Kirim</button>
</form>
```

### Select Lanjutan

```html
<!-- Select dengan optgroup (mengelompokkan pilihan) -->
<label for="bahasa">Bahasa Pemrograman:</label>
<select id="bahasa" name="bahasa">
    <option value="">-- Pilih Bahasa --</option>

    <optgroup label="Frontend">
        <option value="html">HTML</option>
        <option value="css">CSS</option>
        <option value="javascript">JavaScript</option>
    </optgroup>

    <optgroup label="Backend">
        <option value="python">Python</option>
        <option value="php">PHP</option>
        <option value="nodejs">Node.js</option>
        <option value="java">Java</option>
    </optgroup>

    <optgroup label="Mobile">
        <option value="swift">Swift</option>
        <option value="kotlin">Kotlin</option>
        <option value="flutter">Flutter/Dart</option>
    </optgroup>
</select>

<!-- Select multiple (pilih lebih dari satu) -->
<label for="skill">Skill (tahan Ctrl/Cmd untuk pilih banyak):</label>
<select id="skill" name="skill" multiple size="5">
    <option value="html">HTML</option>
    <option value="css">CSS</option>
    <option value="js">JavaScript</option>
    <option value="react">React</option>
    <option value="python">Python</option>
</select>
```

---

## Meta Tags & SEO Dasar

Tag `<meta>` berada di dalam `<head>` dan berisi informasi tentang halaman yang tidak ditampilkan langsung ke pengguna, tetapi penting untuk browser dan mesin pencari.

### Meta Tags Wajib

```html
<head>
    <!-- Encoding karakter (selalu gunakan UTF-8) -->
    <meta charset="UTF-8" />

    <!-- Tampilan di perangkat mobile (selalu sertakan) -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <!-- Judul halaman (muncul di tab browser & hasil pencarian) -->
    <title>Toko Online Budi - Belanja Elektronik Terpercaya</title>
</head>
```

### Meta Tags untuk SEO

```html
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Toko Online Budi - Belanja Elektronik Terpercaya</title>

    <!-- Deskripsi halaman (muncul di hasil pencarian Google, maks ~160 karakter) -->
    <meta name="description" content="Toko Online Budi menyediakan berbagai elektronik berkualitas dengan harga terjangkau. Pengiriman ke seluruh Indonesia." />

    <!-- Kata kunci (kurang penting saat ini, tapi tidak ada salahnya) -->
    <meta name="keywords" content="toko online, elektronik, laptop, smartphone, murah" />

    <!-- Nama penulis/pembuat halaman -->
    <meta name="author" content="Budi Santoso" />

    <!-- Robots: instruksi untuk mesin pencari -->
    <!-- index = boleh diindeks, follow = boleh mengikuti link -->
    <meta name="robots" content="index, follow" />
</head>
```

### Open Graph Meta Tags (Media Sosial)

Open Graph (OG) mengatur tampilan saat link dibagikan di media sosial (Facebook, WhatsApp, Twitter, dll).

```html
<head>
    <!-- ... meta tags lainnya ... -->

    <!-- Open Graph -->
    <meta property="og:title" content="Toko Online Budi - Belanja Elektronik Terpercaya" />
    <meta property="og:description" content="Toko Online Budi menyediakan berbagai elektronik berkualitas." />
    <meta property="og:image" content="https://tokobudi.com/images/og-image.jpg" />
    <meta property="og:url" content="https://tokobudi.com" />
    <meta property="og:type" content="website" />

    <!-- Twitter Card (khusus Twitter/X) -->
    <meta name="twitter:card" content="summary_large_image" />
    <meta name="twitter:title" content="Toko Online Budi" />
    <meta name="twitter:description" content="Belanja elektronik terpercaya." />
    <meta name="twitter:image" content="https://tokobudi.com/images/twitter-card.jpg" />
</head>
```

### Favicon

Favicon adalah ikon kecil yang muncul di tab browser dan bookmark.

```html
<head>
    <!-- Favicon format ICO (paling kompatibel) -->
    <link rel="icon" type="image/x-icon" href="/favicon.ico" />

    <!-- Favicon format PNG (modern) -->
    <link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png" />
    <link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png" />

    <!-- Apple Touch Icon (untuk iPhone/iPad) -->
    <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png" />
</head>
```

### Link Tag Lainnya di `<head>`

```html
<head>
    <!-- Menghubungkan file CSS eksternal -->
    <link rel="stylesheet" href="styles.css" />

    <!-- Canonical URL (menghindari konten duplikat) -->
    <link rel="canonical" href="https://tokobudi.com/laptop" />

    <!-- Preconnect: koneksi awal ke domain lain untuk performa -->
    <link rel="preconnect" href="https://fonts.googleapis.com" />

    <!-- Preload: muat sumber daya penting lebih awal -->
    <link rel="preload" href="hero-image.jpg" as="image" />

    <!-- Stylesheet dari Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet" />
</head>
```

---

## HTML Entities

HTML entities digunakan untuk menampilkan karakter khusus yang memiliki makna di HTML, atau karakter yang tidak ada di keyboard.

### Mengapa Perlu Entities?

Karakter seperti `<`, `>`, dan `&` memiliki makna khusus di HTML. Jika ingin menampilkannya sebagai teks biasa, harus menggunakan entities.

```html
<!-- SALAH: browser akan mengira ini adalah tag -->
<p>Rumus: a < b && b > c</p>

<!-- BENAR: menggunakan entities -->
<p>Rumus: a &lt; b &amp;&amp; b &gt; c</p>
```

### Tabel Entities yang Sering Digunakan

| Karakter | Entity Name | Entity Number | Keterangan |
|----------|-------------|---------------|------------|
| `<` | `&lt;` | `&#60;` | Less than |
| `>` | `&gt;` | `&#62;` | Greater than |
| `&` | `&amp;` | `&#38;` | Ampersand |
| `"` | `&quot;` | `&#34;` | Tanda kutip |
| `'` | `&apos;` | `&#39;` | Apostrof |
| ` ` (spasi) | `&nbsp;` | `&#160;` | Non-breaking space |
| `©` | `&copy;` | `&#169;` | Copyright |
| `®` | `&reg;` | `&#174;` | Registered trademark |
| `™` | `&trade;` | `&#8482;` | Trademark |
| `€` | `&euro;` | `&#8364;` | Euro |
| `£` | `&pound;` | `&#163;` | Pound |
| `¥` | `&yen;` | `&#165;` | Yen |
| `→` | `&rarr;` | `&#8594;` | Panah kanan |
| `←` | `&larr;` | `&#8592;` | Panah kiri |
| `♥` | `&hearts;` | `&#9829;` | Hati |
| `★` | `&#9733;` | `&#9733;` | Bintang penuh |

### Contoh Penggunaan

```html
<p>Hak cipta &copy; 2025 Perusahaan Kami. All rights reserved.</p>

<p>Produk ini adalah merek terdaftar &reg; dari PT. Contoh Jaya.</p>

<p>Harga: &euro;99 atau &pound;85 atau &yen;15.000</p>

<!-- Non-breaking space: mencegah kata terpotong saat wrap -->
<p>Presiden&nbsp;Joko&nbsp;Widodo hadir dalam acara tersebut.</p>

<!-- Menampilkan kode HTML sebagai teks -->
<p>Untuk membuat heading, gunakan tag <code>&lt;h1&gt;</code> hingga <code>&lt;h6&gt;</code>.</p>
```

---

## Atribut Global

Atribut global dapat digunakan pada **semua elemen HTML**. Berikut yang paling penting:

### `id` dan `class`

```html
<!-- id: identifikasi unik, hanya boleh ada satu per halaman -->
<div id="header-utama">Header</div>
<p id="paragraf-intro">Paragraf perkenalan.</p>

<!-- class: bisa digunakan berulang kali, satu elemen bisa punya banyak class -->
<div class="kartu">Kartu 1</div>
<div class="kartu">Kartu 2</div>
<div class="kartu kartu-featured">Kartu Unggulan</div>
```

### `title`

Memberikan tooltip saat kursor diarahkan ke elemen.

```html
<p title="Ini adalah paragraf dengan tooltip">Arahkan kursor ke sini.</p>

<abbr title="HyperText Markup Language">HTML</abbr> adalah bahasa markup.

<a href="dokumen.pdf" title="Download dokumen PDF, ukuran 2.5MB">Download</a>
```

### `data-*` (Custom Data Attributes)

`data-*` digunakan untuk menyimpan data kustom yang tidak perlu ditampilkan ke pengguna, biasanya digunakan oleh JavaScript.

```html
<!-- Menyimpan data produk -->
<div class="produk" data-id="101" data-harga="150000" data-stok="25">
    <h3>Kaos Polos</h3>
    <button class="tombol-beli">Beli Sekarang</button>
</div>

<!-- Menyimpan data pengguna -->
<button data-user-id="42" data-aksi="hapus" class="btn-hapus">
    Hapus Akun
</button>

<!-- Mengakses dengan JavaScript -->
<!-- 
    const produk = document.querySelector('.produk');
    console.log(produk.dataset.id);    // "101"
    console.log(produk.dataset.harga); // "150000"
-->
```

### `tabindex`

Mengatur urutan fokus saat pengguna menekan Tab untuk navigasi keyboard.

```html
<!-- tabindex="0": ikuti urutan normal DOM -->
<button tabindex="0">Tombol Normal</button>

<!-- tabindex="-1": tidak bisa difokus dengan Tab (tapi bisa dengan JavaScript) -->
<div tabindex="-1" id="modal">Modal Dialog</div>

<!-- tabindex positif: urutan kustom (kurang disarankan) -->
<input tabindex="1" type="text" placeholder="Fokus pertama" />
<input tabindex="3" type="text" placeholder="Fokus ketiga" />
<input tabindex="2" type="text" placeholder="Fokus kedua" />
```

### `hidden`

Menyembunyikan elemen (seperti `display: none` di CSS).

```html
<p hidden>Paragraf ini tidak terlihat oleh pengguna.</p>

<div id="pesan-sukses" hidden>
    ✅ Data berhasil disimpan!
</div>
```

### `contenteditable`

Membuat konten elemen bisa diedit langsung oleh pengguna di browser.

```html
<div contenteditable="true" style="border: 1px solid #ccc; padding: 10px;">
    Klik teks ini untuk mengeditnya langsung di browser!
</div>
```

### `draggable`

Mengaktifkan fitur drag-and-drop pada elemen.

```html
<div draggable="true">
    Elemen ini bisa di-drag!
</div>
```

---

## Aksesibilitas HTML (A11y)

Aksesibilitas (disingkat A11y) adalah praktik membuat halaman web yang dapat digunakan oleh **semua orang**, termasuk pengguna dengan disabilitas (pengguna screen reader, keyboard-only, dll).

### Mengapa Aksesibilitas Penting?

1. **Inklusivitas** - Semua orang berhak mengakses informasi
2. **SEO** - Website yang aksesibel lebih disukai mesin pencari
3. **Legalitas** - Di beberapa negara, aksesibilitas web diwajibkan oleh hukum
4. **Pengalaman Pengguna** - Website yang aksesibel umumnya lebih mudah digunakan semua orang

### Alt Text yang Baik

```html
<!-- ❌ Buruk: tidak ada alt text -->
<img src="promo-lebaran.jpg" />

<!-- ❌ Buruk: alt text tidak deskriptif -->
<img src="promo-lebaran.jpg" alt="gambar" />

<!-- ❌ Buruk: mengulangi kata "gambar" -->
<img src="promo-lebaran.jpg" alt="gambar promo lebaran" />

<!-- ✅ Baik: deskriptif dan informatif -->
<img src="promo-lebaran.jpg" alt="Promo Lebaran: diskon 50% untuk semua produk elektronik, berlaku 1-10 April 2025" />

<!-- Gambar dekoratif: gunakan alt="" (kosong) agar screen reader melewatinya -->
<img src="garis-dekoratif.png" alt="" />
```

### Label pada Form

```html
<!-- ❌ Buruk: input tanpa label -->
<input type="text" placeholder="Nama" />

<!-- ❌ Buruk: label tidak terhubung ke input -->
<label>Nama</label>
<input type="text" />

<!-- ✅ Baik cara 1: menggunakan for & id -->
<label for="nama-lengkap">Nama Lengkap:</label>
<input type="text" id="nama-lengkap" name="nama" />

<!-- ✅ Baik cara 2: input di dalam label -->
<label>
    Nama Lengkap:
    <input type="text" name="nama" />
</label>
```

### ARIA (Accessible Rich Internet Applications)

ARIA adalah atribut tambahan untuk meningkatkan aksesibilitas ketika HTML semantik saja tidak cukup.

```html
<!-- aria-label: label untuk elemen yang tidak memiliki teks terlihat -->
<button aria-label="Tutup dialog">✕</button>

<nav aria-label="Navigasi utama">
    <a href="/">Home</a>
    <a href="/about">Tentang</a>
</nav>

<!-- aria-hidden: menyembunyikan elemen dari screen reader -->
<!-- (untuk elemen dekoratif atau yang sudah ada teks alternatifnya) -->
<span aria-hidden="true">★★★★☆</span>
<span class="sr-only">Rating: 4 dari 5 bintang</span>

<!-- aria-required: menandai field wajib (gunakan bersama required) -->
<input type="text" required aria-required="true" />

<!-- aria-expanded: menandai apakah elemen diperluas atau tidak -->
<button aria-expanded="false" aria-controls="dropdown-menu">
    Menu
</button>
<ul id="dropdown-menu" hidden>
    <li><a href="/">Home</a></li>
    <li><a href="/about">Tentang</a></li>
</ul>

<!-- role: mendefinisikan peran elemen secara eksplisit -->
<div role="alert">
    ⚠️ Sesi Anda akan berakhir dalam 5 menit.
</div>

<div role="navigation" aria-label="Breadcrumb">
    <a href="/">Home</a> &rsaquo;
    <a href="/produk">Produk</a> &rsaquo;
    <span aria-current="page">Laptop</span>
</div>
```

### Navigasi Keyboard

Pastikan semua fungsi bisa diakses melalui keyboard (Tab, Enter, Space, Arrow keys):

```html
<!-- ✅ Button: bisa diakses keyboard secara default -->
<button onclick="aksi()">Klik Saya</button>

<!-- ❌ Div sebagai tombol: tidak bisa diakses keyboard -->
<div onclick="aksi()">Klik Saya</div>

<!-- ✅ Jika harus menggunakan div, tambahkan role dan tabindex -->
<div role="button" tabindex="0" onclick="aksi()" onkeydown="if(event.key==='Enter')aksi()">
    Klik Saya
</div>
```

**Tips Aksesibilitas Umum:**
- Selalu gunakan tag HTML yang semantik (`<button>` bukan `<div>` untuk tombol)
- Pastikan kontras warna teks dengan latar belakang cukup (rasio minimal 4.5:1)
- Jangan andalkan warna saja untuk menyampaikan informasi
- Sertakan `<caption>` atau `aria-label` pada tabel kompleks
- Gunakan heading secara berurutan (`<h1>` → `<h2>` → `<h3>`)

---

## Latihan

### Latihan 1: Halaman Multimedia

Buat halaman HTML yang menampilkan galeri multimedia:

```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Galeri Multimedia</title>
</head>
<body>

    <header>
        <h1>Galeri Multimedia Saya</h1>
    </header>

    <main>
        <!-- TODO 1: Tambahkan section "Galeri Foto" dengan minimal 3 gambar -->
        <!-- Setiap gambar harus dibungkus dalam figure + figcaption -->
        <!-- Gunakan https://picsum.photos/400/300 untuk gambar placeholder -->

        <!-- TODO 2: Tambahkan section "Video Pilihan" -->
        <!-- Embed video YouTube favorit kamu menggunakan iframe -->

        <!-- TODO 3: Tambahkan section "Peta Lokasi" -->
        <!-- Embed Google Maps (lokasi kota kamu) menggunakan iframe -->
    </main>

    <footer>
        <p>&copy; 2025 Nama Kamu. All rights reserved.</p>
    </footer>

</body>
</html>
```

---

### Latihan 2: Form Pendaftaran Kursus Lengkap

Buat form pendaftaran kursus online dengan fieldset:

```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Pendaftaran Kursus Online</title>
</head>
<body>
    <h1>Form Pendaftaran Kursus Online</h1>

    <form action="/daftar" method="POST">

        <!-- TODO: Buat fieldset "Data Diri" dengan field: -->
        <!-- nama lengkap (text, required), email (email, required), -->
        <!-- no. telepon (tel, pattern validasi), tanggal lahir (date) -->

        <!-- TODO: Buat fieldset "Pilihan Kursus" dengan: -->
        <!-- dropdown kursus menggunakan optgroup (minimal 2 kategori, 3 kursus/kategori) -->
        <!-- datalist kota asal -->
        <!-- radio button: metode belajar (Online/Offline/Hybrid) -->

        <!-- TODO: Buat fieldset "Pengalaman" dengan: -->
        <!-- checkbox skill yang sudah dikuasai (minimal 5 pilihan) -->
        <!-- select level pengalaman (Pemula/Menengah/Mahir) -->
        <!-- textarea "Ceritakan tujuan belajar kamu" (required, minlength="50") -->

        <!-- TODO: Buat fieldset "Upload Dokumen" dengan: -->
        <!-- input file untuk foto profil (accept hanya gambar) -->
        <!-- input file untuk CV (accept .pdf saja) -->

        <!-- TODO: Checkbox persetujuan syarat & ketentuan (required) -->

        <button type="submit">Daftar Sekarang</button>
        <button type="reset">Reset Form</button>
    </form>
</body>
</html>
```

---

### Latihan 3: Halaman dengan Meta Tags Lengkap

Lengkapi bagian `<head>` dari template berikut:

```html
<!DOCTYPE html>
<html lang="id">
<head>
    <!-- TODO: Tambahkan charset dan viewport -->

    <!-- TODO: Tambahkan title yang SEO-friendly -->

    <!-- TODO: Tambahkan meta description (maks 160 karakter) -->

    <!-- TODO: Tambahkan meta author -->

    <!-- TODO: Tambahkan Open Graph tags (og:title, og:description, og:image, og:url) -->

    <!-- TODO: Tambahkan favicon (boleh gunakan emoji sebagai SVG favicon) -->
    <!-- Hint: <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>🛒</text></svg>" /> -->
</head>
<body>
    <h1>Toko Online Saya</h1>
    <p>Selamat datang di toko online kami!</p>
</body>
</html>
```

---

### Latihan 4: Perbaiki Aksesibilitas

Temukan dan perbaiki semua masalah aksesibilitas pada kode berikut:

```html
<!-- Kode BERMASALAH - perbaiki semua kesalahan aksesibilitas -->
<!DOCTYPE html>
<html>
<head>
    <title>Blog</title>
</head>
<body>

    <!-- Masalah 1: Tidak ada lang attribute di html -->
    <!-- Masalah 2: Tidak ada meta charset dan viewport -->

    <div>
        <!-- Masalah 3: Navigasi tidak menggunakan tag semantic yang tepat -->
        <a href="/">Home</a>
        <a href="/blog">Blog</a>
        <a href="/kontak">Kontak</a>
    </div>

    <div>
        <!-- Masalah 4: Heading tidak berurutan -->
        <h3>Artikel Terbaru</h3>

        <div>
            <!-- Masalah 5: Gambar tanpa alt text -->
            <img src="artikel1.jpg" />
            <h5>Judul Artikel 1</h5>
            <p>Deskripsi artikel 1...</p>
            <!-- Masalah 6: Div digunakan sebagai tombol -->
            <div onclick="bacaLebih(1)">Baca Selengkapnya</div>
        </div>

        <div>
            <img src="artikel2.jpg" alt="gambar" />
            <h5>Judul Artikel 2</h5>
            <p>Deskripsi artikel 2...</p>
            <div onclick="bacaLebih(2)">Baca Selengkapnya</div>
        </div>
    </div>

    <div>
        <!-- Masalah 7: Form tanpa label yang terhubung -->
        <h3>Berlangganan Newsletter</h3>
        <form>
            Email: <input type="text" placeholder="email kamu" />
            <!-- Masalah 8: Input email menggunakan type="text" -->
            <div onclick="daftar()">Daftar</div>
            <!-- Masalah 9: Tombol bukan menggunakan tag button -->
        </form>
    </div>

    <div>
        <!-- Masalah 10: Tidak ada info copyright yang jelas dan tidak pakai footer -->
        Hak Cipta 2025
    </div>

</body>
</html>
```

---

## Tugas Mandiri

### Challenge: Website Blog Pribadi yang Aksesibel

Buat website **Blog Pribadi** yang terdiri dari **2 halaman** dengan standar aksesibilitas dan SEO yang baik:

#### Halaman 1: Beranda Blog (`index.html`)

**Bagian `<head>` harus memiliki:**
- Charset, viewport, title
- Meta description dan author
- Open Graph tags
- Favicon

**Konten halaman:**
- `<header>` dengan navigasi menggunakan `<nav>` (link ke index.html dan artikel.html)
- Section hero: judul blog + tagline + foto profil (dengan alt text deskriptif)
- Section "Artikel Terbaru": minimal 3 preview artikel
  - Setiap artikel berisi: gambar (dengan figure + figcaption), judul (h2), tanggal, cuplikan teks, tombol "Baca Selengkapnya"
  - Setiap tombol harus menggunakan tag `<a>` atau `<button>`, **bukan div**
- Section "Tentang Saya": foto + paragraf perkenalan + list keahlian
- `<footer>` dengan copyright entity `&copy;` dan link media sosial

#### Halaman 2: Halaman Artikel (`artikel.html`)

**Konten halaman:**
- `<header>` dengan navigasi yang sama
- `<main>` berisi satu artikel panjang dengan:
  - Heading yang berurutan (h1 → h2 → h3)
  - Minimal 3 paragraf
  - Satu gambar (figure + figcaption dengan alt text yang baik)
  - Satu blockquote dengan atribut `cite`
  - Satu tabel data sederhana (dengan `<caption>`)
  - Daftar (ul atau ol)
  - HTML entities minimal 3 jenis
- `<aside>` berisi "Artikel Terkait" (list link minimal 3)
- `<footer>` yang sama

#### Kriteria Penilaian:

- [ ] Meta tags lengkap di kedua halaman
- [ ] Semua gambar memiliki alt text yang deskriptif
- [ ] Semua input form memiliki label yang terhubung
- [ ] Menggunakan semantic HTML dengan benar
- [ ] Heading berurutan (tidak melompat)
- [ ] Navigasi menggunakan `<nav>` dan dapat diakses keyboard
- [ ] HTML entities digunakan dengan benar
- [ ] Fieldset dan legend untuk form (jika ada)
- [ ] Kode valid (cek dengan [validator.w3.org](https://validator.w3.org))

#### Fitur Bonus (Nilai Tambah):
- [ ] Tambahkan tabel dengan `colspan` atau `rowspan`
- [ ] Tambahkan elemen `<video>` atau `<audio>`
- [ ] Tambahkan `aria-label` pada elemen yang membutuhkan
- [ ] Tambahkan `data-*` attribute pada elemen yang relevan

---

## Ringkasan Materi

| Topik | Elemen/Atribut Kunci |
|-------|----------------------|
| Block vs Inline | `<div>`, `<span>`, `<blockquote>`, `<q>` |
| Media | `<video>`, `<audio>`, `<figure>`, `<figcaption>`, `<iframe>`, `<picture>` |
| Form Lanjutan | `<datalist>`, `<fieldset>`, `<legend>`, `<optgroup>`, `type="range/color/file"` |
| Validasi Form | `required`, `minlength`, `maxlength`, `min`, `max`, `pattern`, `step` |
| Meta & SEO | `<meta name>`, `<meta property>` (OG), `<link rel="icon">` |
| HTML Entities | `&lt;`, `&gt;`, `&amp;`, `&copy;`, `&nbsp;` |
| Atribut Global | `id`, `class`, `title`, `data-*`, `tabindex`, `hidden` |
| Aksesibilitas | `alt`, `aria-label`, `aria-hidden`, `role`, `label[for]` |

---

## Referensi

- [MDN Web Docs - HTML Elements Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)
- [MDN Web Docs - ARIA](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA)
- [W3C HTML Validator](https://validator.w3.org)
- [WebAIM - Aksesibilitas Web](https://webaim.org)
- [Open Graph Protocol](https://ogp.me)
- [HTML Entities Reference - W3Schools](https://www.w3schools.com/html/html_entities.asp)

---

**Selamat Belajar HTML Lebih Dalam!**

Pada pertemuan berikutnya, kita akan belajar **CSS** untuk mempercantik tampilan halaman HTML yang sudah kita buat!
