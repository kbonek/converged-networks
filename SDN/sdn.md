# Koncepcja SDN

## Ogólna definicja
SDN (Software Defined Networking) - koncepcja architektury sieci polegająca na wydzieleniu z urządzenia sieciowego inteligentnego, tj. zarządczo-sterującego komponentu i pozostawienie dla tego urządzenia wyłącznie zadań polegających na przesyłaniu danych w pakietach pomiędzy portami.

## Co SDN zmieni w sieciach
* Sieci przestaną być statyczne, możliwe będzie dynamiczna zmiana zachowania sieci
* Dynamiczne policy
* Szybkość dostarczania nowych aplikacji
* Rozdzielenie, forwarding plane, control plane, managment plane. Nie chodzi tutaj o rozdzielenie na osobne karty lecz rozdzielenie geograficzne.
* Decentralizacja zarządzania.

## Dlaczego SDN jest lepszy od tradycyjnej statycznej sieci?
Mówiąc ogólnie, SDN może zapewnić elastyczność i dynamikę w bardziej kompleksowy sposób, Nie wszyscy potrzebują SDN, zwłaszcza jeśli ich sieć jest niewielka lub stosunkowo statyczna, ale ponieważ IT często stara się robić więcej za mniej, SDN może pomóc, na przykład, poprzez zwiększenie automatyzacji sieci IT.

Zasadniczo SDN jest architekturą szkieletową, która może być wykorzystywana dla wielu korzyści, w tym bardziej sprawnego i segmentowanego bezpieczeństwa. Wielu producentów nie dostarcza produktów SDN, ale ich rozwiązania integrują się z istniejącymi i przyszłymi rozwiązaniami SDN. Ponieważ różni dostawcy różnie podchodzą do wdrażania SDN, integracja z produktami stron trzecich i ekosystemem są ważne, gdy rozmawiamy o SDN. 

Wiele osób z branży IT zauważyło, że wirtualizacja serwerów, w szczególności VMware ESX, przekształciła centrum danych w ciągu ostatniej dekady. Zdefiniowana programowo sieć (SDN) lub wirtualizacja sieci odnosi się do różnych technologii sieciowych o podobnych zasadach, które były stosowane do wirtualizacji serwerów, tj. Abstrakcji, enkapsulacji itp. - a także są teraz stosowane do innych warstw infrastruktury podobnie jak pamięć masowa i bezpieczeństwo. Pakiety sieciowe i przepływy nadal podlegają tym samym podstawowym siedmiowarstwowym modelom OSI, ale infrastruktura taka jak przełączniki i routery mogą być wirtualne, a obiekty sieciowe, takie jak adresy IP, MAC, porty i przepływy, są odłączane i niezależne od sieci fizycznej.
Filozofia związana z SDN to umożliwienie połączenia świata aplikacji z światem sieciowym. Poprzez ustandaryzowaną architekturę. 

rozproszenie infrastruktury sieciowej, zarządzania i aplikacji

## Idealny przykład użycia SDN:
Aplikacja chcąca wykonać backup sprawdzi jak bardzo obciążona jest sieć i czy wykonanie backupu nie wpłynie negatywnie na stabilność sieci.  Czyli w skrócie bezpośredni dostęp aplikacji do informacji o sieci.

## SDN w Centrach danych
Tradycyjna infrastruktura sieciowa jest dość mocno skoncentrowana na rozwiązaniach sprzętowych. Jednakże, od kilku lat adopcja wirtualnych urządzeń sieciowych i rosnące zainteresowanie centrum danych zdefiniowanych programowo (eng. software-defined data center – SDDC) prowadzi do coraz częstszego opierania funkcjonalność sieci na oprogramowaniu. I tak, jeszcze kilka lat temu stosowane urządzenia sieciowe, takie jak kontrolery optymalizacji sieci WAN czy też kontrolery ADC (Application delivery controllers) to były przede wszystkim rozwiązania sprzętowe. Tym samy funkcje takie jak szyfrowanie / deszyfrowanie, czy też ruch oparty na protokole TCP odbywa się w zaprojektowanym do tego celu rozwiązaniu sprzętowym. Konieczność podniesienia elastyczności organizacji powoduje, że obecnie coraz więcej firm korzysta z funkcji takich kontrolerów, dzięki oprogramowaniu działającym na serwerze lub maszynie wirtualnej.
Centrum danych zdefiniowane przez oprogramowanie może być rozumiane jako przeciwieństwo wcześniej opisanej tradycyjnej sieci. Jednym z kluczowych cech charakterystycznych takiego centrum danych jest to, że jego cała infrastruktura jest zwirtualizowana i dostarczana w postaci usługi. Ponadto zautomatyzowana kontrola aplikacji i usług w centrum danych jest zapewniona poprzez system zarządzania oparty na określonych politykach.

##Podsumowanie
Warto również nadmienić że SDN to nie OpenFlow, OpenFlow zajmuje sie tylko przełącznikami, SDN ma zajmować się, integrować przełączniki, routery, firewalle, aplikacje sieciowe. Postęp w obszarze wirtualizacji firmowych środowisk komputerowych spowodował, że na sieć spadła realizacja założeń firmowego cloud computingu. Dynamiczny charakter usług świadczonych w chmurze wymaga nowego poziomu elastyczności i skalowalności, który często wykracza poza możliwości dzisiejszych centrów przetwarzania danych. Zmiana zakładająca przejście do SDN obejmuje programowalność i elastyczność sieci, umożliwiając jej tym samym sprostanie potrzebom i wymaganiom współczesnego biznesu.

Źródła:
Wikipedia
Prezentacje dotyczące SDN z konferencji PLNOG 10 i 12
Prezentacje dotyczące wdrożenia Fortinet w sieci SDN
https://itwiz.pl/sdn-oprogramowanie-na-pierwszym-planie/
