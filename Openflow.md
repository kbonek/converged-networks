Protokół OpenFlow
---
### Definicja
OpenFlow to protokół komunikacji dzięki któremu użytkownik posiada zdalny dostęp do płaszczyzny danych urządzenia sieciowego.

### Powstanie protokołu OpenFlow
Koncepcją powstania tego protokołu było wsparcie budowy programowalnych sieci komputerowych (ang. Software-defined network, SDN) za sprawą standaryzacji oraz dostosowaniu do możliwości danych urządzeń. Protokół ten powstał dzięki Open Networking Foundation. Organizacja ta zajmuje się między innymi promowaniem oraz wdrażaniem oprogramowania, które jest definiowane przez sieć SDN. ONF definiuje OpenFlow jako pierwszy interfejs komunikacyjny pomiędzy warstwami sterowania, a przekazywania architektury SDN. Dzięki temu mamy bezpośredni dostęp wraz z kontrolowaniem warstwy przesyłu w urządzeniach sieciowych takich jak przełączniki czy routery (fizyczne oraz wirtualne). Protokół OpenFlow jest niezbędny aby przenieść kontrolę sieci z przełączników sieciowych, które są zastrzeżone, do takiego oprogramowania sterującego, które jest otwarte, jak również zarządzane lokalnie.

### Zasada działania:
Korzystając z protokołu OpenFlow mamy możliwość dostępu do bogatego zestawu narzędzi, które pozwalają na zaawansowaną infrastrukturę przepływu pakietów. Optymalizacja transmisji jest przydatna w celu zapewnienia odpowiedniego pasma, uniknięcia wszelkich opóźnień oraz liczby węzłów, przez które przechodzą pakiety. Wyżej wymieniony protokół, dzięki kontroli nad przepływem ruchu oraz jego separacją, pozwala na wirtualizację sieci prywatnych. Administratorzy opierając się o protokół OpenFlow mogą badać nowe rozwiązania, rozbudowywać, modyfikować czy testować konkretną sieć komputerową wykorzystując do tego środowiska produkcyjne. Zaletą w tym przypadku jest również fakt, że takie działania nie zakłócają normalnego funkcjonowania sieci komputerowej.

##### Komunikacja
Protokół OpenFlow ma za zadanie rozdzielić płaszczyznę danych od płaszczyzny sterowania przełączników sieciowych i routeróww warstwie sieci modelu OSI. Płaszczyzna danych to w dużym skrócie przełącznik OpenFlow, natomiast płaszczyznę danych reprezentują kontrolery OpenFlow. W ramach centralizacji funkcji sterowania każdy kontroler steruje wieloma przełącznikami i odwrotnie tzn. dany przełącznik może sterować wieloma kontrolerami. Takie rozwiązanie ma na celu uzyskanie dużej odporności na awarie.

##### Sterowanie
Sterowanie oznacza to, że kontroler określa za pomocą kanału OpenFlow w jaki sposób przełącznik ma przetwarzać pakiety, które otrzymuje. Dzięki temu, że przełączniki samodzielnie przetwarzają pakiety kontrolery mogą wykorzystywać zaawansowane algorytmy nie tracąc przy tym wysokiej wydajności przetwarzania pakietów. OpenFlow oparty jest na protokole TCP. Przy użyciu kontrolera dodawane są odpowiednie reguły do tabel przepływów, które znajdują się w przełącznikach OpenFlow. Taki kontroler może mieć postać od prostego mechanizmu dzięki któremu będą dodawane statyczne wpisy do pamięci przełącznika po obszerny program w którym ruchy przepływów będą zależne od określonych wymagań. Kontrolery wykorzystują port 6653 dla tych przełączników, które chcą ustanowić połączenie. Wcześniejsze wersje wyżej wymienionego protokołu wykorzystywały port 6632.

##### Przepływ
Zalecenia wobec przekazywania pakietów przez przełączniki występują w postaci pozycji przepływu (flowentry). Natomiast czynności takie jak: tworzenie oraz modyfikowanie pozycji przepływu zlecane z pozycji kontrolera są określane jako podstawowe zastosowanie protokołu OpenFlow. Pozycje te wspierają przekazywanie strumienia pakietów (ich przepływ). Wszystkie zgrupowane pozycje stanowią tzw. tabelę przepływów (flowtable). Tabela ma swoje zastosowanie podczas nadejścia nowego pakietu do przełącznika. Przełącznik wówczas sprawdza właściwą tabelę, aby móc wykorzystać najlepszą pojedynczą pozycję przepływu. Po wybraniu najkorzystniejszej pozycji przełącznik wykonuje na pakiecie instrukcje określone w wybranej wcześniej pozycji. Wybór pozycji przepływu wykonywany jest dzięki porównaniu wartości pól zawartych w nagłówku pakietu z wartościami określanymi w danej pozycji. Pozycja przepływu określa konkretnie jakie wartości muszą posiadać wybrane pola w nagłówku pakietu, tak aby dopasowanie było możliwe. W tabelach zawarta jest również informacja co przełącznik powinien wykonać w przypadku braku dopasowania pakietu do jakiejkolwiek z pozycji w tabeli.

