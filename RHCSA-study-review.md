Summary: RHCSA study review
Description: I have created a comprehensive RHCSA course curriculum that aims to provide a comprehensive understanding of the Red Hat Certified System Administrator (RHCSA) certification exam objectives. This course is designed to equip learners with the skills and knowledge required to successfully pass the RHCSA exam and excel in real-world Linux administration scenarios. Ultimately, the RHCSA course curriculum is a comprehensive resource for anyone aspiring to become a certified Red Hat System Administrator. Whether you're new to Linux or seeking to enhance your existing skills, this curriculum offers a structured path to mastering the necessary competencies for RHCSA certification and Linux system administration proficiency.








Access a shell prompt and issue commands with correct syntax
----
Use input-output redirection (>, >>, |, 2>, etc.)
> Nadpisanie
ls -al > listings
cat music.mp3 > /dev/audio
< Wysłanie do komendy
Mail -s "Subject" to-address < Filename
>> Dodanie do pliku
ls -al >> listings
<< Dodanie do komendy albo pliku
2>&1 Przekierowanie erroru na wyjście
ls Documents ABC> dirlist 2>&1
2> Przekierowanie erroru
myprogram 2>errorsfile
find . -name 'my*' 2>error.log
stdin = 0 stdout = 1 stderr = 2
Use grep and regular expressions to analyze text
Wyrażenia regularne Linuksa to znaki specjalne, które pomagają wyszukiwać dane i dopasowywać złożone wzorce. Nie ma róznicy między egrep, a grep -e.
grep 'vivek' /etc/passwd
grep -i -w 'vivek' /etc/passwd ( -i duże/małe, -w dokładny pattern)
grep -E -i -w 'vivek|raj' /etc/passwd (vivek albo raj jako pattern)
grep a^ - słowa zaczynające się na 'a'
grep t$ - słowa kończące się na 't'
egrep -i '^(linux|unix)' filename
grep 'purchase' demo.txt
grep 'purchase..db' demo.txt
grep '[A-Za-z]' filename
grep '[vV][iI][Vv][Ee][kK]' filename
grep '[:upper:]' filename (tylko z dużej litery - odnośnik do klasy
Access remote systems using SSH
ssh username@remote server
sudo apt-get install openssh-server
sudo service ssh status
Log in and switch users in multiuser targets
systemctl get-default
# systemctl set-default multi-user.target
# systemctl set-default multi-user
# systemctl set-default runlevel3.target
# systemctl set-default runlevel3
systemctl isolate multi-user (zmienia czasowo runlevel)
su -
whoami
su linuxconfig = su - linuxconfig
runlevel0.target or poweroff.target	shutdown
runlevel1.target or rescue.target	troubleshooting
runlevel2.target or multi-user.target	niezdefiniowany, taki jak 3
runlevel3.target or multi-user.target	multi-user non graphical
runlevel4.target or multi-user.target	definiowany przez użytk., taki jak 3
runlevel5.target or graphical.target	multi-user GUI
runlevel6.target or reboot.target	reboot

Przy ekranie startowym wyboru kernela nacisnąć 'e' dla edytowania>
Wpisać rd.break w linii zaczynającej się na 'kernel=' , skasować rhgb quiet i ctrl+x >
Wpisać 'mount -o remount,rw /sysroot/', żeby nadać read write>
Wpisać 'chroot /sysroot/' i wpisać 'passwd' dla zmiany hasła>
Stworzyć 'touch /.autorelabel' > exit > logout


Archive, compress, unpack, and uncompress files using tar, star, gzip, and bzip2
Compress gzip file > uncompress gunzip file.gz
Compress bzip2 file > uncompress bunzip file.bz2
tar cvzf directory.tgz directory (gzip)
tar cvjf directory.tgz directory (bzip2)
yum install -y star
star -xattr -H=exustar -c -f=directory.star directory (pakowanie)
star -x -f=directory.star 	(rozpakowanie)
Create and edit text files
cat > cattestfile.txt
touch touchfile.txt
touch file1.txt file2.txt file3.txt file4.txt
vim file1.txt
Create, delete, copy, and move files and directories
touch, cat > , > - tworzy plik / rm - usuwa
mkdir folder / rmdir folder
cp skad dokad
mv skad dokad
Create hard and soft links
ln source link- ln /path/to/source /path/to/link		HARD
ln -s source link						SYMBOLIC
List, set, and change standard ugo/rwx permissions
read - 4, write - 2, execute 1
user - group - others
chmod 777 plik - wszyscy mogą wszystko

Setuid to ustawienie uprawnień do plików w systemie Linux, które umożliwia użytkownikowi uruchomienie tego pliku lub programu za zgodą właściciela tego pliku. Służy to przede wszystkim do podniesienia uprawnień bieżącego użytkownika. Jeśli plik ma „setuid” i należy do użytkownika „root”, to użytkownik, który ma możliwość uruchomienia tego programu, zrobi to jako root zamiast siebie.
chmod u+s myfile
chmod 4755 myfile
-rwSrw-r-- 1 test test 0 Mar 2 17:59 myfile
Duże S jest wtedy gdy setuid jest nalożony, ale właściciel pliku nie ma uprawnień do wykonywania go.
chmod u+x<filename>
-rwsrw-r-- 1 test test 0 Mar 2 17:59 myfile
Setgid używany w plikach jest bardzo podobny do setuid. Po wykonaniu proces będzie działał jako grupa będąca właścicielem pliku.
chmod g+s myfile2
chmod 2755 myfile
mkdir mydir > chgrp grupa mydir/
Ostatnim specjalnym uprawnieniem jest „sticky bit”. Gdy to jest ustawiony w katalogu, pliki w tym katalogu może usunąć tylko właściciel. Typowym zastosowaniem tego jest „/tmp/.”
chmod +t mydir2
chmod 1755 mydir2


Locate, read, and use system documentation including man, info, and files in /usr/share/doc
man ps, whatis ps, apropos ps (znajduje po stringu)
ls /usr/share/doc | grep [command]
Jeśli chcemy zupdatować whatis/apropos to wpisujemy mandb
Ścieżka crona >> /etc/cron.daily/man-db.cron
Boot, reboot, and shut down a system normally
boot, reboot
/boot/grub2/grub.cfg
/boot/efi
/boot/efi/EFI/redhat/grub.efi

Boot systems into different targets manually
systemctl get-default
systemd.unit=emergency.target
# systemctl set-default multi-user.target
# systemctl set-default multi-user
# systemctl set-default runlevel3.target
# systemctl set-default runlevel3
systemctl isolate multi-user (zmienia czasowo runlevel)
su -
whoami
su linuxconfig = su - linuxconfig
runlevel0.target or poweroff.target	shutdown
runlevel1.target or rescue.target	troubleshooting
runlevel2.target or multi-user.target	niezdefiniowany, taki jak 3
runlevel3.target or multi-user.target	multi-user non graphical
runlevel4.target or multi-user.target	definiowany przez użytk., taki jak 3
runlevel5.target or graphical.target	multi-user GUI
runlevel6.target or reboot.target	reboot
Interrupt the boot process in order to gain access to a system
Przy ekranie startowym wyboru kernela nacisnąć 'e' dla edytowania>
Wpisać rd.break w linii zaczynającej się na 'kernel=' , skasować rhgb quiet i ctrl+x >
Wpisać 'mount -o remount,rw /sysroot/', żeby nadać read write>
Wpisać 'chroot /sysroot/' i wpisać 'passwd' dla zmiany hasła>
Stworzyć 'touch /.autorelabel' > exit > logout
Identify CPU/memory intensive processes and kill processes
top, ps, iostat, netstat, vmstat, sar, pkill
nice -n 10 ./script.sh (start scriptu z niskim priorytetem)
renice +5 7891 (pid)
kill -9 7893
Adjust process scheduling
Priorytet procesu waha się od -20 (najwyższy) do +19 (najniższy). Wyższa uprzejmość obniża priorytet wykonania procesu, a niższa uprzejmość go zwiększa. Proces potomny dziedziczy ładność procesu nadrzędnego.
renice -n 5 1919

Manage tuning profiles
yum install tuned
systemctl enable --now tuned
tuned-adm active
tuned-adm recommend
tuned-adm profile <profile name>

Locate and interpret system log files and journals
/var/log/*
syslog >>  /etc/rsyslog.conf
SELinux >>  /var/log/audit/audit.log
journalctl
/var/log/messages
Preserve system journals
mkdir -p /var/log/journal
/etc/systemd/journald.conf >> ustawić dla trwałego przechowywania
[Journal]
Storage=persistent
systemctl restart systemd-journald
Start, stop, and check the status of network services
systemctl status sshd
systemctl network start
status, start, stop, enable, disable, enable --now
Securely transfer files between systems
scp username@from_host:file.txt /local/directory/
scp file.txt username@to_host:/remote/directory/
scp -r username@from_host:/remote/directory/  /local/directory/
scp -r /local/directory/ username@to_host:/remote/directory/
List, create, delete partitions on MBR and GPT disks
Dane są przechowywane na dyskach, które są logicznie podzielone na partycje. Partycja może istnieć na części dysku, na całym dysku lub na wielu dyskach. Każda partycja może zawierać system plików, przestrzeń surowych danych, przestrzeń wymiany lub przestrzeń zrzutu.
Dysk w RHEL można podzielić na kilka partycji. Informacje o partycjach są przechowywane na dysku w małym regionie, który jest odczytywany przez system operacyjny w czasie rozruchu. Jest to znane jako główny rekord rozruchowy (MBR) w systemach opartych na systemie BIOS i tabela partycji GUID (GPT) w systemach opartych na UEFI. Podczas uruchamiania systemu BIOS/UEFI skanuje wszystkie urządzenia pamięci masowej, wykrywa obecność MBR/GPT, identyfikuje dyski rozruchowe, ładuje program ładujący do pamięci z domyślnego dysku rozruchowego, wykonuje kod rozruchowy, aby odczytać tablicę partycji i zidentyfikować partycję /boot, i kontynuuje proces rozruchu, ładując jądro do pamięci i przekazując mu kontrolę.

MBR umożliwia utworzenie tylko do 4 partycji podstawowych na jednym dysku, z opcją użycia jednej z 4 partycji jako partycji rozszerzonej do przechowywania dowolnej liczby partycji logicznych. MBR nie ma również przestrzeni adresowej przekraczającej 2 TB ze względu na jego 32-bitową naturę i rozmiar sektora dysku wynoszący 512 bajtów, którego używa. MBR nie jest również nadmiarowy, więc system staje się niemożliwy do uruchomienia, jeśli zostanie w jakiś sposób uszkodzony.

GPT to nowszy 64-bitowy standard partycjonowania opracowany i zintegrowany z oprogramowaniem układowym UEFI. GPT pozwala na 128 partycji, użycie dysków znacznie większych niż 2 TB i nadmiarowe lokalizacje do przechowywania informacji o partycjach. GPT umożliwia również systemowi opartemu na BIOS-ie uruchamianie z dysku GPT przy użyciu programu ładującego przechowywanego w ochronnym MBR w pierwszym sektorze dysku.

Aby wyświetlić punkty montowania, rozmiar i dostępną przestrzeń:
df -h
W RHEL urządzenia blokowe są abstrakcją dla pewnego sprzętu, np. dysków twardych. Polecenie blkid wyświetla listę wszystkich urządzeń blokowych. Polecenie lsblk wyświetla więcej szczegółów na temat urządzeń blokowych.

fdisk -l # MBR
gdisk -l # GPT

W przypadku partycji opartych na MBR do tworzenia i usuwania partycji można użyć narzędzia fdisk. Aby dokonać zmiany na dysku: fdisk <disk>
W przypadku partycji opartych na GPT do tworzenia i usuwania partycji można użyć narzędzia gdisk. Aby dokonać zmiany na dysku: gdisk <disk>
Aby poinformować system operacyjny o zmianach w tablicy partycji: partprobe

Kod partycji SWAP 82/83 | LVM 8e
Czwarta partycja jest zawsze extended.
Create and remove physical volumes
Logical Volume Manager (LVM) służy do zapewnienia warstwy abstrakcji między fizyczną pamięcią masową a systemem plików. Umożliwia to zmianę rozmiaru systemu plików, rozłożenie go na wiele dysków fizycznych, wykorzystanie losowego miejsca na dysku itp.
Jedna lub więcej partycji lub dysków (physical volumes) może tworzyć kontener logiczny (volume group), który jest następnie dzielony na partycje logiczne (nazywane logical volumes). Są one dalej podzielone na physical extents(PE) i logical extents(LE).

Physical Volume (PV) jest tworzony, gdy blokowe urządzenie magazynujące jest objęte kontrolą LVM po przejściu przez proces inicjalizacji. Ten proces konstruuje struktury danych LVM na urządzeniu, w tym etykietę na drugim sektorze i informacje o metadanych. Etykieta zawiera identyfikator UUID, rozmiar urządzenia oraz wskaźniki do lokalizacji obszarów danych i metadanych.

Volume Group (VG) jest tworzona po dodaniu do niej co najmniej jednego physical volume. Przestrzeń ze wszystkich physical volumes w volume group jest agregowana w celu utworzenia jednej dużej puli pamięci, która jest następnie wykorzystywana do tworzenia jednego lub większej liczby logical volumes.

Żeby zobaczyć physical volumes:
pvs > z dodatkowym info pvdisplay

Żeby stworzyć / usunąć dysk lub partycje:
pvcreate <disk> / pvremove <disk>

Przypisanie physical volume do volume grupy:
Zobaczyć volume group > vgs > z dodatkowym info > vgdisplay
Żeby stworzyć volume grupe:
vgcreate nazwa <disk>
Żeby rozszerzyć istniejącą / pomniejszyć o dysk/ usunąć ostatni:
vgextend / vgreduce / vgremove nazwa <disk>

Tworzenie i usuwanie logical volume:
lvs > dodatkowe info > lvdisplay
lvcreate -L 4G lv1 vg1
Rozszerzanie:
lvextend -L +1G <sciezka do lv>
Redukowanie:
lvreduce -L -1G <sciezka do lv>
Usuwanie LV:
umount <punkt montowania>
lvremove <lvpath>
Configure systems to mount file systems at boot by universally unique ID (UUID) or label
Plik /etc/fstab to plik konfiguracyjny systemu, który zawiera listę wszystkich dostępnych dysków, partycji dyskowych i ich opcji. Każdy filesystem jest opisany w osobnym wierszu. Plik /etc/fstab jest używany przez polecenie mount, które odczytuje plik w celu określenia, które opcje powinny być użyte podczas montowania określonego urządzenia. Do tego pliku można dodać system plików, aby był on automatycznie montowany podczas rozruchu.  
Add new partitions and logical volumes, and swap to a system non-destructively
Pamięć wirtualna to pamięć RAM plus przestrzeń wymiany. Partycja wymiany to standardowa partycja dyskowa wyznaczona jako obszar wymiany przez polecenie mkswap. Plik może być również używany jako przestrzeń wymiany, ale nie jest to zalecane.
mkswap <device> > tworzenie
swapon <device> > włączanie
swapon -s > status swapóws
swapoff <device>
Plik /etc/fstab będzie wymagał nowego wpisu dla wymiany, aby był trwale tworzony.
Create and configure file systems
System plików to logical container używany do przechowywania plików i katalogów. Każdy system plików musi być podłączony do katalogu głównego hierarchii katalogów, aby był dostępny. Zwykle odbywa się to automatycznie podczas uruchamiania systemu, ale można to również zrobić ręcznie. Każdy system plików można podłączyć lub odmontować przy użyciu powiązanego z nim identyfikatora UUID lub przy użyciu etykiety, która może być do niego przypisana. Montowanie to proces dołączania dodatkowego systemu plików, który znajduje się na płycie CD-ROM, dysku twardym (HDD) lub innym urządzeniu pamięci masowej, do aktualnie dostępnego systemu plików komputera.

Każdy system plików jest tworzony na osobnej partycji lub woluminie logicznym. Typowy system RHEL ma wiele systemów plików. Podczas instalacji systemu operacyjnego domyślnie tworzone są systemy plików / i /boot. Typowe dodatkowe systemy plików tworzone podczas instalacji to /home, /opt, /tmp, /usr i /var.

Systemy plików obsługiwane w RHEL są klasyfikowane jako oparte na dysku, oparte na sieci i oparte na pamięci. Systemy plików oparte na dyskach i sieci są przechowywane w sposób trwały, podczas gdy dane w systemach opartych na pamięci są tracone podczas ponownego uruchamiania systemu. Poniżej przedstawiono różne systemy plików:

ext3: Trzecia generacja rozszerzonego systemu plików. Obsługuje kronikowanie metadanych w celu szybszego odzyskiwania, najwyższej niezawodności, systemów plików do 16 TB, plików do 2 TB i do 32 000 podkatalogów. ext3 zapisuje każdą aktualizację metadanych w całości do dziennika po jej zakończeniu. System przeszukuje dziennik systemu plików po ponownym uruchomieniu po wystąpieniu awarii systemu i szybko odzyskuje system plików przy użyciu zaktualizowanych informacji strukturalnych przechowywanych w jego dzienniku.

ext4: Czwarta generacja rozszerzonego systemu plików. Obsługuje systemy plików do 1 EB, pliki do 16 TB, nieograniczoną liczbę podkatalogów, dzienniki metadanych i kwot oraz rozszerzone atrybuty użytkowników.

xfs: XFS to wysoce skalowalny i wydajny 64-bitowy system plików. Obsługuje rejestrowanie metadanych w celu szybszego odzyskiwania po awarii, defragmentacji online, rejestrowania limitów rozszerzeń i rozszerzonych atrybutów użytkownika.

btrfs: System plików B-tree, który obsługuje rozmiar systemu 50 TB. Obsługuje więcej plików, większe pliki i większe woluminy niż ext4 oraz obsługuje funkcje tworzenia migawek i kompresji.

iso9660: Używane w optycznych systemach plików opartych na dyskach CD/DVD.

BIOS Boot: Bardzo mała partycja wymagana do uruchomienia urządzenia z tabelą partycji GUID (GPT) w systemie BIOS.

EFI System Partition: Mała partycja wymagana do uruchomienia urządzenia z tabelą partycji GUID (GPT) w systemie UEFI.

NFS: Katalog lub system plików udostępniony w sieci w celu uzyskania dostępu przez inne systemy Linux.

AutoFS: System plików NFS ustawiony na automatyczne montowanie i odmontowywanie w systemie zdalnym.

CIFS: Wspólny internetowy system plików (aka Samba). Katalog lub system plików udostępniony w sieci w celu uzyskania dostępu do systemu Windows i innych systemów Linux.

vfat: System plików MS-DOS przydatny podczas udostępniania plików między systemami Windows i Linux


Polecenie mount służy do dołączania systemu plików do żądanego punktu w hierarchii katalogów, aby udostępnić go użytkownikom i aplikacjom. Ten punkt jest określany jako punkt montowania, który jest zasadniczo pustym katalogiem utworzonym wyłącznie dla tego punktu. Polecenie mount wymaga podania bezwzględnej nazwy ścieżki (lub jej identyfikatora UUID lub etykiety) do urządzenia blokowego zawierającego system plików oraz nazwy punktu podłączenia w celu dołączenia go do drzewa katalogów. Polecenie mount dodaje wpis do pliku /proc/mounts i instruuje jądro, aby dodało wpis do pliku /proc/mounts również po pomyślnym zamontowaniu systemu plików. Przeciwieństwem polecenia mount jest unmount, które służy do odłączenia systemu plików od hierarchii katalogów i uczynienia go niedostępnym dla użytkowników i aplikacji.

Do stworzenia filesystemu:
mkfs.ext4 <sciezka>
mkfs.xfs <sciezka>
mount <sciezka>  /mnt
umount <sciezka> /mnt
fsck <sciezka> (sprawdzenie systemu plikow ext4)
dumpe2fs <sciezka> (sprawdzenie dodatkowych info o ext4>
xfs_repair (sprawdzenie systemu plikow xfs)
Mount and unmount network file systems using NFS
dnf install nfs-utils
mount -t nfs 10.0.2.5:/home/nfs-share /mnt (zamontowanie filesystemu)
alternatywnie można dodać do /etc/fstab > mount -a

Używanie AutoFS z NFS:

The /etc/autofs.conf File
	Configuration file for the autofs service itself.
The /etc/auto.master File
	Also known as the master map, this is the default primary configuration 
	file for autofs.

Server:
echo ”/export/home /etc/auto.home” » /etc/auto.master
echo ”* 127.0.0.1:/home/&’’ » /etc/auto.home
showmount -e
systemctl enable --now autofs


Extend existing logical volumes
Extend o 2GB logical volume:
lvextend -L +2G /dev/vg1/lv1
lvdisplay > potwierdzic zmiany
Powiększenie filesystemu:
df -Th > potwierdzenie filesystemu
resize2fs /dev/vg1/lvl1 > dla ext3/ext4
xfs_growfs /mnt > dla xfs
Create and configure set-GID directories for collaboration
SUID (oznaczający ustaw identyfikator użytkownika) służy do określenia, że ​​użytkownik może uruchomić plik wykonywalny z efektywnymi uprawnieniami właściciela pliku. Służy to przede wszystkim do podniesienia uprawnień bieżącego użytkownika. Gdy użytkownik wykona plik, system operacyjny będzie działał jako właściciel pliku. Zamiast normalnego x, który reprezentuje uprawnienia do wykonywania, widoczny będzie jako s.
chmod u+s <filename>

SGID (oznaczający identyfikator grupy) służy do określenia, że ​​użytkownik może uruchomić plik wykonywalny z efektywnymi uprawnieniami grupy będącej właścicielem. Służy to przede wszystkim do podniesienia uprawnień bieżącego użytkownika. Gdy użytkownik wykona plik, system operacyjny będzie działał jako właściciel pliku. Zamiast normalnego x, który reprezentuje uprawnienia do wykonywania, widoczny będzie jako s.
chmod g+s <filename>

Aby utworzyć grupę i katalog współdzielony:
groupadd accounts
mkdir -p /home/shared/accounts
chown nobody:accounts /home/shared/accounts
chmod g+s /home/shared/accounts
chmod 070 /home/shared/accounts
Używając SGID w katalogu, wszystkie pliki utworzone w katalogu będą własnością grupy katalogu, a nie grupy właściciela.

Jeśli bit sticky jest ustawiony w katalogu, pliki w tym katalogu może usunąć tylko właściciel. Typowy przypadek użycia dotyczy katalogu /tmp. Może do niego zapisywać dowolny użytkownik, ale inni użytkownicy nie mogą usuwać plików innych osób.
chmod +t <katalog>

SUID, SGID i sticky bit można również ustawić za pomocą notacji liczbowej. Standardowa liczba (rwx) jest poprzedzona 4 dla SUID, 2 dla SGID i 1 dla bitu sticky.



Configure disk compression – wycofane z RHCSA 9
Wirtualny optymalizator danych (VDO) zapewnia redukcję danych poprzez deduplikację, kompresję i cienkie przydzielanie.
dnf install vdo kmod-kvdo
vdo create --name=vdo1 --device=/dev/sdb --vdoLogicalSize=30G --writePolicy=async
mkfs.xfs /dev/mapper/vdo1
mount /dev/mapper/vdo1 /mnt
Manage layered storage – wycofane z RHCSA 9
Stratis to rozwiązanie do zarządzania pamięcią masową wprowadzone w RHEL 8, które umożliwia konfigurację zaawansowanych funkcji pamięci masowej, takich jak zarządzanie oparte na puli, elastyczne przydzielanie zasobów, migawki systemu plików i monitorowanie.
dnf install -y stratisd stratis-cli 
systemctl start stratisd
Sprawdzenie filesystemu na dysku:
lsblk -f / blkid -p /dev/sdb

Jeśli istnieje system plików, usuń go za pomocą:
wipefs -a /dev/sdb
Aby utworzyć system plików i potwierdzić:
stratis pool create appteam /dev/*
stratis blockdev
stratis fs create appteam appfs1
stratis fs
mount /stratis/appteam/appfs1 /mnt/app_storage

in /etc/fstab:
/stratis/appteam/appfs1    /mnt/app_storage   xfs     defaults,x-systemd.requires=stratisd.service 0 0

df -h
stratis pool add-data appteam /dev/*
stratis blockdev
stratis fs snapshot strat1 fs1 snapshot1

Aby zamontować migawkę:
unmount /stratis/strat1/fs1
mount /stratis/strat1/snapshot1 /mnt

Aby usunąć system plików i pulę stratis i potwierdzić:
stratis filesystem destroy strat1 fs1
stratis filesystem list
stratis pool destroy strat1
stratis pool list
Diagnose and correct file permission problems
Uprawnienia do plików można modyfikować za pomocą chmod i setfacl.
Schedule tasks using at and cron
Planowanie i wykonywanie zadań jest obsługiwane przez demony atd i crond. Podczas gdy atd zarządza zadaniami zaplanowanymi do jednorazowego uruchomienia w przyszłości, crond jest odpowiedzialny za powtarzalne uruchamianie zadań w określonych z góry godzinach. Podczas uruchamiania crond odczytuje harmonogramy z plików znajdujących się w katalogach /var/spool/cron i /etc/cron.d i ładuje je do pamięci w celu późniejszego wykonania.
Istnieją 4 pliki, które kontrolują uprawnienia do ustawiania zaplanowanych zadań. Są to at.allow, at.deny, cron.allow i cron.deny. Pliki te znajdują się w katalogu /etc. Składnia plików jest identyczna, każdy plik przyjmuje 1 nazwę użytkownika w wierszu. Jeśli nie istnieją żadne pliki, żaden użytkownik nie jest dozwolony. Domyślnie pliki odmowy istnieją i są puste, a pliki zezwolenia nie istnieją. Otwiera to pełny dostęp do korzystania z obu narzędzi dla wszystkich użytkowników. 
Wszystkie działania dotyczące atd i crond są rejestrowane w pliku /var/log/cron.
Do zaplanowania zadania używa się poniższej składni:
at 11:30pm 6/30/15
Polecenia do wykonania są zdefiniowane w terminalu, naciśnij ctrl + d po zakończeniu. Dodane zadanie można przeglądać za pomocą at i można je usunąć za pomocą opcji -d.

Można również wykonać script:
at -f ~/script1.sh 11:30pm 6/30/15

Plik /etc/crontab ma następujące kolumny:
1: Minuty godziny (0-59), z wieloma wartościami oddzielonymi przecinkami lub * do oznaczenia każdej minuty.
2: Godziny dnia (0-23), z wieloma wartościami oddzielonymi przecinkami lub * do oznaczenia każdej godziny.
3: Dni miesiąca (1-31), z wieloma wartościami oddzielonymi przecinkami lub * do reprezentowania każdego dnia.
4: Miesiąc roku (1-12, styczeń-grudzień), z wieloma wartościami oddzielonymi przecinkami lub * reprezentującymi każdy miesiąc.
5: Dzień tygodnia (0-6, nd-sob), z wieloma wartościami oddzielonymi przecinkami lub * do oznaczenia każdego dnia.
6: Pełna nazwa ścieżki polecenia lub skryptu do wykonania, wraz z wszelkimi argumentami.
Wartości kroków mogą być używane z */2, co oznacza co 2 minuty.


Do edycji pliku można użyć polecenia crontab. Typowe opcje to e (edycja), l (podgląd), r (usuń):
crontab -e
Start and stop services and configure services to start automatically at boot
Aby sprawdzić status usługi:
systemctl status <service>
Aby rozpocząć /zatrzymać usługę:
systemctl start/stop <service>
Aby usługa przeładowała swoją konfigurację:
systemctl reload <service>
Aby usługa uruchamiała/nie się przy starcie:
systemctl enable / disable <service>
Aby wyświetlić plik konfiguracyjny usługi:
systemctl list-dependencies <service>


Configure systems to boot into a specific target automatically
systemctl get-default
systemctl list-units --type target --all
systemctl set-default <target>
systemctl isolate
Configure time service clients
Aby ustawić zegar systemowy zgodnie z zegarem sprzętowym:
hwclock -s
Aby ustawić zegar sprzętowy zgodnie z zegarem systemowym:
hwclock -w
Do wyświetlenia daty i godziny można również użyć polecenia timedatectl.
Aby zmienić datę lub godzinę:
timedatectl set-time 2020-03-18
timedatectl set-time 22:43:00
timedatectl list-timezones
Aby włączyć NTP:
timedatectl set-ntp yes


Aby uruchomić usługę chronyd
systemctl start chronyd
sudo vi /etc/chronv.conf » server <ip> iburst ; systemctl restart chronyd
chronyc sourcestats - command displays statistics about chrony time sources.
chronyc sources - command displays information about chrony time sources
chronyc sources -v   -  command displays information about chrony time sources, in a verbose format, with an informative header.
chronyc tracking - command, to check the status of time sync, on a server using chrony.
chronyc makestep

Install and update software packages from Red Hat Network, a remote repository, or from the local file system
Rozszerzenie .rpm to format plików, którymi manipuluje system zarządzania pakietami Redhat Package Manager (RPM). RHEL 8 zapewnia narzędzia do instalacji i administrowania pakietami RPM. Pakiet to grupa plików zorganizowanych w strukturę katalogów i metadanych, które tworzą aplikację.
Nazwa pakietu RPM ma następujący format:
openssl-1.0.1e-34.el7.x86_64.rpm
# package name = openssl
# package version = 1.0.1e
# package release = 34
# RHEL version = el7
# processor architecture = x86_64
# extension = .rpm

Polecenie menedżera subskrypcji może służyć do łączenia subskrypcji Red Hat z systemem.
Polecenie dnf jest nakładką na rpm i jest preferowanym narzędziem do zarządzania pakietami. Polecenie yum zostało zastąpione przez dnf w RHEL 8. Wymaga to, aby system miał dostęp do repozytorium oprogramowania. Główną zaletą dnf jest to, że automatycznie rozwiązuje zależności, pobierając i instalując wszelkie dodatkowe wymagane pakiety.

Aby skonfigurować repozytorium: (from scratch)
sudo vi /etc/yum.repos.d/epel.repo

[epel]
name=Extra Packages for Enterprise Linux
baseurl= <paste repo url here>
enabled=1
gpgcheck=0

sudo yum clean all

Aby wyświetlić listę włączonych i wyłączonych repozytoriów:

sudo yum list –available <package>
dnf repolist all
dnf repoinfo
Aby wyszukać pakiet:
dnf search <package>
dnf list <package>

dnf info <package>
dnf install <package>
dnf remove <package>
dnf provides <path>
dnf localinstall <path>
dnf groups list
dnf group "System Tools"
dnf group remove "System Tools"
dnf history list
dnf config-manager --add-repo <url>
dnf config-manager --enablerepo <repository>
dnf config-manager --disablerepo <repository>

Aby utworzyć repozytorium:
dnf install createrepo
mkdir <path>
createrepo --<name> <path>
yum-config-manager --add-repo file:// HYPERLINK 
Work with package module streams
RHEL 8 wprowadził koncepcję strumieni aplikacji. Komponenty udostępniane jako strumienie aplikacji mogą być pakowane jako moduły lub pakiety RPM i są dostarczane za pośrednictwem repozytorium AppStream w RHEL 8. Strumienie modułów reprezentują wersje składników Application Stream. Tylko jeden strumień modułów może być aktywny w określonym czasie, ale umożliwia to dostępność wielu różnych wersji w tym samym repozytorium dnf.
dnf module list
dnf module info --profile <module-name>
dnf module install <module-name>
dnf module remove <module-name>
dnf module install <module-name>:<version>/<profile>
<module-name> -v (sprawdza wersje modułu)

Modify the system bootloader
Konfigurację GRUB2 można edytować bezpośrednio na ekranie startowym. Konfigurację można również edytować za pomocą wiersza poleceń.
command grub2


Aby dokonać zmiany w konfiguracji:
vi /etc/default/grub
# Change a value
grub2-mkconfig -o /boot/grub2/grub.cfg
# View changes
less /boot/grub2/grub.cfg

Manage basic networking
Format adresu IPv4 to zestaw 4 8-bitowych liczb całkowitych, które dają 32-bitowy adres IP. Format IPv6 to zestaw 8 16-bitowych liczb szesnastkowych, które dają 128-bitowy adres IP.
Polecenie nmcli służy do konfigurowania sieci za pomocą usługi NetworkManager.
To polecenie służy do tworzenia, wyświetlania, edytowania, usuwania, aktywowania i dezaktywowania połączeń sieciowych. Każde urządzenie sieciowe odpowiada urządzeniu Network Manager. Użycie nmcli z opcją połączenia wyświetla listę dostępnych profili połączeń w NetworkManager. Polecenia ip można również użyć do konfiguracji sieci. Główna różnica między ip a nmcli polega na tym, że zmiany wprowadzone za pomocą polecenia ip nie są trwałe.


Aby wyświetlić informacje o interfejsie sieciowym:
less /etc/sysconfig/network-scripts/if*
Żeby zobaczyć IP adress:
ip addr
Aby wyświetlić aktualne połączenia:
nmcli connection show
Użycie nmcli z opcją urządzenia wyświetla listę dostępnych urządzeń sieciowych w systemie.
Aby wyświetlić aktualny stan urządzenia sieciowego i szczegóły:
nmcli device status
nmcli device show

Aby dodać połączenie Ethernet IPv4:
nmcli connection add con-name <name> ifname <name> type ethernet ip4 <address> gw4 <address>
Aby ręcznie zmodyfikować połączenie:
nmcli connection modify <name> ipv4.addresses <address>
nmcli connection modify <name> ipv4.method manual
nmcli connection delete <name>
Aby aktywować połączenie:
nmcli connection up <name>

Aby sprawdzić używane serwery DNS:
cat /etc/resolv.conf
Aby zmienić używany serwer DNS:
nmcli con mod <name> ipv4.dns <dns>
systemctl restart NetworkManager.service
Configure hostname resolution
Aby wyszukać adres IP na podstawie nazwy hosta, można użyć poleceń host lub nslookup.
Plik /etc/hosts jest jak lokalny DNS. Plik /etc/nsswitch.conf kontroluje kolejność sprawdzania zasobów pod kątem rozwiązania.
Aby wyszukać nazwę hosta:
hostname -s # short
hostname -f # fully qualified domain name

Plik nazwy hosta znajduje się w /etc/hostname. Aby odświeżyć wszelkie zmiany, uruchom polecenie hostnamectl.
Configure network services to start automatically at boot
Aby zainstalować usługę i sprawić, by uruchamiała się automatycznie przy starcie:
dnf install httpd
systemctl enable httpd
Aby ustawić połączenie, które ma być włączone podczas rozruchu:
nmcli connection modify eth0 connection.autoconnect yes
Restrict network access using firewall-cmd/firewall
Netfilter to framework dostarczany przez jądro Linuksa, który zapewnia funkcje filtrowania pakietów. W RHEL 7 i wcześniejszych iptables był domyślnym sposobem konfigurowania Netfiltera. Wadą ipables było to, że dla ipv6 wymagana była osobna wersja (ip6tables), a interfejs użytkownika nie jest zbyt przyjazny dla użytkownika.

Domyślnym systemem firewall w RHEL 8 jest firewalld. Firewalld jest zaporą strefową.
Każda strefa może być powiązana z jednym lub większą liczbą interfejsów sieciowych, a każda strefa może być skonfigurowana do akceptowania lub odrzucania usług i portów.
Polecenie firewall-cmd jest klientem wiersza poleceń dla firewalld.

Aby sprawdzić strefy zapory:
firewall-cmd --get-zones
To list configuration for a zone:
firewall-cmd --zone work --list-all
Aby utworzyć nową strefę:
firewall-cmd --new-zone servers --permanent
Aby ponownie załadować konfigurację firewall-cmd:
firewall-cmd --reload
Aby dodać usługę do strefy:
firewall-cmd --zone servers --add-service=ssh --permanent
Aby dodać interfejs do strefy:
firewall-cmd --change-interface=enp0s8 --zone=servers --permanent
Aby uzyskać aktywne strefy:
firewall-cmd --get-active-zones
Aby ustawić strefę domyślną:
firewall-cmd --set-default-zone=servers
Aby sprawdzić usługi dozwolone dla strefy:
firewall-cmd --get-services
Aby dodać port do strefy:
firewall-cmd --add-port 8080/tcp --permanent --zone servers
Manage users and groups
RHEL 8 obsługuje trzy typy kont użytkowników: root, normalne i service. Użytkownik root ma pełny dostęp do wszystkich usług i funkcji administracyjnych. Zwykły użytkownik może uruchamiać aplikacje i programy, do których wykonywania ma uprawnienia. Konta usług są odpowiedzialne za opiekę nad zainstalowanymi usługami.

Plik /etc/passwd zawiera ważne dane logowania użytkownika.

Plik /etc/shadow może odczytać tylko użytkownik root i zawiera informacje o uwierzytelnianiu użytkownika. Każdy wiersz w pliku odpowiada jednemu wpisowi w pliku passwd. Ustawienia ważności hasła są zdefiniowane w pliku /etc/login.defs. Plik /etc/defaults/useradd zawiera wartości domyślne dla polecenia useradd.

Plik /etc/group zawiera informacje o grupie. Każdy wiersz w pliku przechowuje jeden wpis grupy.

Plik /etc/gshadow przechowuje zaszyfrowane hasła grup. Każdy wiersz w pliku odpowiada jednemu wpisowi w pliku grupy.

Ze względu na ręczną modyfikację mogą wystąpić niespójności między powyższymi czterema plikami uwierzytelniającymi. Polecenie pwck służy do sprawdzania niespójności.

Komendy vipw i vigr służą do modyfikowania odpowiednio plików passwd i group. Polecenia te uniemożliwiają dostęp do zapisu w tych plikach podczas wprowadzania modyfikacji przez uprzywilejowanego użytkownika.

useradd user1
cat /etc/group | grep user1
Aby określić UID i GID podczas tworzenia użytkownika:
useradd -u 1010 -g 1005 user1
Aby utworzyć użytkownika i dodać go do grupy:
useradd -G IT user2
Zauważ, że -G jest grupą drugorzędną, a -g jest grupą podstawową. Grupa podstawowa to grupa, którą system operacyjny przypisuje do plików, do których należy użytkownik. Grupa drugorzędna to jedna lub więcej innych grup, do których należy również użytkownik.
Aby usunąć użytkownika:
userdel user1
Aby zmodyfikować użytkownika:
usermod -l user5 user1 # note that home directory will remain as user1
Aby dodać użytkownika, ale nie dać dostępu do powłoki:
useradd -s /sbin/nologin user
Change passwords and adjust password aging for local user accounts
Aby zmienić hasło dla użytkownika:
passwd user1
Aby przejść przez informacje dotyczące starzenia się hasła, można użyć polecenia chage bez żadnych opcji.
Aby wyświetlić informacje o wygaśnięciu hasła użytkownika:
chage -l user1
Aby ustawić wygaśnięcie hasła dla użytkownika za 30 dni od teraz:
chage -M 30 user1
Aby ustawić datę ważności hasła:
chage -E 2021-01-01 user1
Aby ustawić hasło tak, aby nigdy nie wygasało:
zmiana -E -1 użytkownik1
Create, delete, and modify local groups and group memberships
Aby utworzyć grupę:
groupadd IT
Aby utworzyć grupę z określonym GID:
groupadd -g 3032
Aby usunąć grupę:
groupdel IT
Aby zmienić nazwę grupy:
groupmod -n IT-Support IT
Aby zmodyfikować GID grupy:
groupmod -g 3033 IT-Support
Aby dodać użytkownika do grupy:
groupmod -aG IT-Support user1
Aby wyświetlić członków grupy:
groupmems -l -g IT-Support
Aby usunąć użytkownika z grupy:
grupka -d user1 IT-Support
Configure superuser access
Aby wyświetlić plik sudoers:
visudo /etc/sudoers
Członkowie grupy wheel mogą używać sudo we wszystkich poleceniach. Aby dodać użytkownika do grupy wheel:
sudo usermod -aG wheel user1
Aby zezwolić poszczególnym użytkownikom sudo na dostęp do określonych poleceń:
visudo /etc/sudoers
user2 ALL=(root) /bin/ls, /bin/df -h, /bin/date
Configure firewall settings using firewall-cmd/firewalld
Ustawienia sieciowe, takie jak maskarada i przekazywanie IP, można również skonfigurować w aplikacji GUI firewall-config. Aby zainstalować tę aplikację:
dnf zainstaluj firewall-config
Aby ustawić przekierowanie portów w ustawieniach jądra:
vi /etc/sysctl.conf
# add line
net.ipv4.ip_forward=1
# save file
sysctl -p
Create and use file access control lists
Aby dać użytkownikowi dostęp do odczytu i zapisu do pliku za pomocą listy kontroli dostępu:
setfacl -m u:user1:rw- testFile
getfacl testFile
Aby ograniczyć użytkownikowi dostęp do pliku za pomocą listy kontroli dostępu:
setfacl -m u:user1:000 testFile
getfacl testFile
Aby usunąć listę kontroli dostępu dla użytkownika:
setfacl -x u:user1 testFile
getfacl testFile
Aby dać grupie dostęp do odczytu i wykonywania rekurencyjnie przy użyciu listy kontroli dostępu:
setfacl -R -m g:IT-Support:r-x testDirectory
getfacl testFile
Configure key-based authentication for SSH 
Aby wygenerować pliki id_rsa i id_rsa.pub:
ssh-keygen
Aby włączyć ssh dla użytkownika:
touch authorized_keys
echo "publicKey" > /home/new_user/.ssh/authorized_keys
Aby skopiować klucz publiczny z serwera 1 na serwer 2:
ssh-copy-id -i ~/.ssh/id_rsa.pub server2
cat ~/.ssh/known_hosts # validate from server1

Set enforcing and permissive modes for SELinux
Security Enhanced Linux (SELinux) to implementacja architektury obowiązkowej kontroli dostępu (MAC) opracowana przez amerykańską Narodową Agencję Bezpieczeństwa (NSA). MAC zapewnia dodatkową warstwę ochrony poza standardową Linux Discretionary Access Control (DAC), która obejmuje tradycyjne uprawnienia do plików i katalogów, ustawienia ACL, ustawienia bitów setuid/setgid, uprawnienia su/sudo itp.
Kontrola MAC jest drobnoziarnista; chronią inne usługi w przypadku negocjacji jednej z usług. MAC używa zestawu zdefiniowanych reguł autoryzacji zwanych polityką do badania atrybutów bezpieczeństwa związanych z podmiotami i obiektami, gdy podmiot próbuje uzyskać dostęp do obiektu i decyduje, czy zezwolić na tę próbę dostępu. Decyzje SELinux są przechowywane w specjalnej pamięci podręcznej zwanej Access Vector Cache (AVC).
Gdy aplikacja lub proces żąda dostępu do obiektu, SELinux sprawdza w AVC, gdzie są buforowane uprawnienia dla podmiotów i obiektów. Jeśli nie można podjąć decyzji, wysyła żądanie do serwera bezpieczeństwa. Serwer zabezpieczeń sprawdza kontekst zabezpieczeń aplikacji lub procesu oraz obiektu. Kontekst bezpieczeństwa jest stosowany z bazy danych strategii SELinux.
Aby sprawdzić status SELinux:
getenforce
sestatus
Aby ustawić SELinux w trybie zezwalającym, zmodyfikuj plik /etc/selinux/config zgodnie z poniższymi wskazówkami i uruchom ponownie:
SELINUX=permissive
Wiadomości rejestrowane z SELinux są dostępne w /var/log/messages.
List and identify SELinux file and process context
Aby wyświetlić konteksty SELinux dla plików:
ls -Z
Aby wyświetlić konteksty dla użytkownika:
id -Z
Przedstawione konteksty są zgodne ze składnią user:role:type:level. Użytkownik SELinux jest mapowany na użytkownika Linux przy użyciu polityki SELinux. Rola jest pośrednikiem między domenami a użytkownikami SELinux. Typ definiuje domenę dla procesów i typ dla plików. Poziom jest używany dla zabezpieczeń wielokategorii (MCS) i zabezpieczeń wielopoziomowych (MLS).
Aby wyświetlić procesy dla użytkownika:
ps -Z # ps -Zaux, aby zobaczyć dodatkowe informacje
Restore default file contexts
Aby wyświetlić konteksty SELinux dla plików:
chcon unconfined:u:object_r:tmp_t:s0
Aby przywrócić konteksty SELinux dla pliku:
restorecon file.txt
Aby odtworzyć konteksty SELinux rekurencyjnie dla katalogu:
restorecon -R directory
Use boolean settings to modify system SELinux settings
SELinux ma wiele zdefiniowanych kontekstów i polityk. Wartości logiczne w SELinux umożliwiają włączanie i wyłączanie wspólnych reguł.
Aby sprawdzić ustawienia logiczne SELinux:
getebool -a | wirtualna skrzynka grep
Aby ustawić na stałe ustawienie logiczne SELinux:
setsebool -P use_virtualbox on
Diagnose and address routine SELinux policy violations
Narzędzie administracyjne SELinux jest narzędziem graficznym, które umożliwia wykonanie wielu operacji konfiguracyjnych i zarządczych. Aby zainstalować i uruchomić narzędzie:
yum install setools-gui
yum install policycoreutils-gui
system-config-selinux
Alerty SELinux są zapisywane do /var/log/audit/audit.log, jeśli demon auditd jest uruchomiony, lub do pliku /var/log/messages przez demona rsyslog w przypadku braku auditd.
Dostęp do GUI o nazwie SELinux Troubleshooter można uzyskać za pomocą polecenia sealert. Pozwala to na analizę wiadomości o odmowie SELinux i zapewnia zalecenia dotyczące rozwiązywania problemów
Find and retrieve container images from a remote registry
Kontener służy do uruchamiania wielu izolowanych aplikacji na tym samym sprzęcie. W przeciwieństwie do maszyny wirtualnej kontenery współużytkują system operacyjny systemów hosta. Jest lżejszy, ale trochę mniej elastyczny. 
Podman to silnik kontenerowy opracowany przez firmę Redhat. Podman to alternatywa dla znanego silnika kontenerowego Docker. Służy do bezpośredniego zarządzania podami i obrazami kontenerów. Interfejs wiersza poleceń Podmana (CLI) używa tych samych poleceń, co interfejs Docker CLI. Docker nie jest oficjalnie obsługiwany w RHEL 8.
Aby wyszukać obraz w zdalnym repozytorium i pobrać go:
dnf install podman -y
podman search httpd # note that docker.io/library/httpd has 3000+ stars
podman pull docker.io/library/httpd
Inspect container images
Aby wyświetlić obrazy po ich pobraniu:
podman images
Aby sprawdzić obraz za pomocą Podmana:
podman inspect -l # -l gets the latest container
Aby sprawdzić obraz w zdalnym rejestrze za pomocą Skopeo:
dnf zainstaluj skopeo -y skopeo sprawdza docker://registry.fedoraproject.org/fedora:latest
Perform container management using commands such as podman and skopeo
Strona podręcznika dla Podmana i bash-completion może być użyta, aby podać więcej szczegółów na temat korzystania z Podmana.
Aby wyświetlić logi kontenera:
podman logs -l
Aby wyświetlić pid dla kontenera:
podman top -l
Perform basic container management such as running, starting, 
Aby rozpocząć, zatrzymaj i usuń kontener:
podman run -dt -p 8080:80/tcp docker.io/library/httpd # redirect requests on 8080 host port to 80 container port
podman ps -a # view container details, use -a to see all
# check using 127.0.0.1:8080 on a browser
podman stop af1fc4ca0253 # container ID from podman ps -a
podman rm af1fc4ca0253
stopping, and listing running containers
Dockerfile może służyć do tworzenia niestandardowego kontenera:
sudo setsebool -P container_manage_cgroup on
vi Dockerfile
# contents of Dockerfile
#####
#FROM registry.access.redhat.com/ubi8/ubi-init
#RUN yum -y install httpd; yum clean all; systemctl enable httpd;
#RUN echo "Successful Web Server Test" > /var/www/html/index.html
#RUN mkdir /etc/systemd/system/httpd.service.d/; echo -e '[Service]\nRestart=always' > /etc/systemd/system/httpd.service.d/httpd.conf
#EXPOSE 80
#####
podman build -t mysysd .
podman run -d --name=mysysd_run -p 80:80 mysysd
podman ps # confirm that container is running

Zauważ, że SELinux Boolean, o którym mowa powyżej, można znaleźć za pomocą:
getsebool -a | grep "container"
Zauważ, że powyższy rejestr to Podman Universal Base Image (UBI) dla RHEL 8.
Configure a container to start automatically as a systemd service
Podman nie został pierwotnie zaprojektowany do uruchamiania całego systemu Linux lub zarządzania usługami, takimi jak kolejność uruchamiania, zależność, sprawdzanie i odzyskiwanie usług po awarii. To jest zadanie systemu inicjującego, takiego jak systemd.
Konfigurując plik jednostki systemd na komputerze hosta, host może automatycznie uruchamiać się, zatrzymywać, sprawdzać stan i w inny sposób zarządzać kontenerem jako usługą systemd. Wiele usług systemu Linux jest już spakowanych, aby RHEL mógł działać jako usługi systemd.

Aby skonfigurować kontener do działania jako usługa systemd:
sudo setsebool -P container_manage_cgroup on
podman run -d --name httpd-server -p 8080:80 # -d for detached, -p for port forwarding
podman ps # confirm the container is running
vi /etc/systemd/system/httpd-container.service
# contents of httpd-container.service
#####
#[Unit]
#Description=httpd Container Service
#Wants=syslog.service
#
#[Service]
#Restart=always
#ExecStart=/usr/bin/podman start -a httpd-server
#ExecStop=/usr/bin/podman stop -t 2 httpd-server
#
#[Install]
#WantedBy=multi-user.target
#####
systemctl start httpd-container.service
systemctl status httpd-container.service # confirm running
systemctl enable httpd-container.service # will not run as part multi-user.target
Zauważ, że inne usługi systemd można przeglądać w /etc/systemd/system i używać jako przykładów.
Attach persistent storage to a container
Aby dołączyć pamięć trwałą do kontenera:
ls /dev/sda1 # using this disk
mkdir -p /home/containers/disk1
podman run --privileged -it -v /home/containers/disk1:/mnt docker.io/library/httpd /bin/bash #  --privileged to allow with SELinux, -it for interactive terminal, -v to mount, and /bin/bash to provide a terminal
Conditionally execute code (use of: if, test, [], etc.)
Przykład użycia instrukcji if i test pokazano w pliku example.sh poniżej:
# contents of example.sh
#####
##!/bin/bash
#ping -c 1 $1
#if test "$?" -eq "0"; then
#	echo "$1 IP is reachable"
#else
#	echo "$1 IP is not reachable"
#fi
#exit
#####
Argumenty wejściowe można przekazać po nazwie skryptu, np. 1 jest pierwszym argumentem wejściowym. $? termin rozszerza kod zakończenia ostatnio wykonanego polecenia. Podczas używania echo argument -e może być użyty do wypisania znaków, takich jak nowe wiersze.

Przykład użycia instrukcji case jest pokazany w example.sh poniżej:
# contents of example.sh
#####
##!/bin/bash
#now=$(date + "%a")
#case $now in
#	Mon)
#		echo "Full Backup";
#		;;
#	Tue|Wed|Thu|Fri)
#		echo "Partial Backup";
#		;;
#	Sat|Sun)
#		echo "No Backup";
#		;;
#	*)	;;
#esac
#exit
#####

Przykład używając [] jest pokazany z example.sh poniżej:
# contents of example.sh
#####
##!/bin/bash
#ping -c 1 $1
#if ["$?" -eq "0"]; then
#	echo "$1 IP is reachable"
#else
#	echo "$1 IP is not reachable"
#fi
#exit
#####
Use Looping constructs (for, etc.) to process file, command line input
Przykład pętli for pokazano w example.sh poniżej:
# contents of example.sh
#####
##!/bin/bash
#for file in ./*.log
#do
#	mv "${file}" "${file}".txt
#done
#exit
#####
Przykład pętli while jest pokazany w example.sh poniżej:
# contents of example.sh
#####
##!/bin/bash
#input = "/home/kafka.log"
#while IFS = read -r line
#do
#	echo "$line"
#done < "$input"
#exit
#####
Process script inputs ($1, $2, etc.)
Dostęp do pierwszej zmiennej przekazanej do skryptu można uzyskać za pomocą $1
Processing output of shell commands within a script
Przykład pokazano z example.sh poniżej:
# contents of example.sh
#####
##!/bin/bash
#echo "Hello World!" >> example-`date +%Y%m%d-%H%M`.log
#exit
#####
Processing shell command exit codes
$? termin rozszerza kod zakończenia ostatnio wykonanego polecenia.


