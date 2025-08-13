* Setelah install OS jangan LUPA 
- Disable Selinux -> Restart
- Update OS 
- Khusus Almalinux jangan lupa install epel sebelum update 
yum install epel-release -y

=============ALMALINUX CPANEL=================
* Konfigurasi custom DB Server
mkdir /root/cpanel_profile
touch /root/cpanel_profile/cpanel.config
# isikan :  mysql-version=10.5

* Install rsyslog
dnf install rsyslog -y
systemctl start rsyslog.service
systemctl enable rsyslog.service
# verifikasi syslog sudah berjalan dengan baik : 
tail /var/log/messages
===============================================

============== Install Screen =================
yum install screen -y
* ctrl+a+c : membuat sebuah sesi screen baru, sehingga anda dapat menggunakan beberapa sesi screen.
* ctrl+a+n : beralih ke sesi screen selanjutnya (tentunya jika anda membuat beberapa sesi)
* ctrl+a+p : beralih ke sesi screen sebelumnya
* ctrl+a+d : melepaskan sebuah sesi screen (tanpa menghentikan proses yang berjalan di dalam screen)
* exit : untuk mengakhiri sebuah sesi screen
* screen -r namascreen : untuk memilih screen	
* screen -R namascreen : untuk membuat screen dan diberi nama
============= END Install Screen ==============

============== Install cPanel =================
* JANGAN LUPA Screen
screen -R instcpanel

* disable Networkmanager
systemctl stop NetworkManager.service
systemctl disable NetworkManager.service
* installasi :
cd /home && curl -o latest -L https://securedownloads.cpanel.net/latest && sh latest
============== Install cPanel =================

=========== Install CSF dan CMQ ===============
cd /usr/local/src
wget https://download.configserver.com/cmq.tgz
tar -xzf cmq.tgz
cd cmq
sh install.sh

cd /usr/local/src
wget https://download.configserver.com/csf.tgz
tar -xzf csf.tgz
cd csf
sh install.sh
=========== END Install CSF dan CMQ ===========

==== Install & Konfig SNMPD Internal/Manage====
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

syslocation Technovillage - Bogor
syscontact sa@semutdata.co.id


exec cpuload /viewload
exec eximqueue /bin/cat /var/log/exim_mainlog.queue
dontLogTCPWrappersConnects yes
agentaddress udp:0.0.0.0:13371  #Khusus Ubuntu buat change Port 13371
------END isi snmpd.conf default antmedia-----

* change port snmpd ke 13371
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

==== END Install & Konfig SNMPD Internal/Manage====

============== Install RK HUnter ==================
yum install epel-release -y
yum install rkhunter -y

* Test pengecekan
rkhunter -c    /    rkhunter -c -sk

* cek hasil pengecekan
cat /var/log/rkhunter/rkhunter.log | grep -i warning

* Buat crontab weekly scan
vi /etc/cron.weekly/rkhunter.sh

----------- ISI rkhunter.sh -----------
#!/bin/bash
(/usr/local/bin/rkhunter -c -cronjob 2>&1 \ mail -s “Weekly Rkhunter Scan Report” sa@semutdata.co.id)
chmod +x /etc/cron.weekly/rkhunter.sh
-------- END ISI rkhunter.sh ----------
============= END Install RK HUnter ===============

============== Install SmartMonTool ===============
yum -y install smart*
* edit konfigurasi = 
  vi /etc/smartmontools/smartd.conf
* comment = DEVICESCAN -H -m root
* tambahkan = DEVICESCAN -H -m sa@semutdata.co.id

* Jangan lupa ENABLE smartd service dan restart
systemctl enable smartd
systemctl restart smartd
systemctl status smartd
============ END Install SmartMonTool =============

=========== Install Imunify AV Free ===============
* Buka menu Security Advisor, tunggu hingga muncul info install Imunify AV.
* setelah aktif enable menu di cpanelnya dengan menjalankan command di ssh:
/usr/share/av-userside-plugin.sh
=========END Install Imunify AV Free ==============

wget https://tools.serverkita.web.id/space-alert.sh

=========== Tambahan Maldet =========================
cd /usr/local/src/
wget  http://www.rfxn.com/downloads/maldetect-current.tar.gz
tar -xzf maldetect-current.tar.gz
cd maldetect-*
sh ./install.sh


============ Installasi SSL Hostname ===============
/usr/local/cpanel/bin/checkallsslcerts



konfig :
vi /usr/local/maldetect/conf.maldet

Untuk memperbaharui Maldet:

maldet -u or maldet –d

Untuk scan semua file dan memberikan Anda outputnya:

maldet -a /home/*/