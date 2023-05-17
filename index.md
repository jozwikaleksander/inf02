# 1.Diagnostyka systemu Linux

## 1.1. lsblk
Podaje informacje na **temat  dysku twardego**. Aby wyświetlić konkretne
informacje skorzystaj z **przełącznika -o** i podaj nazwy kolumn.

### 1.1.1. Najważniejsze kolumny

- **NAME** - nazwa urządzenia
- **FSTYPE** - system plików
- **MODEL** - model urządzenia
- **SERIAL** - numer seryjny
- **SIZE** - pojemność urządzenia

**Przykład**

![Polecenie lsblk](img/1.1.png)

## 1.2. lscpu
Podaje informacje o **  procesorze**.

**Niektóre z informacji które możemy znaleźć:**

- Nazwa
- Taktowanie
- Liczba rdzeni
- Wielkość pamięci L1 Cache
- Wielkość pamięci L2 Cache

**Przykład**

![Polecenie lscpu](img/1.2.png)

## 1.3. lspci
Wyświetla urządzenia PCI w tym ** kartę graficzną** i ** kartę sieciową**.

### 1.3.1. Karta graficzna

![Polecenie lspci](img/1.3.png)

**Użyta komenda:** lspci -v | more

### 1.3.2. Karta sieciowa

![Polecenie lspci](img/1.3.2.png)

**Użyta komenda:** lspci -v | more

## 1.4. Plik /etc/os-release
Podaje **nazwę** i **wersje systemu operacyjnego**.

**Przykład**

![Plik /etc/os-release](img/1.4.png)

Aby wyświetlić zawartość pliku korzystam z polecenia **cat**.

## 1.5. uname
Podaje m.in. ** wersję jądra (przełącznik -r)** i ** architekturę (przełacznik -p)**.

### 1.5.1. Wersja jądra

![uname -r](img/1.5.1.png)

### 5.2. Architektura

![uname -p](img/1.5.2.png)

## 1.6. dmidecode
Dostarcza informacji na temat m.in. **pamięci RAM, procesorze, płycie głównej**. Aby wybrać konkretne urządzenie skorzystaj z przełącznika **-t**.

### 1.6.1. Pamięć RAM
![dmidecode -t memory](img/1.6.1.png)

**Użyta komenda:** dmidecode -t memory

### 1.6.2. Płyta główna
![dmidecode -t baseboard](img/1.6.2.png)

**Użyta komenda:** dmidecode -t baseboard

## 1.7. top
Wyświetla **procesy** oraz **informacje o zasobach komputera**.

**Przykład**
![top](img/1.7.1.png)

**Informacje które możemy odczytać to między innymi:**

- liczba uruchomionych procesów
- liczba uśpionych procesów
- ilość wolnej pamięci RAM
- ilość używanej pamięci RAM

## 1.8. du
Wyświetla rozmiar katalogu. Aby wygodnie wyświetlić wyniki skorzystaj
z przełączników **-h** i **-s**.

### 1.8.1. Rozmiar katalogu /etc
![du -sh /etc](img/1.8.1.png)

**Użyta komenda:** du -sh /etc

### 1.8.2. Rozmiar katalogu /var

![du -sh /var](img/1.8.2.png)

**Użyta komenda:** du -sh /var

## 1.9. hostname
![hostname](img/1.9.png)

Wyświetla nazwę hosta.

## 1.10. Plik /etc/passwd
Zawiera listę wszystkich użytkowników wraz z ich UID, GID, ścieżką do katalogu domowego i używaną powłoką.

**Przykład:**

![cat /etc/passwd](img/1.10.1.png)

**<span style="color:var(--red-color)">1000 - UID</span>**

**<span style="color:var(--green-color)">100 - GID</span>**

Jeżeli nie pamiętasz, które jest które użyj polecenia [id](#id).

## 1.11. id
![id admin](img/1.11.png)

Wyświetla **UID** i **GID** określonego użytkownika.