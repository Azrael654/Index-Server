1. rm -rf buat hapus directori dan seluruh isinya
2. lokasi selinux /etc/selinux/config
3. cat > nama_file : ini berarti akan membuat file baru, 
   kalian bisa mengubah "nama_file" dengan nama sesuai yang anda inginkan
4. cat nama_file : ini berfungsi untuk melihat isi sebuah file melalui terminal linux.
5. perintah rename bisa pakai mv   

37.17879.22

rm -f buat hapus file
rm -rf hapus folder

#screen 
	Instalasi : yum install screen -y
	ctrl+a+c : membuat sebuah sesi screen baru, sehingga anda dapat menggunakan beberapa sesi screen.
	ctrl+a+n : beralih ke sesi screen selanjutnya (tentunya jika anda membuat beberapa sesi)
	ctrl+a+p : beralih ke sesi screen sebelumnya
	ctrl+a+d : melepaskan sebuah sesi screen (tanpa menghentikan proses yang berjalan di dalam screen)
	exit : untuk mengakhiri sebuah sesi screen
	screen -R namascreen : membuat sesi baru dengan menggunakan nama
	screen -r namascreen : untuk memilih screen
	screen -ls : Lihat daftar screen 
	
# tmux
	instalasi : yum install tmux -y
	

-systemctl punya 6 opsi: start, stop, satus, restart, enable, disable

#perintah 'sed' 
	Sed ini kepanjangannya Stream Editor. Dan sesuai namanya, sed berfungsi 
	memanipulasi input yang berupa stream; bisa dari input langsung ataupun membaca dari file.

-untuk monitoring kinerja server gunakan command "to"


------------------------------------------------------------------------------------------------------------------
Mengamankan akses root ssh																						
Jangan lupa, untuk limit root akses ssh ketika setup server baru di /etc/ssh/sshd_config						
======	
# global config
Port 3759
UseDNS no
PermitRootLogin no
UsePAM yes
PasswordAuthentication yes
# permit ssh login for user
Match Address 103.146.62.0/24,103.146.63.0/24,103.167.112.0/24,103.167.113.0/24,158.140.162.94,202.157.177.139
    PermitRootLogin yes

======
- untuk cek ip terblokir atau tidak
	grep IP_ADDRESS /etc/csf/csf.deny
	
- untuk lihat list & kapasitas partisi
	df -h (df = "disk-filesystem) (h = "human-readable)
	
---------------------------------------------------------------------------------------------------------------------	

#chmod (Change Mode)

	untuk penggunaan chmod ada dua cara untuk mendifenisikan permission/hak akses, dengan simbol (karakter alfanumerik), atau bisa juga dengan bilangan oktal (0 sampai 7)

	Pada dasarnya, setiap file dapat diakses oleh 3 jenis pengguna yaitu:

	Owner untuk user atau pengguna
	Group untuk group atau kelompok
	Other untuk other atau orang lain (bisa public)
	Sedangkan untuk tipe aksesnya adalah:

	Read : diizinkan untuk membaca isi file
	Write: diizinkan untuk menulis ke file
	Execute: diizinkan untuk mengeksekusi file sebagai program / script
	
	Nilai Numerik
	-Read : 4
	-Write: 2
	-Execute: 1
	
	Simbol

	-Read : r
	-Write: w
	-Execute: e
	
#chown
	Perintah ini digunakan untuk mengganti owners/pemilik dari file/direktori. 
	chown {user}:{group} file/direktori

#ps
	ps adalah perintah yang digunakan jika kita perlu mengecek proses yang berjalan pada server. 
	Contoh perintah ps dasar adalah ps -aux, karena semua proses yang berjalan akan tampil.Bila kita hanya ingin melihat suatu proses (misalnya apache), 
	maka gunakan perintah ps -aux | grep apache.
	
	
##########################|SIAPA TAU BUTUH|#############################################
<><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><><>

https://docplayer.info/46343283-Perintah-dasar-linux-untuk-pengelola-server.html
https://www.digitalocean.com/community/tutorials/grep-command-in-linux-unix

########################################################################################


# command grep
	command ini digunakan untuk mencari kata dalam file
	(grep "cari kata" namafile)
	
# restore database mysql
	mysql -u username -p katasandi nama-database < nama-backup.sql
	
# hitung jumlah baris, kata dan huruf pada file
	wc namafile
	
# firewalld
	firewall-cmd --permanent --zone=public --add-port=NO_PORT/tcp <---Allow Port--->
	firewall-cmd --permanent --zone=public --add-source=IP_ADDRESS <---Allow IP--->
	firewall-cmd --permanent --remove-source=IP_ADDRESS <---Remove IP--->
	firewall-cmd --permanent --add-service=ADD_A_SERVICE <---Add a Service--->
	firewall-cmd --permanent --remove-service=ADD_A_SERVICE <---Remove a Service--->
	firewall-cmd --reload <---Reload Firewall--->
	
	
