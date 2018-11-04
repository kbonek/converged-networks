## Wstęp 
W sieci, w której wielu użytkowników rywalizuje o dostęp do pasma, zachodzi potrzeba priorytetyzacji pakietów w sieci.
Co raz to nowsze usługi w sieciach potrzebują stałego i wysokiego poziomu jakości połączenia.
Dotyczy to szczególnie usług działających w trybie czasu rzeczywistego, które są nieodporne na opóźnienia
i wymagają stałej szerokości pasma. Takie wysokie wymagania doprowadziły do powstania mechanizmów, które będą zapewniały
transmisję danych z zachowaniem pewnych gwarancji. Obecnie najpopularniejszą architekturą sieci, która pozwala na zapewnienie
ścisłych gwarancji QoS w sieciach IP jest architektura Diffserv.
### Model DiffServ
Jest to model oparty o architekturę usług zróżnicowanych, którego  głównym założeniem podczas tworzenia był wzrost 
skalowalności  w porównaniu do modelu IntServ. Architektura DiffServ nie wymaga sygnalizowania dla zestawienia połączenia.
Zapewnienie jakości usług polega na mechanizmie rozróżniania typu ruchu w sieci i odbywa się na poziomie klasy (grupy) połączeń,
a nie na poziomie pojedynczego połączenia
### Archtektura DiffServ
* **Agent Pasma (Bandwidth Broker)-** zarządza zasobami sieci, odpowiada za funkcje związane z konfiguracją routerów brzegowych 
oraz wykonywanie funkcji AC (Admision Control), czyli przyjmowanie albo odrzucanie nowych wywołań. 
Funkcja AC zapobiega stanom przeciążenia sieci oraz jest niezbędna w sieciach IP oferujących ścisłe gwarancje QoS.
* **Router brzegowy-** przydzielenie pakietu do klasy usług odbywa się w wejściowym ruterze brzegowym 
w chwili wejścia pakietu do domeny DiffServ.
* **Domena DiffServ-** zestaw ściśle związanych ze sobą węzłów. Domeny mogą ze sobą współpracować,
ale są również od siebie niezależne. Zbiór współpracujących ze sobą domen nazywa się region.
### Klasyfikowanie i oznaczanie pakietów
**Klasyfikacja pakietów** jest przeprowadzana na podstawie wartości jednego lub wielu pól nagłówka 
pakietu IP (np. adresu i numeru portu nadawcy czy identyfikatora protokołu transportowego) lub na podstawie wartości
punktu kodowego DSCP (Differantied Service Code Point) w nagłówku pakietu. Punkt kodowy ma wartość 6 bitów
i jest częścią jednobajtowego pola DS. W wersji 4 protokołu IP
wykorzystuje się do tego bajt ToS (Type of Service), natomiast w wersji 6 protokołu IP jest to bajt Traffic Class.
***BA (Behaviour Aggregate)-*** zespół pakietów z tym samym DCSP, pakiety te są tak samo traktowane w ramach domeny.

**Oznaczanie pakietów w routerach brzegowych** polega na ustawieniu odpowiedniej wartości pola DSCP w nagłówku pakietu. 
Oznaczanie może odbyć się bezpośrednio po przejściu przez mechanizm klasyfikacji bądź też po przejściu 
przez mechanizm monitorowania ruchu. W drugim przypadku wygląda to tak, że wartość pola zależy 
od przyporządkowania do odpowiedniego poziomu zgodności. Dzięki oznaczeniu pakietów mogą one w procesie 
kolejkowania być obsłużone z wyższym bądź niższym priorytetem. 
Oznaczenie wpływa również na obsługę pakietów w węzłach szkieletu sieci. 
### PHB (Per hop behaviour)
Sposób przesyłania pakietów przez routery szkieletowe określają reguły PHB (Per hop behaviour). 
Reguły te zdefiniowane są w każdym węźle dla każdej z obsługiwanych klas i określają sposób traktowania danej klasy 
ruchu rozpoznawanej na podstawie odpowiedniego pola DSCP.
#### Klasy usług
Odpowiednie dokumenty RFC definiują przypisanie odpowiednich wartości kodowych do poszczególnych klas.
* **Przekazywanie niesklasyfikowane (bez opcji klasyfikowania)**
* **Klasa EX(Expedited Forwarding) [RFC3246]** Cechuje się małymi opóźnieniami i małą zmiennością opóźnienia, 
ma również zagwarantowane pasmo. Wartość kodowa 101110.
* **Klasa AF(Assured Forwarding) [RFC2597]** Charakteryzuje się brakiem gwarancji wielkości opóźnienia. 
Gwarantuje tylko, że wielkość opóźnienia będzie zgodna z ustaleniami z prawdopodobieństwem nie niższym, 
niż zostało uzgodnione. Zdefiniowane są 4 klasy usług AF. Pakiety, które zostaną przypisane do danej klasy AF, 
nie mogą zmieniać kolejności. W ramach każdej klasy określono 3 poziomy prawdopodobieństwa odrzucenia pakietów. 
Poziomy te służą do priorytetyzacji pakietów w kolejce. W sytuacji przeciążenia sieci w pierwszej kolejności 
odrzucane zostają pakiety z najwyższą wartością prawdopodobieństwa odrzucenia. Wartość kodowa:

Prawdopodobieństwo odrzucenia pakietu | Klasa 1 | Klasa 2 | Klasa 3 | Klasa 4
------------ | ------------- | ----------- | ------------- | -------------
Niskie  | 001010 | 010010 | 011010 | 100010 
Średnie  | 001100 | 010100 | 011100 | 100100 
Wysokie  | 001110 | 010110 | 011110 | 100110 


