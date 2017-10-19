---
layout: post
date: 2016-04-08 17:18:35 +0700
title: Cara Membuat Icons Font Awesome Bergerak
categories: bagaimana
tags: code
---
<p>NB: Untuk melihat icons nya berfungsi di tulisan ini jika anda menggunakan tampilan mobile/classic beralihlah ke tampilan Desktop.</p>
<p>Pastinya sudah pada tau kan apa itu Font Awesome? buat anda yang belum tau bisa langsung menuju halaman <a href="https://fortawesome.github.io/Font-Awesome/icons/">Font Awesome</a>.</p>
<p>Nah di kesempatan yang sempit ini saya ingin memberi tutorial bagaimana membuat icons awesome itu bergerak, bagini cara menganimasikan, animasi ini di kembangkan oleh <strong><a href="https://github.com/l-lin">Louis LIN</a></strong> ya, anda bisa fork project nya di <a href="https://github.com/l-lin/font-awesome-animation" target="_blank">github</a>.</p>
<p>Pertama tambahkan css tambahan untuk menganimasikan font awesome nya dengan cara tambahkan kode ini di header anda</p>
<pre><span class="nt">&lt;link</span> <span class="na">rel=</span><span class="s">"stylesheet"</span> <span class="na">href=</span><span class="s">"https://cdnjs.cloudflare.com/ajax/libs/font-awesome-animation/0.0.8/font-awesome-animation.min.css"</span><span class="nt">&gt;</span>
</pre>
<p>Atau anda bisa langsung menjadikan satu dengan css anda cara import contoh:</p>
<pre>@import url("https://cdnjs.cloudflare.com/ajax/libs/font-awesome-animation/0.0.8/font-awesome-animation.min.css");</pre>
<p>Tempatkan line paling atas css anda kode tersebut, atau anda bisa langsung manggabungkan kodenya dengan css anda.</p>
<p>Lalu setelah itu cara menggunakanya cukup mudah yaitu dengan cara memanggil class icon awesome anda spasi class animasinya.</p>
<blockquote><p><code></code><code class="html"><span class="nt">&lt;i</span> <span class="na">class=</span><span class="s">"fa fa-ikon-anda animasinya"</span><span class="nt">&gt;&lt;/i&gt;</span> </code></p></blockquote>
<p>Class animasinya anda bisa lihat <a href="https://l-lin.github.io/font-awesome-animation/" target="_blank">di sini</a>. Intinya ke dua class tersebut anda gabung menjadi satu, tambahkan spasi untuk menambah class lebih dari satu, sebagai contoh:</p>
<pre><i class="fa fa-thumbs-up faa-bounce animated"></i><code> &lt;i class="fa fa-thumbs-up fa-2x faa-bounce animated"&gt;&lt;/i&gt;</code></pre>
<pre><i class="fa fa-thumbs-o-down faa-vertical animated"></i> &lt;i class="fa fa-thumbs-o-down faa-vertical animated"&gt;</pre>
<pre><i class="fa fa-hand-paper-o faa-shake animated"></i> &lt;i class="fa fa-hand-paper-o faa-shake animated"&gt;</pre>
<pre><i class="fa fa-play-circle faa-pulse animated"></i> &lt;i class="fa fa-play-circle faa-pulse animated"&gt;</pre>
<p>Mudah kan, untuk membuat bergerak ikon nya saat di hover/klik ikuti aja kodenya On Hover, contoh:</p>
<pre><i class="fa fa-heart faa-tada animated-hover"></i> <code>&lt;i class="fa fa-heart faa-tada animated-hover"&gt;&lt;/i&gt;</code></pre>
<pre><i class="fa fa-heart faa-tada animated-hover" style="color: #f66767;"></i> <code>&lt;i class="fa fa-heart faa-tada animated-hover" </code><span class="attribute-name">style</span>="<a class="attribute-value">color:#f66767</a>"<code>&gt;&lt;/i&gt;</code></pre>
<p>Di atas adalah hover jika di klik ikon nya saja, jadi misal di depan link ada icon nya ketika link di hit icon nya tidak bergerak kalau yang di hit bukan icons nya, untuk membuat gerak juga ketika posisi area link di hit anda perlu menambah class <code>faa-parent animated-hover</code> di alamat href link nya, dan class icons nya di isi class “On Parent Hover” contoh</p>
<pre><a class="faa-parent animated-hover" href="#"><i class="fa fa-thumbs-up faa-pulse"></i> Sukai ini</a> <code> &lt;a href="#" class="faa-parent animated-hover"&gt;&lt;i class="fa fa-thumbs-up faa-pulse"&gt;&lt;/i&gt; Sukai ini&lt;/a&gt;</code></pre>
<p>Anda juga bisa mempercepat atau memperlambat gerakan animasi dengan menambah class <code>faa-fast</code> untuk lebih cepat dan <code>faa-slow</code> untuk lebih lambat. <img src="https://eggoez.bitbucket.io/wp-content/emojione/png/1f913.png" alt="🤓" class="emojione" style="font-size:inherit;height:3ex;width:3.1ex;min-height:20px;min-width:20px;display:inline-block;margin:-.2ex .15em .2ex;line-height:normal;vertical-align:middle"> </p>
<p>Jadi seperti itu kurang lebih cara membuat animasi fort awesome ikon nya bergerak <img src="https://eggoez.bitbucket.io/wp-content/emojione/png/1f643.png" alt=":)" class="emojione" style="font-size:inherit;height:3ex;width:3.1ex;min-height:20px;min-width:20px;display:inline-block;margin:-.2ex .15em .2ex;line-height:normal;vertical-align:middle"></p>
