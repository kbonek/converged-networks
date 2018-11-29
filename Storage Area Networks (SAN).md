
## Opis

**SAN ( Storage Area Network )** — stanowi rozwiązanie architektoniczne dla podłączenia zewnętrznych urządzeń pamięci masowej, takich jak macierze dyskowe, biblioteki taśmowe, napędy optyczne do serwerów w taki sposób, aby system operacyjny rozpoznaje podłączone zasoby lokalne. SAN charakteryzują się świadczeniem tzw. sieciowych urządzeń blokowych (zwykle za pośrednictwem protokołów Fibre Channel, iSCSI lub AoE), podczas gdy sieci hurtowni danych (ang. Network Attached Storage, NAS) ukierunkowane na zapewnienie dostępu do przechowywanych na ich systemie plików danych za pomocą sieciowego systemu plików (NFS, SMB/CIFS, lub Apple Filing Protocol). Należy zwrócić uwagę, że kategoryczne rozdzielenie rodzaju "SAN — to tylko dyski sieciowe NAS — to tylko sieciowy system plików" jest sztucznym: wraz z pojawieniem się iSCSI zaczęło się wzajemne przenikanie technologii w celu zwiększenia elastyczności i ułatwienia ich stosowania. Na przykład, w 2003 roku NetApp już udzielały iSCSI na swoich NAS, a EMC i HDS — wręcz przeciwnie, chciano NAS-bramy do swoich SAN-tablic.


## Typy siec

Większość sieci pamięci masowej wykorzystuje protokół SCSI do komunikacji między serwerami i urządzeniami pamięci masowej na poziomie topologii magistrali . Ponieważ protokół SCSI nie jest przeznaczony do tworzenia pakietów sieciowych, protokoły niskiego poziomu są używane w sieciach pamięci masowej:

