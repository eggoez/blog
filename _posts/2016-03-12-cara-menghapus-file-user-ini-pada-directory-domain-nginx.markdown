---
layout: post
date: 2016-03-12 17:18:35 +0700
title: Menghapus file .user.ini pada directory domain nginx
categories: vps
tags: apache Debian Linux nginx SSH
---
<p>Jika anda menghapus sebuah domain dari nginx server anda pastinya nginx untuk alasan security tidak menghapus directory atau folder domain anda, dan akan menyisakan semua isi file yang sudah ada.</p>
<p>Nah ketika anda sudah selesai dan ingin hapus semua file/folder domain anda misalnya</p>
{% highlight shell_session %}
cd /home/wwwroot/
root@vps:/home/wwwroot# rm -rf eggoez.com
rm: cannot remove 'eggoez.com/.user.ini': Operation not permitted{% endhighlight %}
<p><span id="more-2067"></span></p>
<p>Nah apa sih masalahnya? jadi file .user.ini ini tidak bisa di hapus, lalu gimana cara hapusnya? cobain<br>
masuk ke directory dimana .user.ini berada contoh</p>
{% highlight terminal %}
cd /home/wwwroot/eggoez.com
root@vps:/home/eggoez.com# ls -all
total 12
drwxr-xr-x 2 www  www  4096 Mar 12 16:21 .
drwxr-xr-x 5 root root 4096 Mar 12 16:40 ..
-rw-r--r-- 1 root root   65 Mar 12 16:21 .user.ini
root@vps:/home/wwwroot/eggoez.com#{% endhighlight %}
<p>langsung aja anda chattr ya contoh</p>
{% highlight terminal %}
chattr +i .user.ini &amp;&amp; chattr -i .user.ini
{% endhighlight %}
<p>lalu kembali ke directory sebelumnya</p>
{% highlight terminal %}
cd ..{% endhighlight %}>
<p>cobain hapus foldernya</p>
{% highlight shell %}rm -rf eggoez.com{% endhighlight %}
<p>Beres <img src="https://eggoez.bitbucket.io/wp-content/emojione/png/1f643.png" alt=":)" class="emojione" style="font-size:inherit;height:3ex;width:3.1ex;min-height:20px;min-width:20px;display:inline-block;margin:-.2ex .15em .2ex;line-height:normal;vertical-align:middle"></p>