# Install & Konfig SNMPD Internal/Manage====

	yum install net-snmp net-snmp-utils -y
	# Ubah default config snmpd
	mv /etc/snmp/snmpd.conf /etc/snmp/snmpd.confasli
	vi /etc/snmp/snmpd.conf

	----isi snmpd.conf default antmedia----
	com2sec semut localhost  semut
	com2sec semut 202.157.177.139 semut
	com2sec semut 103.167.112.42 semut
	com2sec semut 158.140.162.94 semut

	group MyROGroup v1         semut
	view all    included  .1                               80

	access MyROGroup ""      any       noauth    exact  all    none   none

	syslocation Gedung Cyber - Jakarta
	syscontact sa@semutdata.co.id


	exec cpuload /viewload
	exec eximqueue /bin/cat /var/log/exim_mainlog.queue
	dontLogTCPWrappersConnects yes
	agentaddress udp:0.0.0.0:13371  #Khusus Ubuntu buat change Port 13371
	------END isi snmpd.conf default antmedia-----

	* change port snmpd ke 13371 #OS Keluarga Redhat
	echo OPTIONS=\"-LS0-5d -Lf /dev/null -p /var/run/snmpd.pid -x TCP:13371 UDP:13371\" >> /etc/sysconfig/snmpd

	* Buat file /viewload
	vi /viewload
	---------isi /viewload ---------------
	#!/bin/sh

	lload=`/bin/cat /proc/loadavg | cut -d \. -f 1`

	if [ ${lload} -gt "15" ];
		then
			echo high
			else
					echo normal
	fi
	---------end isi /viewload------------

	chmod +x /viewload

	* Buat crontab untuk grep mailqueue ke MRTG
	crontab -e
	*/1 * * * * /usr/sbin/exim -bpc > /var/log/exim_mainlog.queue
	*/1 * * * * /usr/bin/mailq | grep -c "^[A-F0-9]" > /var/log/exim_mainlog.queue

	* allow IP internal 
	csf -a 202.157.177.139
	csf -a 103.167.112.42
	csf -a 158.140.162.94
	csf -a 103.167.112.34

	* Jangan lupa ENABLE snmpd service dan restart
	systemctl enable snmpd
	systemctl restart snmpd

	==== END Install & Konfig SNMPD Internal/Manage ====
	
	
	
# allow port di iptable
	iptables -I INPUT -p tcp --dport NOMOR_PORT --syn -j ACCEPT
	iptables-save
	
# cek os
	- hostnamectl
	- cat /etc/os-relese
	
	
# Update kernel Linux

	dnf update -y

	rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org

	dnf install https://www.elrepo.org/elrepo-release-8.el8.elrepo.noarch.rpm -y

	dnf list available --disablerepo='*' --enablerepo=elrepo-kernel

	dnf --enablerepo=elrepo-kernel install kernel-ml -y

	dnf --enablerepo=elrepo-kernel install kernel-lt -y
	
# chattr Membuat File di Linux Tidak Dapat Dirubah dan Dihapus
	chattr +i {file/direktori} membuat file/directory terkunci
	chattr -i {file/direktori} membuka kunci file/directory 
	
# akses ssh kudu allow IP heula berarti aya strict terhadap akses service/port ssh.
	1. Pake Host Access Control (Ieu strict port/service apapun) rulena ALLOW dlu baru DENY. 
	2. /etc/ssh/sshd.config . Strict khusus service sshd
	masing2 server beda penerapan. terutama server klien + cpanel eta di host access control


-------------------------------------------------------------------------|
Cpanel kl msh trial mau update ke berbayar mst di update license nya     |
 pake CLI.																 |
/usr/local/cpanel/cpkeyclt												 |
-------------------------------------------------------------------------|

# which
	Perintah "which" berguna untuk mencari lokasi file binary suatu program atau perintah, terutama jika Anda ingin mengecek apakah suatu program sudah terinstall atau belum, atau jika Anda ingin mengecek apakah ada lebih dari satu versi dari suatu program yang terinstall pada sistem

=================================================================================================================================
	
# Untuk mengecek spesifikasi server melalui SSH, dapat menggunakan perintah berikut:

	-lscpu: Perintah ini akan menampilkan informasi tentang arsitektur CPU, seperti jumlah core, kecepatan clock, dan lain-lain.
	
	-lshw: Perintah ini akan menampilkan informasi tentang hardware yang terpasang pada server, seperti motherboard, CPU, RAM, hard drive, dan lain-lain.
	
	-dmidecode: Perintah ini akan menampilkan informasi tentang hardware yang terpasang pada server, termasuk informasi tentang BIOS dan motherboard.
	
	-hdparm -I /dev/sda: Perintah ini akan menampilkan informasi tentang hard drive yang terpasang pada server, seperti tipe,   kecepatan, dan lain-lain. Ganti /dev/sda dengan device name hard drive yang ingin Anda cek.
	
=================================================================================================================================

# Lihat pass root mysql
	cat /root/.my.cnf