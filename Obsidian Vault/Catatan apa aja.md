==Description

```
File ini berisi tentang catatan apapun, file ini dibuat secara random. Untuk mencari catatak silahkan gunakan Ctrl + f, lalu cari apa yang akan dicari.

Jangan heran jika menemukan hal-hal yang gak nyambung 1 sama lain, karena ini memang tidak dibuat secara teratur.
```

GPT-3 API : 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
================================================================================================================================ 
1. Product Knowledge
   - domain dan hosting
     domain dan hosting adalah 2 hal yang tidak dipisahkan dari sebuah website, ibarat seperti sebuah bangunan hosting adalah
	 tanah/tempat untuk membangun dan domain adalah alamatnya agar mudah ditemukan oleh orang lain.

   - server
     - vps
	   vps adalah virtual private server 
	   
	 
   -i itu untuk insert atau edit vi di linux
   -wq (write quit) untuk save dan keluar dari editor vi
   -rm -rf buat hapus directori dan seluruh isinya
   - cara cek ip public itu cukup akses https://www.antmediahost.com/my-ip-address/
   -lokasi selinux /etc/selinux/config
 

- cara seting reccord semuanya ada di dns manager, carinya di whm cupang.
- kalau whm gabisa dibuka buka host acces control, ip yg di allow tidak boleh dibawah yg deny.
- Srx buat domain lokal, liquid buat internasional. Ini pengaturan oreder domain sebelum masuk server
- 

# cara ubah port ssh
	- ubah di /etc/ssh/sshd_config
	- lalu restart ssh, systemctl restart sshd
	- allow port di firewall, firewall-cmd --permanent --zone=public --add-port=PORT_BARU/tcp
	- reload firewall,firewall-cmd --reload
	
# instalasi csf di linux (centos)
	https://www.antmediahost.com/cara-install-csf-firewall-di-linux/
	
# kalau wordpress kena deface atau hack
	- cek .htaccess
	- cek permalink
	
# Untuk Install module php pada server buka "easyApache"

# kalau reseller gabisa akses whm
	buka "host access control" di whm cupang, terus tambah 'whostmgrd' dan alamat ip nya, lalu kasih
	catetan itu siapa.
	posisi yg allow harus ada diatas yg deny, intinya yg deny harus paling bawah
	
# Cripting kabel LAN
	- putih oren, oren
	- putih ijo, biru
	- putih biru, ijo
	- putih coklat, coklat
	

# Allow menggunakan iptables
	 iptables -I INPUT -p tcp --dport NOMOR_PORT --syn -j ACCEPT
	 
# shared hosting harus pakai id1 & id2
	id1.antmediahost.com
	id2.antmediahost.com

# dns default antmediahost
	103.146.62.250 dns 1
	103.146.63.250 dns 2
	
# my vps
	103.167.112.88
	hiji2tilu4
	
# Sementara ioncube di php 8.0 memang tidak di support (https://forums.cpanel.net/threads/ioncube-question.689069/) 
  dan disupport kembali diversi php 8.1. Untuk itu silahkan gunakan php 8.1
	
# kl abs change versi php. Bikin aja phpinfo, Kl msh gagal, ada yg g beres berarti.

# List blm paham
	-UCEPROTECTL3
	-cripting kabel lan biar ga 100mbps
	-ganti ip kasus qoohost3
	-edit record selain di cPanel/whm
	-renew ssl psht.or.id
	
# Winbox
	fungsinya untuk remote router
	
#aaPanel	
	Warning:
	If you cannot access the panel,
	release the following port (7800|888|80|443|20|21) in the security group
	
# JunkMail 
	Jika email tidak terkirim dan mendapat bouceback "JunkMail rejected", coba cek BoxTrapper, jika enable maka ganti menjadi disable.
	Login whm > Tweak Setting > BoxTrapper.
	
v=spf1 a:mx.masuk.email a:masuk.email a:mail.masuk.email ~all


/544d5653


# Kalau ada case yang sampe harus buat orang cPanel masuk server, yang di kasih itu alamat IP nya