##### Akcje
Przetwarzanie pakietów wykonywane przy użyciu przełącznika jest określanie przy pomocy akcji. Najważniejsza rzecz to przesłanie pakietu do danego portu przełącznika. Akcje potrafią również określać odrzucenie pakietu oraz jego modyfikację (zmiana wartości pól). Do czynności można zaliczyć również takie działania jak definiowanie instrukcji sterowania przebiegiem przetwarzania pakietu.

### Wsparcie przez producentów urządzeń sieciowych
Wielu producentów routerów i przełączników takich jak: Alcatel-Lucent, Cisco, Huawei, IBM, Hewlett-Packard, MikroTik postanowiła, że będą wspierać oraz obsługiwać protokół OpenFlow na swoich urządzeniach. Protokół ten używany jest pomiędzy przełącznikiem, a kontrolerem na bezpiecznym kanale.

### Rozwój
28 luty 2011r. ONF wydaje wersję 1.1 protokołu OpenFlow
maj 2011r. firma Marvell i Larch Networks w oparciu o protokół OpenFlow wprowadza w pełni funkcjonalne przełączanie na stosie kontroli sieci Marvell oraz rodzinie procesów pakietowych Prestera. Indiana University w powiązaniu z Open Networking Foundation uruchamia laboratorium SDN, aby móc przetestować współpracę różnych produktów sieciowych z produktami OpenFlow 
grudzień 2011r. zarząd ONF zatwierdza wersję 1.2 i publikuje ją w lutym 2012r.
luty 2012r. Big Switch Networks wydaje Project Floodlight - oprogramowanie Open Source OpenFlow Controller oparte na licencji Apache. 
kwiecień 2012r. Google przedstawiła oraz opisała przeprojektowanie sieci wewnętrznej firmy na przestrzeni ostatnich lat, tak aby móc działać w oparciu o protokół OpenFlow ze znaczną poprawą wydajności
czerwiec 2012r. Infoblox publikuje LINC - oprogramowanie Open Source zgodne z wersją 1.2 oraz 1.3 protokołu OpenFlow. HP potwierdza wsparcie dla protokołu wobec 16 produktów 
listopad 2012r. firma Big Switch Networks wydaje komercyjny pakiet SDN Suite w oparciu o protokół OpenFlow, którego zadaniem jest możliwość konfiguracji wirtualnych przełączników
styczeń 2013r. firma NEC przedstawiła wirtualny przełącznik dla systemu Windows Server 2012, który ma za zadanie wprowadzenie wirtualizacji sieciowej na podstawie działania OpenFlow dla środowisk firmy Microsoft
wrzesień 2016r. ONF wydaje wersję 1.6 - jednak dostępna tylko dla członków fundacji
Obecnie ogólnodostępna wersja to 1.5.1

### Podsumowując
Z powodu braku otwartego standardu dzięki któremu byłby dostęp do płaszczyzny danych dzisiejsze urządzenia sieciowe podobne są do systemów klasy mainframe. Z pomocą przychodzi wyżej wymieniony protokół którego zadanie polega na przeniesieniu funkcji sterowania zamkniętych urządzeń producentów do lokalnie zarządzającego oprogramowania otwartego. Oznacza to, że protokół OpenFlow pozwala aby trasa pakietów z pomocą sieci telekomunikacyjnej była definiowana przy użyciu oprogramowania działającego w kontrolerze.  Odseparowanie sterowania od przekazywania pakietów daje możliwość bardziej zaawansowanego zarządzania ruchem niż w przypadku wykorzystania tylko  mechanizmów ACL (list kontroli dostępu) czy protokołów trasowania. 

### Źródła:

[Prezentacja](https://docplayer.pl/1782294-Protokol-openflow-piotr-gierz-architekt-rozwiazan-w-sluzbie-software-defined-networks-sdn.html)

[Prezentacja](http://docplayer.pl/66664051-Architektura-sieci-sterowanych-programowo-protokol-openflow-sieci-sterowane-programowo-grzegorz-rzym.html)

[Artykuł](https://www.computerworld.pl/news/OpenFlow-i-sieci-sterowane-programowo,374742.html)

[Wikipedia](https://en.wikipedia.org/wiki/OpenFlow)
