# install-mysql-workbench
cara install mysql workbench di linux fedora 27

1. download file mysql workbench
   mysql-workbench-community-8.0.13-1.fc27.x86_64.rpm
2. download terlebih dahulu file repository dari mysql community
   - bisa lewat url https://repo.mysql.com/yum/ atau
   - https://repo.mysql.com/yum/mysql-8.0-community/fc/27/x86_64/mysql80-community-release-fc27-1.noarch.rpm
3. instal dengan perintah sebagai berikut
   rpm -Uvh mysql80-community-release-fc27-1.noarch.rpm
4. install mysql workbench
   rpm -ivh mysql-workbench-community-8.0.13-1.fc27.x86_64.rpm
   
jika terjadi error seperti dibawah ini :
warning: mysql-workbench-community-8.0.13-1.fc27.x86_64.rpm: Header V3 DSA/SHA1 Signature, key ID 5072e1f5: NOKEY
error: Failed dependencies:
     libpcrecpp.so.0()(64bit) is needed by mysql-workbench-community-8.0.13-1.fc27.x86_64
     
install terlebih dahulu dependencies yang kurang dengan cara :
sudo dnf install pcre-cpp libzip proj python-paramiko python2-crypto

setelah itu jalankan kembali perintah di poin 4.
5. install mysql community server
   sudo dnf install mysql-community-server   
6. mengaktifkan repolist
   repolist enabled | grep mysql
   
menjalankan mysql : sudo service mysqld start
cek status dari mysql : sudo service mysqld status

login mysql dan ganti password root lewat terminal :
1. sudo grep 'temporary password' /var/log/mysqld.log
2. login dengan password temporar yang sudah tersedia
3. mysql -uroot -p
4. mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'isidenganpasswor';
