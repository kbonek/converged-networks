
## Opis

**SAN ( Storage Area Network )** — stanowi rozwiązanie architektoniczne dla podłączenia zewnętrznych urządzeń pamięci masowej, takich jak macierze dyskowe, biblioteki taśmowe, napędy optyczne do serwerów w taki sposób, aby system operacyjny rozpoznaje podłączone zasoby lokalne.
SAN charakteryzują się świadczeniem tzw. sieciowych urządzeń blokowych (zwykle za pośrednictwem protokołów Fibre Channel, iSCSI lub AoE), podczas gdy sieci hurtowni danych (ang. Network Attached Storage, NAS) ukierunkowane na zapewnienie dostępu do przechowywanych na ich systemie plików danych za pomocą sieciowego systemu plików (NFS, SMB/CIFS, lub Apple Filing Protocol).
Należy zwrócić uwagę, że kategoryczne rozdzielenie rodzaju "SAN — to tylko dyski sieciowe NAS — to tylko sieciowy system plików" jest sztucznym: wraz z pojawieniem się iSCSI zaczęło się wzajemne przenikanie technologii w celu zwiększenia elastyczności i ułatwienia ich stosowania. Na przykład, w 2003 roku NetApp już udzielały iSCSI na swoich NAS, a EMC i HDS — wręcz przeciwnie, chciano NAS-bramy do swoich SAN-tablic.

## Typy siec

SAN-Switch Qlogic SANbox 5600 z podłączonymi do niego optyczne złączkami Fibre Channel.
Większość sieci przechowywania danych wykorzystuje protokół SCSI do komunikacji między serwerami i urządzeniami do przechowywania danych na poziomie opon topologii. Tak jak protokół SCSI nie jest przeznaczony do tworzenia pakietów sieciowych w sieciach przechowywania danych są używane protokoły niskiego poziomu:
- Fibre Channel Protocol (FCP), transport SCSI przez Fibre Channel. Najczęściej stosowany obecnie protokół. Istnieje w wersjach 1 Gbit/s, 2 Gbit/s, 4 Gbit/s, 8 Gbit/s, 10 Gbit/s, 16 Gbit/s, 20 Gbit/s.
- iSCSI, transport SCSI przez TCP/IP.
- iSER, transport iSCSI przez InfiniBand / RDMA.
- SRP, transport SCSI przez InfiniBand / RDMA
- FCoE, transport FCP/SCSI na "czystego" Ethernet.
- FCIP i iFCP, hermetyzacja i wysyłanie FCP/SCSI w pakietach IP.
- HyperSCSI, transport SCSI przez Ethernet.
- FICON transport przez Fibre Channel
- ATA over Ethernet, transport ATA za pośrednictwem sieci Ethernet.

## Wspólne korzystanie z urządzeń pamięci masowej

