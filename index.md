# Diagnostyka systemu Linux

Zobacz [  podsumowanie](#podsumowanie).

## lsblk
Podaje informacje na **temat  dysku twardego**. Aby wyświetlić konkretne
informacje skorzystaj z **przełącznika -o** i podaj nazwy kolumn.

### Najważniejsze kolumny

- **NAME** - nazwa urządzenia
- **FSTYPE** - system plików
- **MODEL** - model urządzenia
- **SERIAL** - numer seryjny
- **SIZE** - pojemność urządzenia

**Przykład**

![Polecenie lsblk](img/1.1.png)

## lscpu
Podaje informacje o **  procesorze**.

**Niektóre z informacji które możemy znaleźć:**

- Nazwa
- Taktowanie
- Liczba rdzeni
- Wielkość pamięci L1 Cache
- Wielkość pamięci L2 Cache

**Przykład**

![Polecenie lscpu](img/1.2.png)

## lspci
Wyświetla urządzenia PCI w tym ** kartę graficzną** i ** kartę sieciową**.

### Karta graficzna

![Polecenie lspci](img/1.3.png)

**Użyta komenda:** lspci -v | more

### Karta sieciowa

![Polecenie lspci](img/1.3.2.png)

**Użyta komenda:** lspci -v | more

## Plik /etc/os-release
Podaje **nazwę** i **wersje systemu operacyjnego**.

**Przykład**

![Plik /etc/os-release](img/1.4.png)

Aby wyświetlić zawartość pliku korzystam z polecenia **cat**.

## uname
Podaje m.in. ** wersję jądra (przełącznik -r)** i ** architekturę (przełacznik -p)**.

### Wersja jądra

![uname -r](img/1.5.1.png)

### Architektura

![uname -p](img/1.5.2.png)

## dmidecode
Dostarcza informacji na temat m.in. **pamięci RAM, procesorze, płycie głównej**. Aby wybrać konkretne urządzenie skorzystaj z przełącznika **-t**.

### Pamięć RAM
![dmidecode -t memory](img/1.6.1.png)

**Użyta komenda:** dmidecode -t memory

### Płyta główna
![dmidecode -t baseboard](img/1.6.2.png)

**Użyta komenda:** dmidecode -t baseboard

## top
Wyświetla **procesy** oraz **informacje o zasobach komputera**.

**Przykład**
![top](img/1.7.1.png)

**Informacje które możemy odczytać to między innymi:**

- liczba uruchomionych procesów
- liczba uśpionych procesów
- ilość wolnej pamięci RAM
- ilość używanej pamięci RAM

## du
Wyświetla rozmiar katalogu. Aby wygodnie wyświetlić wyniki skorzystaj
z przełączników **-h** i **-s**.

### Rozmiar katalogu /etc
![du -sh /etc](img/1.8.1.png)

**Użyta komenda:** du -sh /etc

### Rozmiar katalogu /var

![du -sh /var](img/1.8.2.png)

**Użyta komenda:** du -sh /var

## hostname
![hostname](img/1.9.png)

Wyświetla nazwę hosta.

## Plik /etc/passwd
Zawiera listę wszystkich użytkowników wraz z ich UID, GID, ścieżką do katalogu domowego i używaną powłoką.

**Przykład:**

![cat /etc/passwd](img/1.10.1.png)

**<span style="color:var(--red-color)">1000 - UID</span>**

**<span style="color:var(--green-color)">100 - GID</span>**

Jeżeli nie pamiętasz, które jest które użyj polecenia [id](#id).

## id
![id admin](img/1.11.png)

Wyświetla **UID** i **GID** określonego użytkownika.

## Podsumowanie

| Informacja                            | Polecenie                                             |
|---------------------------------------|-------------------------------------------------------|
|   Karta graficzna                    | lspci -v \| more  [](#lspci)                         |
|   Karta sieciowa                     | lspci -v \| more  [](#lspci)                         |
|   Nazwa i wersja system operacyjnego | /etc/os-release   [](#plik-etcos-release)            |
|   Wersja jądra                       | uname -r          [](#uname)                         |
|   Architektura                       | uname -p          [](#uname)                         |
|   Pamięć RAM                         | dmidecode -t memory [](#dmidecode)                   |
|   Płyta główna                       | dmidecode -t baseboard [](#dmidecode)                |
|   Procesy i zasoby komputera         | top [](#top)                                         |
| 猪  Rozmiar katalogu                   | du [](#du)                                           |
|   Nazwa hosta                        | hostname [](#hostname)                               |
|   Używana powłoka                    | /etc/passwd [](#plik-etc-passwd)                     |
| פּ  Ścieżka do katalogu domowego       | /etc/passwd [](#plik-etc-passwd)                     |
|   UID i GID użytkownika              | /etc/passwd [](#plik-etc-passwd) lub id [](#id)     |

# Konfiguracja serwera tekstowego Open Suse 42.3

## Konfiguracja interfejsów

### Dodanie bramy domyślnej
![W oknie Network Settings przechodzimy do zakładki Routing i w sekcji Routing Table dodajemy trase.](img/Konfiguracja%20interfejsow/1.png)

![Wpisujemy adres IP bramy domyślnej i nazwa urządzenia, czyli karty sieciowej](img/Konfiguracja%20interfejsow/2.png)

![Po dodaniu trasy widzimy ją w tabeli](img/Konfiguracja%20interfejsow/3.png)

### Zmiana nazwy serwera
![W oknie Network Settings przechodzimy do Hostname/DNS i wpisujemy statyczną nazwę hosta](img/Konfiguracja%20interfejsow/4.png)

### Wyłączenie interfejsu
![Przejdź do edycji ustawień interfejsu, następnie do zakładki **General** i w sekcji **Device Activation** zmień opcję **Activate Device** na **Never**](img/Konfiguracja%20interfejsow/5.png)

## Serwer HTTP

- ** Nazwa usługi:** apache2
- ** Nazwa pakietu:** yast2-http-server
- **   Domyślny właściciel:** wwwrun
- **  Grupa właściciela:** www
- **ﴘ Domyślny numer portu**: 80 (TCP)
- ** Katalog do plików konfiguracyjnych:** /etc/apache2
- ** Domyślna ścieżka strony**: /srv/www
- **  Link do dokumentacji: [kliknij tutaj](https://doc.opensuse.org/documentation/leap/reference/html/book-reference/cha-apache2.html)**

## Serwer FTP

- ** Nazwa usługi:** vsftpd
- ** Nazwa pakietu:** vsftpd lub yast2-ftp-server
- ** Plik konfiguracyjny:** /etc/vsftpd.conf
- **ﴘ Domyślne numery portów**: 20 (przesył danych), 21 (polecenia) (TCP)
- ** Domyślna ścieżka do udostępnionych plików**: /srv/ftp
- **  Link do dokumentacji: [kliknij tutaj](https://doc.opensuse.org/documentation/leap/reference/html/book-reference/cha-ftp.html)**

## Serwer DNS

- ** Nazwa usługi:** named
- ** Nazwa pakietu:** yast2-dns-server
- ** Plik konfiguracyjny:** /etc/named.conf
- **ﴘ Domyślne numery portów**: 53 (UDP i TCP)
- **  Link do dokumentacji: [kliknij tutaj](https://doc.opensuse.org/documentation/leap/reference/html/book-reference/cha-dns.html#sec-dns-bind)**

Przed nauką konfiguracji serwera DNS warto nauczyć się teorii, zestaw fiszek programu Anki: [kliknij tutaj](https://www.github.com/jozwikaleksander/inf02/flashcards/DNS.apkg).

## Serwer DHCP

- ** Nazwa usługi:** dhcpd
- ** Nazwa pakietu:** yast2-dhcp-server
- ** Plik konfiguracyjny:** /etc/dhcpd.conf
- **ﴘ Domyślne numery portów**: 67 (serwer) i 68 (klient) - UDP
- **  Link do dokumentacji: [kliknij tutaj](https://doc.opensuse.org/documentation/leap/reference/html/book-reference/cha-dhcp.html)**