kalau cPanel hanya 1 akun lebih baik jgn diaktifkan php-fpm

Log cpanel
 
 Ruko Amparanjati, Jl. Raya Pakuan Regency No.06, RT.01/RW.07, Margajaya, Bogor Barat, Bogor City, West Java 16116
 
 Jl. Kp. Grogol No. 111 RT.03/RW.02 (Ujung jln. H. Snaip, belok kanan dikit, rumah tingkat No. 111), Grogol, Limo, Kota Depok Jawa Barat 16512
 
 HP = 085691573210
 
 
 kalau ojs error di htaccess, coba hapus htaccess nya
 
#rsync update kloudmi
 rsync -avh --update --progress -e "ssh -p 3759" root@103.167.112.196:/home/ /manage2/kloudmi-migrasi/home/
 

======================================================================
 
# custom css DaftarWeb
 


```css
.content .domain-checker {
    padding: 20px 0 20px;
}


.wp24-dc .dc-form > div {
    display: flex;
    align-items: stretch;
    align-content: flex-start;
    flex-direction: column;
    justify-content: space-between;
}

[type=button], [type=submit], button {
    display: inline-block;
    font-weight: 14px;
    color: #ffffff;
    text-align: center;
    white-space: nowrap;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    background-color: #102d5e;
    border: 1px solid #102d5e;
    c36: ;
    padding: 0.5rem 1rem;
    padding-top: 10px;
    margin-top: 10px;
    font-size: 1rem;
    border-radius: 3px;
    -webkit-transition: all .3s;
    -o-transition: all .3s;
    transition: all .3s;
}
```

=================================================================================================================================
c2673693.tier1.quicns.com                       |
-------------------------------------------------
pass email hr.admin@suzuki.persada-group.com
>>>>>>>> E^B0jjoZHSTn <<<<<<<<<<<<<<<<<<<
---------------------------------------------------------------------------------------------------------------------------------

# Hosting DA di gurame kyknya blm terintregasi ke WHMCS, jadi kalau ada order, upgrade, ataupun downgrade. Harus manual lewat panel directadmin

=================================================================================================================================

# Batasi folder wp-admin ke ip tertentu, ini ditaruh setelah # END WordPress


```php
	# WP-Login
	<Files wp-login.php>
	Order Deny,Allow
	Deny from all
	Allow from 103.146.62.2		# Ganti sesuai alamat IP yang akan di allow
	Allow from 103.146.63.245	# Ganti sesuai alamat IP yang akan di allow
	Allow from 103.167.112.34	# Ganti sesuai alamat IP yang akan di allow
	Allow from 103.83.93.212	# Ganti sesuai alamat IP yang akan di allow
	</Files>
```
	
	

==== DS bappeda-esxi.pelalawankab.go.id =================================================

Menggunakan Lisence cPanel VPS

Dell iDrac 6
=========
https://103.31.235.174:4433/index.html
User : root
Password : hiji2tilu4!@#

vm-cpanel : 103.146.63.188
port ssh : 1428
passwd ; hiji2tilu4!@#

port ssh : 1428

IP Lama : 
103.31.235.176	Network
103.31.235.177	Gateway
103.31.235.178	Proxmox 
103.31.235.179	Usable 
103.31.235.180	usable 
103.31.235.181	usable 
103.31.235.182	usable 
103.31.235.183	Broadcast

spek sekarang 
* mobo =  GA-X99-UD4 
* processor = Intel(R) Xeon(R) CPU E5-2620 v3 @ 2.40GHz
* RAM = 32Gb DDR4


bayarnya maret 2020

proxmox : 103.146.63.186:8006

Untuk login ke DS bappeda-esxi.pelalawankab.go.id
* IP : 103.146.63.186
* Pass: Bodootciek13#@!
* Port: 1428

=================================================================================================================================


============================================ Catatan Web Kalsel Banyak Error ====================================================