Siłą napędową dla rozwoju sieci pamięci masowej stał się gwałtowny wzrost ilości informacji biznesowych (takich jak e-mail, bazy danych i szczególnie wysoko obciążone serwery plików), które wymagają szybkiego dostępu do obudów urządzeń na poziomie blokowym. Wcześniej w zakładzie powstawały "wyspy" o wysokiej wydajności macierzy dyskowych SCSI. Każda taka tablica została przydzielona do konkretnej aplikacji i widać jak mu pewną ilość "wirtualnych dysków twardych" (LUN'ów).
Sieć pamięci masowej pozwala połączyć te "wyspy" środkami szybki sieci. Również bez użycia technologii SCSI transportu nie da się zorganizować odporne klastry, w których jeden serwer łączy się z dwoma i więcej obudów tablic, znajdujących się w dużej odległości od siebie, na wypadek klęsk żywiołowych.
Sieci pamięci masowej pomagają zwiększyć efektywność wykorzystania zasobów pamięci masowej, ponieważ dają możliwość zaznaczyć dowolny zasób każdego węzła sieci.
Nie należy zapominać o urządzeniach do tworzenia kopii zapasowych, które również łączą się z SAN. W tej chwili istnieją jako przemysłowe, biblioteki taśmowe (na kilka tysięcy taśm) od wiodących marek, jak i low-end rozwiązania dla małych firm. Sieci pamięci masowych umożliwia podłączenie do jednego hosta kilku napędów takich bibliotek, zapewniając w ten sposób repozytorium danych do tworzenia kopii zapasowej od setek terabajtów do wielu petabajtów.

## Porównanie technologii wymiany danych

Czasami porównują SAN i NAS, mówiąc właściwie o różnicy między dyskiem sieciowym i sieciowy PS — która polega na tym, kto obsługuje system plików, widget, który przechowuje dane.
W przypadku dysku sieciowego (również "urządzenia blokowego", ang. block device):
- komunikacja z nim w sieci odbywa się blokami podobnie, jak i z lokalnym SCSI lub SATA-dysk;
- system plików, jeśli jest potrzebna, tworzony i zarządzany przez klienta i zazwyczaj służy im jeden.

W przypadku sieciowego systemu plików ("zasobów z łącznym/rozdzielonym dostępem" — nie przechowuje, a tylko przekazuje dane):
- komunikacja w sieci odbywa się z zastosowaniem bardziej endowych pojęć "plik" i "katalog", odpowiednich obiektów podlegających "prawdziwej" FS na dyskach fizycznych (lub logicznych na nich w przypadku stosowania RAID, LVM);
- ten system jest tworzony i obsługiwany w ramach systemu zdalnego, przy tym może jednocześnie służyć do odczytu i zapisu wielu klientów.

![alt text](https://github.com/IhnatekoYehor/converged-networks/blob/master/SAN/1.png)

## Topologia sieci

### Struktura pojedynczego przełącznika
**Struktura pojedynczego przełącznika (ang.Single-Switch Fabric)** - składa się z jednego przełącznika Fibre Channel, serwerów i systemów pamięci masowej. Zazwyczaj ta topologia jest bazową dla wszystkich standardowych rozwiązań.

![alt text](https://github.com/IhnatekoYehor/converged-networks/blob/master/SAN/1.jpg)

### Drzewo lub Kaskadowego struktura

**Kaskadowy struktura (ang. cascaded fabric)** — zestaw komórek, przełączniki których łączą w drzewo z pomocą między zmianami połączeń **(ang. Inter-Switch link, ISL)**. Podczas inicjalizacji sieci przełączniki wybierają "wierzchołek drzewa" **(ang. principal switch, główny przełącznik)** i przeznaczają ISL'am status "upstream" (w górę) lub "downstream" (w dół) w zależności od tego, czy prowadzi ten link w stronę głównego switcha lub na peryferie.

![alt text](https://github.com/IhnatekoYehor/converged-networks/blob/master/SAN/2.jpg)

### Pierścień

**Pierścień (ang. ring fabric)** — praktycznie powtarza schemat topologii kraty. Wśród zalet — wykorzystanie mniejszej ilości połączeń ISL

![alt text](https://github.com/IhnatekoYehor/converged-networks/blob/master/SAN/4.jpg)

### Europy środkowo-rozproszona

**Europy środkowo-rozproszona topologia (ang. core-edge fabric)** — praktycznie powtarza schemat topologii kraty. Wśród zalet — mniejsza nadmiarowość połączeń i wysoki stopień odporności na uszkodzenia.

![alt text](https://github.com/IhnatekoYehor/converged-networks/blob/master/SAN/5.png)

## Wydajność
Pojawienie się nowych zaawansowanych technologicznie materiałów przyczynia się do wzrostu wydajności sieci opartych na technologii Fibre Channel i Ethernet. Już istnieją przełączniki obsługujące prędkość transmisji 10Gbit/s. Służy do tego nowy typ radia — XFP, a także światłowód w standardzie ОМ3. Przyrost prędkości transmisji przyczynia się i to, że przełączniki mogą zbierać na Inter Switch Link'ach trank gupy z kilku portów. Przełączniki "SilkWorm" od Brocade mogą zbierać trank z ośmiu linków. Tranków może być kilka, jeśli występuje taka potrzeba.

Żródła:
- https://en.wikipedia.org/wiki/Storage_area_network
- https://searchstorage.techtarget.com/definition/storage-area-network-SAN
- https://www.netapp.com/us/info/what-is-storage-area-network.aspx
