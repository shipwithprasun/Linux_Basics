# Linux_Basics

pwd
whoami
date -> date/date + %D/%T/%H:%M:S
ls /ls -a/l/t/r/h
clear
cat filename
less filename
more filename
touch filename
rm filename
vi filename
nano filename
mkdir dir_name
rmdir dir_name
rm -rf dir_name
cp file dest/path/
mv file dest/path/
mv file file_renamed
head -5 filename
tail -5 filename
sort filename
sort -r filename
sort filename | uniq
grep "word" filename
egrep "word1|word2" filename
shuf filename
wc -l filename
cmp fileA fileB
diff -u fileA fileB
find /path/ -name filename

updatedb
locate filename

history
man command
command --help
which command
bc
cal / cal year/ cal month year
uptime
script -> ctrl+D
alias long_command="small_shortcut"
alias -p

<!-- Compressing/Decompress files -->
gzip filename
gzip -k filename
gzip -d filename
gunzip filename

<!-- Compressing/Decompress Folders -->
tar -czf filename.tar.gz myfile/
tar -xzf filename.tar.gz

<!-- Compressing/Decompress multiple files -->
zip myfiles.zip fileA fileB fileC
unzip myfiles.zip
unzip -l myfiles.zip
9e06e23c29b0
<!-- Download file from internet -->
wget URL_of_file
wget -O opt_file.txt URL_of_file

<!-- Call APIs on Linux -->
curl https://meowfacts.herokuapp.com/

apt or yum/dnf

rpm -qa|grep java / dnf list installed

apt search package_name
yum/dnf list available

systemctl status firewalld.service
systemctl list-units --type=service --all

printenv