1. kebanyakan wordpress tidak bisa dibuka karena limit pada php.ini, tapi ini sudah diatasi dengan menambah limitnya.
2. Pada domain banhub.kalselprov.go.id terdapat error 500, ini kemungkinan dikarenakan plugin atau theme WordPress yang digunakan terkonflik dengan satu sama lain atau dengan versi WordPress yang digunakan.

=================================================================================================================================

https://www.antmediahost.com/colocation-server-area31-cimanggis/





CBt_(-0.Dy~X

# cuso

Domain : minosaroyo.cusoindonesia.id 
User : minosaroyocusoin
Pass : A*i[nm^kp8_Q

=================================================================================================================================

# Kalau server pakai cPanel, mysql nya gabisa dibuat REPLICATION SLAVE


=================================================================================================================================
													UAS EKONOMI SYARIAH
													
1. 	a)	
	Kesempurnaan pasar adalah kondisi teori ekonomi di mana semua pasar memenuhi syarat-syarat kesempurnaan. 			Syarat-syarat ini termasuk:

		1. Jumlah pelaku pasar yang sangat besar sehingga tidak ada satu pelaku pasar yang dapat mempengaruhi harga pasar secara signifikan.

		2. Semua pelaku pasar memiliki informasi yang sama dan lengkap mengenai harga dan kualitas dari produk yang dijual di pasar.

		3. Ada mobilitas yang mudah bagi pelaku pasar untuk masuk dan keluar dari pasar.

		4. Tidak ada biaya transaksi yang terkait dengan berpartisipasi di pasar.

		5. Produk yang dijual di pasar homogen, yaitu semuanya sama dan tidak ada perbedaan kualitas antara satu produk dengan produk lainnya.

	Jika suatu pasar memenuhi semua syarat kesempurnaan ini, maka dianggap sebagai pasar yang sempurna. Pada pasar yang sempurna, harga akan mencerminkan nilai ekonomi dari produk tersebut, dan pelaku pasar akan membuat keputusan yang rasional dalam membeli atau menjual produk. Namun, kebanyakan pasar di dunia nyata tidak sempurna dan seringkali tidak memenuhi semua syarat kesempurnaan ini.
	
	b)
	Makro ekonomi syariah adalah cabang dari ilmu ekonomi yang mempelajari tentang perekonomian secara keseluruhan dari perspektif yang diakui oleh prinsip-prinsip dasar dari ajaran Islam. Dalam makro ekonomi syariah, pertimbangan moral dan etika dianggap sebagai faktor penting dalam pengambilan keputusan ekonomi, dan prinsip-prinsip ekonomi seperti keadilan dan kepatutan harus diikuti dalam mengelola perekonomian.
	
	c)
	Kebijakan fiskal adalah kebijakan yang diambil oleh pemerintah untuk mengelola pendapatan dan pengeluaran yang berkaitan dengan pengelolaan perekonomian. Kebijakan fiskal dapat berupa pengeluaran pemerintah atau pemotongan pajak yang dapat mempengaruhi tingkat pendapatan, pengeluaran, dan kekayaan masyarakat serta tingkat aktivitas ekonomi secara keseluruhan.
	
2. 
	Prinsip-prinsip dasar ekonomi Islam yang menjadi pondasi rancang bangun ekonomi Islam adalah sebagai berikut:

		a. Konsep maqashid al-shari'ah: Maqashid al-shari'ah adalah tujuan atau manfaat yang ingin dicapai oleh syari'at Islam. Prinsip ini menekankan pentingnya memahami tujuan dasar dari setiap hukum dan kebijakan ekonomi dalam Islam.

		b. Prinsip keadilan: Islam menekankan pentingnya keadilan dalam setiap aspek kehidupan, termasuk dalam bidang ekonomi. Keadilan diartikan sebagai pembagian yang adil dari kekayaan dan kesempatan ekonomi di antara anggota masyarakat.

		c. Prinsip kepatutan: Islam menekankan pentingnya kepatutan dalam setiap tindakan ekonomi, yaitu meminimalisir kerugian dan memaksimalkan keuntungan bagi semua pihak yang terlibat dalam transaksi.

		d. Prinsip kebersihan: Islam menekankan pentingnya kebersihan dalam setiap tindakan ekonomi, yaitu tidak melakukan transaksi yang merugikan pihak lain atau yang merugikan masyarakat secara keseluruhan.

		e. Prinsip kehati-hatian: Islam menekankan pentingnya kehati-hatian dalam setiap tindakan ekonomi, yaitu mempertimbangkan implikasi sosial dan keberlanjutan dari setiap keputusan ekonomi.

	Prinsip-prinsip ini merupakan pondasi dasar dari sistem ekonomi Islam yang berusaha mencapai kesejahteraan sosial, keadilan, dan keberlanjutan bagi semua anggota masyarakat.
	
