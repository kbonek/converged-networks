
# DAS (Direct Attached Storage) 

Architektura Storage – okazuje się, że to uniwersalne słowo, które praktycznie na stałe weszło do polskiego słownika informatyka, ma bardzo wiele znaczeń. Oznacza tyle, co gromadzenie i przechowywanie danych, zazwyczaj w dużej ilości. 
Nieważne czy są to informacje dotyczące finansów, sprzedaży, marketingu czy korespondencji email. Stały dostęp do baz danych jest podstawowym warunkiem prowadzenia biznesu. W opracowaniu strategii przechowywania danych, jest wiele czynników do rozważenia, np.: wymagana pojemność nośników, dostępny budżet, kwalifikacje pracowników, wydajność urządzeń i możliwość ich ewentualnej rozbudowy. 

Bezpośrednio podłączana przestrzeń dyskowa (Direct Attached Storage) znana pod skróconą nazwą DAS, była pierwszym rodzajem platformy sieciowej służącej do przechowywania danych. Na dobrą sprawę nadal jest w powszechnym użyciu. Jak sama nazwa mówi, jest to rozwiązanie gdzie dodatkowa pamięć masowa jest bezpośrednio podłączona do serwera. Rozwiązanie to może obejmować jeden lub więcej dysków połączonych z serwerem, gdzie dzięki odpowiedniemu kontrolerowi HBA (Host Bus Adapter) system może zostać skonfigurowany w układzie RAID.

DAS jest rozwiązaniem, w którym każdy serwer posiada dedykowaną pamięć masową podłączoną bezpośrednio poprzez interfejs SCSI lub FC. Operacje odczytu/zapisu związane m.in. z kopiami bezpieczeństwa, odtworzeniami czy archiwizacją przeprowadzane są bezpośrednio na podłączony zasób. Zasób ten nie jest współdzielony a dostęp do niego posiada tylko serwer do którego jest on podpięty.

Jedną z zalet  pamięci DAS jest jej niski koszt początkowy. Pierwsza inwestycja w serwer i dodatkową pamięć masową jest w stanie zaspokoić potrzeby małych organizacji przez pewien czas. Jednak w momencie gdy coraz więcej danych jest dodawanych i zapotrzebowanie na dostępną pamięć magazynową wzrasta, to praca serwera musi zostać wstrzymana w celu instalacji dodatkowych dysków.
Oprócz tego rozwój systemów DAS wymaga specjalistycznej wiedzy informatycznej, co oznacza dodatkowy koszt dla małego przedsiębiorstwa w postaci zatrudnienia nowego pracownika lub skorzystania z usług konsultanta.
Główną wadą  przechowywania danych na nośnikach DAS jest ich mała skalowalność (możliwość rozbudowy) z powodu ograniczonej liczby dysków, jaką może obsługiwać kontroler HBA.  Oprócz tego w platformach typu DAS użytkownicy muszą bezpośrednio łączyć się z serwerem w celu uzyskania dostępu do zgromadzonych na nim danych. Co za tym idzie, w momencie gdy serwer musi zostać wyłączony np. w celu konserwacji, przeglądu, zainstalowania nowego oprzyrządowania, aktualizacji systemu operacyjnego lub w przypadku zainfekowania wirusem, użytkownicy nie będą mieli dostępu do danych. 
Serwery oprócz swojej podstawowej funkcji udostępniania, często używane są również do zarządzania różnymi aplikacjami takimi jak email, pakiety rachunkowe, aplikacje bazodanowe. Rozwiązanie typu DAS jest idealne dla aplikacji, dla których system operacyjny serwera umożliwia dostęp użytkownikom zarówno na poziomie blokowym jak i z poziomu plików. Jednak  jego skuteczność może okazać się problemowa, kiedy serwer prowadzi kilka różnorodnych operacji poza samym udostępnianiem plików.
Bazujące na serwerach urządzenia DAS mogą być dobrą propozycją dla małych przedsiębiorstw, których działanie opiera się wykorzystaniu tylko jednego lub kilku serwerów. Jednak gdy ilość serwerów wzrasta, a co za tym idzie również i złożoność zarządzania dostępnymi przestrzeniami dyskowymi, można będzie zaobserwować tendencją wzrostową kosztów IT w przedsiębiorstwie.
DAS jest jednym z pierwszych rozwiązań na rynku pamięci masowych i od dłuższego czasu zastępowany rozwiązaniami typu NAS czy SAN.
 

### Autorzy:
Dawid Bielak, Miłosz Szymaszek, Dawid Jabłoński


### Źródło:
* <https://www.s4e.pl/das-nas-san-storage-nie-jedno-ma-imie/>
* <https://www.backupacademy.pl/das-vs-nas/>
* <https://en.wikipedia.org/wiki/Direct-attached_storage>
* <https://www.wanstor.com/business-direct-attached-storage-das.htm>
* <http://www.apexmicrosystems.com/?page_id=518>

