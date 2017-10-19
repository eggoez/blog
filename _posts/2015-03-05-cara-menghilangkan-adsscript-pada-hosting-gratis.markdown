---
layout: post
date: 2015-03-05 17:18:35 +0700
title: Cara Menghilangkan Ads/Script pada hosting gratis
categories: tips
tags: Hosting code
---
<p>Hosting gratisan adalah hosting tidak berbayar yang <strong>kebanyakan</strong> dipilih oleh orang indonesia :D<br>
Walau sebenarnya hosting gratis itu tidak se <strong>AMAN</strong> hosting berbayar, namun saya pribadi sangat kagum dengan hosting gratis, pasalnya mereka ada yang jauh lebih baik dari segi <strong>uptime</strong> dan <strong>fitur</strong>nya melebihi hosting berbayar, biasanya saya sebut <del>Hosting Gratis Rasa-h Bayar</del> ;) baik, karena banyak hosting gratis yang bermunculan maka anda harus pintar² memilih dan memilah hosting gratisnya, kebanyakan menurut pengalaman saya hosting gratis yang bagus dan berkualitas baik itu tidak luput dengan adanya iklan, ada juga hosting yang menyematkan ads/iklan/script pada halaman web anda, seperti sebut saja 000webhost, dsb.<span id="more-1498"></span></p>
<p><a href="https://eggoez.bitbucket.io/wp-content/uploads/2015/03/script-ads-free-hosting.png" class="fancybox image"><img class="alignleft wp-image-1510 " src="https://eggoez.bitbucket.io/wp-content/uploads/2015/03/script-ads-free-hosting.png" alt="Scripts/Ads Free Hosting" width="349" height="116"></a> namun jika anda ingin belajar membangun sebuah web tidak ada salahnya sebelum anda membeli hosting/vps anda jajal dulu hosting gratis yang saya rekomendasikan. bisa anda <a href="https://eggoez.bitbucket.io/flatpress/?x=entry:entry140311-041133;comments:1">baca di sini</a>. Baiklah kembali ke judul ya</p>
<blockquote><p>Jika anda terlanjur cinta dan sayang pada hosting gratis pilihan anda, dan rasanya tidak mau dan tidak mungkin untuk berpisah darinya, walau pada nyatanya dia punya kekurangan yaitu menyematkan scripts ads yang jujur membuat halaman anda tidak menarik dan membuat anda males atau bahkan malu mengakuinya :ha3:</p></blockquote>
<p>Jangan khawatir, ada beberapa cara/tips untuk menghilangkan itu, cara yang pertama adalah menonaktifkan script tersebut, dengan cara menambahkan baris kode untuk mengatakan tidak ada script pada broswer pengunjung, caranya, pastikan anda tahu kaki/footer halaman anda, dan anda tau dimana anda harus mencari footer tersebut,&nbsp; sekarang edit footer anda, yang anda rasa adalah bagian akhir dari web anda, karena kebanyakan script ads dipasang pada akhir yaitu setelah <code>&lt;/html&gt; </code>umumnya, tambakan kode ini</p>
<pre>&lt;/noscript&gt;</pre>
<p>Simpan. Cara di atas sudah mengilangkan iklan/script dihalaman anda.</p>
<p>Cara kedua, yaitu menambahkan elemen style untuk hide/menyembunyikan baris kode di bawahnya, letakkan kode nya di atas script iklan tersebut, hanya menambah baris kode ini jika halaman anda HTML</p>
<pre>&lt;iklan style="display:none"&gt;</pre>
<p>Untuk file .php jika halaman anda menggunakan php dan ditulis dengan kode pemrogaman php, berarti anda harus membuat <code>echo</code> untuk ditampilkan di html nya, sisipkan kode ini sebelum penutup <code>?&gt;</code> php anda dan pastikan letaknya di bawah <code>echo</code> penutup <code>&lt;/html&gt; </code>Hamalan anda.</p>
<pre>echo "&lt;iklan style="display:none;"&gt;";</pre>
<p>Cara ketiga (yang paling ampuh)<br>
Cara kedua di atas terbilang masih belum ampuh, sebab mereka hanya menonaktifkan dan menyembunyikan iklan yang di bawa script tersebut, halaman anda juga tidak clean/bersih sepenuhnya, dan halaman anda tidak valid menurut w3 validator, sebab ada tag yang belum tertutup pastinya, jika hosting anda mendukung PhP, cobalah kode berikut, tetap sama sisipkan dibaris bawah <code>&lt;/html&gt;</code> footer anda. Atau cari <code>index.php</code> anda dan sisipkan di bawah sendiri setelah penutup tag <code>?&gt;</code> php</p>
<pre>&lt;?php exit; ?&gt;</pre>
<p>Simpan dan lihat hasilnya ;) Ini akan membuat akhir dari halaman anda, jika ada script / tag di bawah kode ini tidak akan ditampilkan atau dimuat dihalaman anda, jadi halaman anda akan sepenuhnya bersih tanpa iklan, dan kelihatan cantik dengan penutup akhir <code>&lt;/html&gt;</code></p>
<p>Silahkan dicoba ;) Semoga bermanfaat :D</p>