3.
	Zakat, infak, dan shodakoh merupakan tiga konsep penting dalam Islam yang bertujuan untuk membantu meringankan beban keuangan bagi orang-orang yang membutuhkan, serta mencapai kesetaraan dan keadilan sosial. 
	
4. 
	Berikut ini adalah 5 jenis produk kebijakan fiskal yang diberlakukan pada masa Rasulullah SAW:

		1. Zakat: Zakat adalah sejenis pajak yang harus dibayarkan oleh orang-orang yang mampu kepada orang-orang yang membutuhkan. Zakat merupakan salah satu prinsip yang penting dalam makro ekonomi syariah karena dianggap sebagai cara untuk mencapai kesetaraan dan keadilan sosial.

		2. Jizyah: Jizyah adalah pajak yang dikenakan kepada orang-orang non-Muslim yang tinggal di wilayah Islam. Jizyah dianggap sebagai ganti dari kewajiban mengikuti wajib militer yang harus dipenuhi oleh orang-orang Muslim.

		3. Kharaj: Kharaj adalah pajak yang dikenakan kepada orang-orang yang memiliki tanah pertanian di wilayah Islam. Kharaj dianggap sebagai ganti dari kewajiban membela negara yang harus dipenuhi oleh orang-orang Muslim.

		4. Sadaqah: Sadaqah adalah sumbangan keuangan atau material yang diberikan kepada orang-orang yang membutuhkan dengan tujuan membantu meringankan beban keuangan mereka.

		5. Wakaf: Wakaf adalah cara untuk mengelola kekayaan dengan cara menyisihkan sebagian dari kekayaan tersebut untuk kepentingan sosial dan keagamaan. Wakaf merupakan bentuk kebijakan fiskal yang diberlakukan pada masa Rasulullah SAW karena dapat membantu meningkatkan kesejahteraan masyarakat dan mengurangi ketimpangan kekayaan.
		
		
=================================================================================================================================

g-bRY8n9:YOx65




==SEO On Page

```
heading 1 : 1
heading 2 : 2
heading 3 : 4
heading 4 : 6
```



lshw -short -class cpu
lshw -short -class memory
lshw -short -class disk
lshw -class disk -class storage
hdparm -I /dev/sdX (sda/sdb/sdc/ etc)


NAS ==> TeknikalSupport:\Dokumen Server KLHK\AQMS\Spek_Server_HP_AQMS-Tersisa-2023.xlsx

<h2>naon we lah</h2>