- [Protokół Fibre Channel](https://pl.wikipedia.org/wiki/Fibre_Channel/), transport SCSI przez Fibre Channel . Najczęściej używany protokół w tej chwili. Występuje w wersjach 1 -- Gbit / s, 2 Gbit / s, 4 Gbit / s, 8 Gbit / s, 10 Gbit / s, 16 Gbit / s, 20 Gbit / s.
- [iSCSI](https://pl.wikipedia.org/wiki/ISCSI/), transport SCSI przez [TCP / IP](https://pl.wikipedia.org/wiki/Model_TCP/IP/)  .
- iSER , transport iSCSI za pośrednictwem InfiniBand / RDMA .
- SRP , transport SCSI przez InfiniBand / RDMA
- FCoE , FCP / SCSI transport przez "czysty" Ethernet.
- FCIP i iFCP , FCP / SCSI hermetyzacja i transmisja w pakietach IP.
- HyperSCSI , transport SCSI przez Ethernet .
- Transport FICON przez Fibre Channel (używany tylko przez mainframe ).
- ATA przez Ethernet , ATA - transport przez Ethernet .

## Udostępnianie urządzeń pamięci masowej

Siłą napędową rozwoju sieci pamięciowych był gwałtowny rozwój informacji biznesowych (takich jak poczta e-mail , bazy danych i serwery plików o dużym obciążeniu), wymagających szybkiego dostępu do urządzeń dyskowych na poziomie bloku. Wcześniej przedsiębiorstwo posiadało "wyspy" wysokowydajnych macierzy dyskowych SCSI . Każda taka tablica została przydzielona dla konkretnej aplikacji i jest widoczna jako liczba "wirtualnych dysków twardych " ( LUN ).

Pamięć sieciowa pozwala łączyć te "wyspy" z szybką siecią. Ponadto, bez użycia technologii transportu SCSI, niemożliwe jest zorganizowanie klastrów odpornych na uszkodzenia, w których jeden serwer łączy się z dwoma lub więcej macierzami dyskowymi znajdującymi się w dużej odległości od siebie w przypadku klęsk żywiołowych.

Sieci pamięci masowej pomagają poprawić efektywność wykorzystania zasobów w systemach pamięci masowej, ponieważ zapewniają możliwość przydzielenia dowolnego zasobu do dowolnego węzła sieciowego.

Nie zapomnij o urządzeniach do tworzenia kopii zapasowych, które są również podłączone do sieci SAN. W chwili obecnej istnieją zarówno przemysłowe biblioteki taśmowe (na kilka tysięcy taśm) od wiodących marek, jak i low-endowe rozwiązania dla małych firm. Sieci pamięci masowych pozwalają na podłączenie kilku dysków takich bibliotek do jednego hosta, zapewniając w ten sposób przechowywanie danych dla kopii zapasowych od setek terabajtów do kilku petabajtów.

## Porównanie technologii wymiany danych
Czasami porównują SAN i NAS , mówiąc w rzeczywistości o różnicy między dyskiem sieciowym i systemem plików sieciowych - kto służy systemowi plików, który przechowuje dane .

W przypadku dysku sieciowego (również "urządzenie blokowe", ang. block device ):

- wymiana danych z nią w sieci odbywa się w blokach, tak jak w przypadku lokalnego dysku SCSI lub [SATA](https://pl.wikipedia.org/wiki/Serial_ATA/) ;
- system plików, jeśli jest potrzebny, jest tworzony i zarządzany przez klienta i z reguły jest przez niego używany.
W przypadku sieciowego systemu plików ("shared / shared access" - nie przechowuje, ale tylko przesyła dane):

- dane są wymieniane za pośrednictwem sieci, wykorzystując koncepcje " plików " i " katalogów wyższego poziomu" odpowiadające obiektom "prawdziwego" FS na dyskach fizycznych (lub logiczne w przypadku RAID , LVM );
- Ten system plików jest tworzony i utrzymywany w systemie zdalnym i może być jednocześnie używany do odczytu i zapisu przez wielu klientów.

![alt text](https://github.com/IhnatekoYehor/converged-networks/blob/master/SAN/1.png)

## Topologia sieci

### Struktura pojedynczego przełącznika
**Struktura pojedynczego przełącznika (ang.Single-Switch Fabric)** - składa się z serwera i systemu pamięci Fibre Channel . Zazwyczaj ta topologia jest podstawowa dla wszystkich standardowych rozwiązań - inne topologie są tworzone poprzez łączenie jednoprzyciskowych komórek.

![alt text](https://github.com/IhnatekoYehor/converged-networks/blob/master/SAN/Untitled%20Diagram%200.png)

### Struktura drzewa lub kaskady 
**Struktura kaskadowa ( ang. Cascade fabric )** - zestaw komórek, których przełączniki są połączone z drzewem za pomocą połączeń między przełącznikami **( ang. Inter-Switch link, ISL )**. Podczas inicjalizacji sieci przełączniki wybierają "wierzchołek drzewa" ( główny przełącznik - **principal switch**) i przypisują status **"upstream"** (w górę) lub **"downstream"** (w dół) do numerów ISL, w zależności od tego, czy to łącze prowadzi do głównego przełącznika lub na peryferie.

![alt text](https://github.com/IhnatekoYehor/converged-networks/blob/master/SAN/Untitled%20Diagram%201.png)

### Krata 

**Krata** (ang. meshed fabric) - zestaw komórek, z których każdy jest połączony ze wszystkimi innymi. Jeśli jedna (i wiele kombinacji - i więcej) połączeń ISL nie, połączenie z siecią nie zostanie zerwane. Wadą jest duża redundancja połączeń.

![alt text](https://github.com/IhnatekoYehor/converged-networks/blob/master/SAN/Untitled%20Diagram%202.png)

### Ring

**Ring** ( ang. born ring fabric ) - praktycznie powtarza schemat topologii siatki . Korzyści obejmują mniej połączeń ISL

![alt text](https://github.com/IhnatekoYehor/converged-networks/blob/master/SAN/Untitled%20Diagram%203.png)

### Centralnie rozprowadzane
**Centralnie rozproszona topologia** ( ang. core-edge fabric ) - praktycznie powtarza schemat topologii sieci . Korzyści obejmują mniejszą nadmiarowość połączeń i wysoki stopień odporności na uszkodzenia
![alt text](https://github.com/IhnatekoYehor/converged-networks/blob/master/SAN/Untitled%20Diagram%204.png)

## Produktywność 
Pojawienie się nowych zaawansowanych technologicznie materiałów przyczynia się do wzrostu wydajności sieci opartych na technologii Fibre Channel i Ethernet. Już istnieją przełączniki obsługujące prędkość transmisji 10Gbit/s.

Żródła:
- https://en.wikipedia.org/wiki/Storage_area_network
- https://searchstorage.techtarget.com/definition/storage-area-network-SAN
- https://www.netapp.com/us/info/what-is-storage-area-network.aspx