z)B,k1Iqq;J(

u7cJ#n7uQZ;l



buatkan saya plugin wordpress, namanya "Shortcode Maker", nama pembuatnya "Azril Hakim".
berikut fungsinya.

1. ada form pembuatan shortcode
2. setiap shortcode yang sudah dibuat akan ditampilkan dibawah form

=================================================================================================================================
1. Harga perolehan investasi saham PT. Unilever Indonesia pada April 1 adalah:
Jumlah saham: 1.000 lembar
Harga per saham: Rp. 5.000,-
Kurs: 106
Biaya komisi: 1% dari harga kurs pembelian (1.000 x Rp. 5.000 x 106 x 1%) = Rp. 5,580,-
Harga perolehan investasi saham = (1.000 x Rp. 5.000 x 106) + Rp. 5,580 = Rp. 5,580,580,-

2. Harga perolehan investasi saham PT. Telkom Indonesia pada Mei 1 adalah:
Jumlah saham: 300 lembar
Harga per saham: Rp. 5.000,-
Kurs: 108
Biaya komisi: 1% dari harga kurs pembelian (300 x Rp. 5.000 x 108 x 1%) = Rp. 1,644,-
Harga perolehan investasi saham = (300 x Rp. 5.000 x 108) + Rp. 1,644 = Rp. 1,644,644,-
Harga perolehan investasi obligasi RI pada Mei 1 adalah:
Jumlah obligasi: 40 lembar
Harga per obligasi: Rp. 30.000,-
Kurs: 102
Biaya komisi: Rp. 20.000,-
Harga perolehan investasi obligasi = (40 x Rp. 30.000 x 102) + Rp. 20.000 = Rp. 1,248,000 + Rp. 20,000 = Rp. 1,268,000

Itu adalah harga perolehan investasi saham dan pinjaman obligasi yang dimiliki oleh PT. Yudha Pratama. Harap diingat bahwa biaya bunga (kupon) tidak diperhitungkan dalam harga perolehan ini karena hanya diakui pada saat bunga diterima.



Jumlah obligasi: 100 lembar
- Harga per obligasi: Rp. 20.000,-
- Kurs: 104
- Biaya provisi dan materai: Rp. 10.400,-
- Harga perolehan obligasi = (100 x Rp. 20.000 x 104) + Rp. 10.400 = Rp. 2,048,400

Setelah itu, mari hitung bunga yang berjalan. Bunga dibayar setiap tanggal 1 Maret dan 1 September. Jadi, pada tanggal 25 Juni 2022, bunga yang berjalan adalah selama 3 bulan (Juni, Juli dan Agustus).

- Bunga per tahun = 9% dari nominal
- Bunga per tahun = 9/100 x Rp. 20.000 x 100 = Rp. 18,000
- Bunga per 3 bulan = Rp. 18,000 / 4 = Rp. 4,500

Jurnalnya adalah :
- Debit: Investasi obligasi (Rp. 2,048,400)
- Kredit: Kas (Rp. 2,048,400)

- Debit: Bunga berjalan (Rp. 4,500)
- Kredit: Pendapatan bunga (Rp. 4,500)

دولار واحد وسبعة وثمانون سنتا. كان هذا كل شيء. وستون سنتات منه كان في البنسات. البنسات أنقذت واحدة واثنين في وقت واحد من قبل تجريف البقال ورجل الخضار والجزار حتى يحترق خد المرء مع الافتراض الصامت للبخل أن مثل هذا التعامل الوثيق ينطوي على. ثلاث مرات ديلا عدها. دولار واحد وسبعة وثمانون سنتا. وفي اليوم التالي سيكون عيد الميلاد.


=================================================================================================================================

1. my interests are technology, accounting, urban farming, and electrical tranportation. My passion is technology
2. as a sysadmin, my skills and expertise are on digital world, like Linux, cPanel, cyber security, etc. Also i have skills on web and app development, little bit of accounting, coffe, and bartendering
3. i don't know yet
4. i will be rich

=================================================================================================================================
 Pass idrac persada : MXPEY949AEX9
 
kalau server baru ganti ip, terkadang perlu konfigurasi ulang di /etc/mailips

=================================================================================================================================

.D!BOR$H7tI[
K]OypFZ+%5At

Berikut detail nya:

sales.spv@kedamaian.persada-group.com
New pass : nXvK&PDP+EN[

staff.lab@kedamaian.persada-group.com
Gg~If87H!mS8

staff.pak@kedamaian.persada-group.com
ZbbjNX?pK0HY



hasriyan.rahmat@kedamaian.persada-group.com
=+&$Ikhu#kW+

staff.fin@kedamaian.persada-group.com
7FPh,3W=E}JS

alqorin.shohih@kedamaian.persada-group.com
?{N$!v}__?&[

legal.ga@persada-group.com
9H#44NJy!@uI

eko@psda.my.id
f6GOaZRdwXXY

febriansyah.febriansyah@kedamaian.persada-group.com
6-];0@{~3BpY

support.mkt@kedamaian.persada-group.com
0yZrsTiJPLO3

imelda.arianti@suzuki.persada-group.com
o-AO~PiWF0w=

diana.diana@suzuki.persada-group.com
5-m~%4ItIV^E

suraji.suraji@hino.persada-group.com
tAYl7A*)dAC%

fad.plr@suzuki.persada-group.com
c^.kL4YcpZvW

zohra.putri@hino.persada-group.com
6{}+Dc-VWZvY

okvita.indah@hino.persada-group.com
qN79$.6Lv6FQ


When using the 'Manage Suspension' interface for an email account, what does selecting 'Hold' for the Send option do?

a. Holds all of that account's outbound emails in the queue for a default period of 30 minutes before sending, to avoid spam filters.
b. Holds all of that account's outbound emails into a separate 'Sent' folder for archival purposes.
c. Holds all of that account's outbound emails in the queue until Send has been changed back to the 'Allow' setting.
d. Holds all of that account's outbound emails in the queue in the 'Frozen' state until manually unfrozen via the command-line.

Match the following SSL Certificate types with their validation methods.

Extended Validation   
   	Validates that the domain is registered and accessible over the internet by DNS or HTTP
Organized Validation   
   	The organization is validated by a 3rd party organization
Domain Validation   
   	The Certificate Authority has proof the organization exists and does business outside of the internet.
	
	
acc3dd@!avpsA



==CASE HOST ACCESS CONTROL NOT WORK==
Case terjadi di server cPanel yang menggunakan imunify360 (sejauh ini). Server kloudmi dan Lele contohnya.
Sejauh yang diketahui kendala terjadi karena ketika imunify360 diaktifkan, ada beberapa tambahan rule yang ditambahkan ke nftables config. Rule Host Access Control kemungkinannya tertimpah rule Imunify360.
Kondisi default nftables config (lokasi : /etc/sysconfig/nftables.conf), rule Host Access Control ada di posisi awal konfigurasi, seperti berikut :
[root@server1 ~]# more /etc/sysconfig/nftables.conf
table inet filter {
        chain INPUT {
                type filter hook input priority filter; policy accept;
                counter packets 83876144 bytes 9620571799 jump cPanel-HostAccessControl
                counter packets 83875827 bytes 9620555447 jump cP-Firewall-1-INPUT
        }

        chain FORWARD {
                type filter hook forward priority filter; policy accept;
                counter packets 0 bytes 0 jump cPanel-HostAccessControl
                counter packets 0 bytes 0 jump cP-Firewall-1-INPUT
        }

        chain OUTPUT {
                type filter hook output priority filter; policy accept;
        }

        chain cPanel-HostAccessControl {
                ip saddr 103.146.63.245 ct state new tcp dport 2083 counter packets 9 bytes 468 accept
        }
Jika kita install imunify360 maka rule diatas hilang. Namun ketika kita input rule Host Access Control di WHM maka akan buat baru dibagian bawah tapi hanya bagian "chain cPanel-HostAccessControl" saja. Seperti ini :
table inet filter {
        chain cPanel-HostAccessControl {
                ip saddr 103.146.63.245 ct state new tcp dport 3759 counter packets 0 bytes 0 accept
                ip saddr 103.167.112.34 ct state new tcp dport 3759 counter packets 0 bytes 0 accept
                ip saddr 103.146.62.10 ct state new tcp dport 3759 counter packets 0 bytes 0 accept
                ip saddr 158.140.162.94 ct state new tcp dport 3759 counter packets 0 bytes 0 accept
                ip saddr 103.146.62.14 ct state new tcp dport 3759 counter packets 0 bytes 0 accept
                ct state new tcp dport 3759 counter packets 0 bytes 0 reject
        }
}
Maka merujuk konfigurasi ketika tanpa menggunakan Imunify360, kita perlu add bagian chain INPUT, chain FORWARD dan chain OUTPUT untuk Host Access Controlnya di bagian table inet filter sebelum sub bagian chain cPanel-HostAccessControl. Berikut yang perlu ditambahkan :
 chain INPUT {
                type filter hook input priority filter; policy accept;
                counter packets 83420064 bytes 9799462107 jump cPanel-HostAccessControl
        }

        chain FORWARD {
                type filter hook forward priority filter; policy accept;
                counter packets 0 bytes 0 jump cPanel-HostAccessControl
        }

        chain OUTPUT {
                type filter hook output priority filter; policy accept;
        }
Restart service nftables : service nftables restart

=================================================================================================================================

Template newsletter QUIC.cloud

QUIC.cloud kami mengoptimalkan konten WordPress Anda untuk akses website lebih cepat, di mana pun pengunjung Anda tinggal. QUIC.cloud dapat meningkatkan pengalaman pengguna, data vital web inti, skor kecepatan halaman, dan peringkat mesin pencari. Dengan beberapa fitur premium & handal berikut :

Content Delivery Network

QUIC.cloud CDN adalah jaringan pengiriman konten yang mampu melayani puluhan ribu permintaan secara bersamaan, melalui jaringan node yang didistribusikan secara strategis di seluruh dunia. QUIC.cloud menghadirkan dukungan HTTP/3 mutakhir dan fitur keamanan WordPress yang penting. Dan, tidak seperti CDN lainnya, QUIC.cloud bermitra dengan LiteSpeed Cache untuk menyajikan konten WordPress statis dan dinamis.

Jaringan pengiriman konten global QUIC.cloud yang sangat skalabel, kaya fitur, terintegrasi dengan plugin Litespeed Cache maka berpengaruh besar kepada jangkauan pengunjung Anda dengan cepat, di mana pun mereka tinggal.

Security Prioritize

QUIC.cloud melindungi situs Anda di tingkat CDN, jadi tidak perlu khawatir dengan tingkat keamanan website Anda karena terdapat fitur :
- Mengurangi serangan brute-force berskala besar yang umum terjadi pada website yang menggunkan WordPress.
- Dalam kondisi aktivitas website abnormal, reCAPTCHA tingkat CDN muncul untuk memproteksi pengunjung yang mencoba melakukan serangan atau mencoba menyusup kedalam sistem wordpress Anda.
- Memberikan perlindungan DDoS Layer-7 tingkat lanjut.

DNS Service

Layanan DNS bawaan QUIC.cloud yang 100% GRATIS memungkinkan Anda untuk secara opsional menyederhanakan dan mengoptimalkan website dengan konfigurasi DNS yang mudah dalam pengelolaannya pada QUIC.cloud.

Optimasi Image

Seperti diketahui, gambar merupakan salah satu komponen penting dalam sebuah website dan untuk mengoptimalkan gambar yang Anda unggah ke dalam website yang secara otomatis menyesuaikan ukuran gambar kedalam format WebP tanpa mengurangi kualitas gambar yang sudah diunggah.

Optimasi Page

Fungsi dari fitur ini untuk menyimpan halaman website, kemudian akan mengirimkan halaman website yang telah tercache ke pengunjung. Sehingga tidak perlu mengekseskusi seluruh data dan database di website.







CORPORATE 10GB Rp105.000/Bulan
CORPORATE 20GB Rp140.000/Bulan
CORPORATE 30GB Rp189.000/Bulan
CORPORATE 50GB Rp245.000/Bulan


zohra.putri@hino.persada-group.com
!AmzD@.bhuD3

okvita.indah@hino.persada-group.com
?aH1&X~I*dA?

transfer turacon.com
corporate 20GB
di akun M Sadeli

http://stlouis-admin.cusoindoneis.id/
stlouisadmincuso
w?+9={}M5LI}

http://stlouis-vote.cusoindoneis.id/
stlouisvotecusoi
*e&H7m}%uQXD



tokopedia.plr@hino.persada-group.com
EX7ZQ^RVK&I1

fad.plr@hino.persada-group.com
oNZ-w5IrQga;


matacash.co.id & donasi-matajari.com
RAM : 8GB
Drive : 2 x 1TB SATA

+kY((Hd%mDv$


riza.aprianti@suzuki.persada-group.com
Pass: ,rNJ,7{#~nW1

admin.training2@suzuki.persada-group.com
Pass: _6l14o-ffM7%


server axiadata :
korelasipersada 22B
euri 21 B (tidak keluar)
sister-sei 20B


+++++++++++++++++++++++++++++++++++++++++++++ WP Server Connect ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++ 
1. 	Buat direktori wp-server-connect di dalam direktori wp-content/plugins pada instalasi WordPress kamu.

2.	Buat file wp-server-connect.php di dalam direktori wp-server-connect dan isi dengan informasi plugin seperti judul, 	deskripsi, versi, penulis, dan lainnya.

3.	Buat direktori assets/css dan assets/js di dalam direktori wp-server-connect.

4.	Buat file wp-server-connect.css dan wp-server-connect.js di dalam direktori assets/css dan assets/js.

5.	Buat direktori assets/img di dalam direktori wp-server-connect.

6.	Simpan gambar server-connect-icon.png, ssh-icon.png, dan rdp-icon.png di dalam direktori assets/img.

7.	Buat direktori includes di dalam direktori wp-server-connect.

8.	Buat file class-wp-server-connect.php di dalam direktori includes dan isi dengan kode untuk mengaktifkan plugin dan menambahkan fungsi.

9.	Buat direktori db di dalam direktori includes.

10.	Buat file wp-server-connect-db.php, class-wp-server-connect-db.php, dan wp-server-connect-db-install.php di dalam direktori db.

11.	Buat direktori templates di dalam direktori includes.

12.	Buat file remote-connection-plugin-page.php, remote-connection-admin-page.php, connection-table.php, connection-list.php, dan connection-form.php di dalam direktori templates.

13. Isi file-file yang telah dibuat dengan kode yang diperlukan.



public_html/wp-content/yDSX3Ge7hJr.php


postgre cupang

- eproccom_iksasuser : eproccom	
- eproccom_ueproc19 :eproccom
- renegade_tes : renegade
- renegade_henry : renegade
- aminnoki_odontou : aminnoki


	
103.146.63.78


aku punya 2 perusahaan, yang 1 namanya DaftarWeb websitenya daftarweb.net, ini buat jasa web development. Yang 1 lagi namanya PunyaHosting websitenya punyahosting.com, ini buat jualan hosting, domain, vps, dll. Nah aku mau buat kedua perusahaan itu collab di satu promosi namanya "Promo UMKM Digital". Ini target pasarnya UMKM kebanyakan dari mereka itu berumur 30-60 tahun dan sering aktif di WhatsApp dan Facebook, nah aku mau promosiin lewat media itu (WhatsApp & Facebook). yang jadi permasalahan disini itu aku mau buat post di WhatsApp & Facebook tapi bingung sama kata-katanya biar menarik di target pasar aku. coba buatkan itu



"Promo UMKM Digital - Solusi Digital Terbaik untuk Bisnis Anda!
DaftarWeb dan PunyaHosting sedang menghadirkan kesempatan terbaik bagi Pegiat UMKM untuk membangun kehadiran online bisnis Anda dengan solusi digital terbaik. Dapatkan jasa web development profesional dan fitur-fitur terbaik yang mencakup:

- Free Domain .com
- 1GB Hosting
- 5 Pages
- Tombol order ke WhatsApp
- 1 Email Account
- 2x Revisi

Semua fitur tersebut bisa Anda dapatkan dengan harga hanya Rp 600.000 saja. Segera bergabung dengan kami dan nikmati solusi digital terbaik untuk bisnis Anda, serta bangun kehadiran online yang optimal dengan fitur-fitur hebat yang kami tawarkan. Namun perlu diingat, promo ini hanya berlaku untuk 20 UMKM pertama yang mendaftar. Jadi, jangan lewatkan kesempatan Anda dan daftarkan bisnis Anda sekarang juga!"

untuk lebih lengkapnya bisa dilihat disini



at5SgAgO.Cq2E)G_





