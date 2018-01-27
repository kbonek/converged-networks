# **Systemy RAID**

Macierz dyskowa RAID składa się najczęściej z kilku dysków fizycznych łączonych ze sobą za pomocą sterownika obecnie, najczęściej stosowanym sterownikiem jest SCSI.  Skupiając się na samej technologii, możemy powiedzieć o tym, iż RAID może być sprzętowy lub programowy, a zasadą działanie jest tworzenie kopii danych na jednym lub większej ilości dysków w celu zabezpieczenia danych przed utratą lub zwiększenia wydajności samego systemu – istotną rzeczą jest to, iż macierz RAID nie zabezpieczy nas przed awarią dysków – zalecane jest więc tworzenie kopii bezpieczeństwa. Przez niektóre osoby macierze RAID są mylnie postrzegane, jakoby w zależności od numeru były one mniej lub bardziej bezpieczne tudzież wydajne. Nic bardziej mylnego. Macierze RAID zgodnie ze swoją numenklaturą opisują sposoby tworzenia, wydajności, bezpieczeństwa, co również naprowadza nas do sposobu zastosowania właściwej macierzy w wybranym środowisku. W zależności od potrzeb i zasobów możemy przecież potrzebować szybkiego systemu gotowego przejąć pracę w przypadku awarii lub macierzy do przetrzymywania kopii zapasowej.  
	
Systemy RAID mogą być również łączone, celem uzyskania dodatkowych profitów – przykładem takiego rozwiązania jest RAID 1+0 oraz 1+5

## **Macierze RAID**

W zależności od sposobu wykonywania kopii, możemy skorzystać z RAID 0/1/2/3/4/5/1+0/1+5/6/7 do nich możemy dodać takie rozwiązania jak JBOD

 **JBOD** – system połączenia co najmniej dwóch dysków. System jest o tyle prosty, iż jest to liniowe połączenie wielu dysków fizycznych celem otrzymania jednego dużego dysku logicznego. Mówiąc krótko łączymy kilka dysków twardych, które będą wykorzystywane jako jeden dysk.  Nasuwa się zatem pytaniem jak wygląda wydajność, przecież dyski mogą posiadać różną prędkość – w takim wypadku brana pod uwagę jest średnia prędkość wszystkich dysków. 
 
![image](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e2/JBOD.svg/200px-JBOD.svg.png)


Rozwiązanie posiada oczywiście swoje zalety – jest proste w konfiguracji i w łatwy sposób pozwala na rozszerzenie partycji/przestrzeni dyskowej, minusem jednak jest to, iż w przypadku awarii jednego z nich macierz przestanie działać. 


**RAID 0** – macierz tego typu wymaga połączenia co najmniej 2 dysków twardych, których pojemność jest sumowana i charakteryzuje się zwiększoną wydajnością. Z przeprowadzonych testów wynika, iż tego typu rozwiązanie pozwala niemal dwukrotnie przyspieszyć pracę urządzeń.  Mimo to RAID 0 posiada istotne wady, nie zabezpieczy nas przed utratą danych, z racji, iż dane są zapisywane naprzemiennie na dyskach, awaria jednego z nich spowoduje utratę całości danych.  
 
![image](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9b/RAID_0.svg/150px-RAID_0.svg.png)
 
Zastosowanie dla tego typu macierzy znajdziemy w systemach, gdzie potrzebujemy zwiększonej szybkości operacji dyskowych na stacjach roboczych czy obróbki plików multimedialnych. 

**RAID 1** – jest to macierz typu Mirror czyli replikacja danych. Rozwiązanie cechujące się odpornością na awarię, nawet w przypadku uszkodzenia jednego z dysków, dane nie zostaną uszkodzone. Klonowanie wiąże się jednak z tym, iż te same dane będą zapisywane na obu dyskach jednocześnie, co za tym idzie, macierz tego typu będzie posiadać pojemność równą najmniejszego dysku, a prędkości zapisu i odczytu będą na poziomie najwolniejszego z nich. 

![image](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b7/RAID_1.svg/150px-RAID_1.svg.png)
 
W związku z powyższym macierz typu RAID 1 znajdzie zastosowanie w przypadku przechowywania ważnych danych lub wykonywania kopii zapasowych.

**RAID 2** – przede wszystkim ten rodzaj macierzy jest wykorzystywany niezwykle rzadko, ponieważ podział danych jest wykonywany już na poziomie bitów zapamiętanych z wykorzystaniem kodowania Hamminga a do jej budowy potrzebujemy nie mniej, niż 3 dyski twarde. RAID 2 charakteryzuje się tym, iż dane podzielone na bity zostają zapisane na dwóch dyskach, trzeci natomiast jest wykorzystywany jako źródło informacji do korekcji błędów. 



![image](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b5/RAID2_arch.svg/350px-RAID2_arch.svg.png)




System jest przestarzały i obecnie nie znajduje dla niego realnego zastosowania – został wyparty przez macierze RAID typu 5 oraz 6.


**RAID 3** -podobnie jak w macierzy typu RAID 2 wykorzystywane były co najmniej trzy dyski, z czego trzeci dysk służył do zapisywania informacji o parzystości bitów. 

 ![image](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f9/RAID_3.svg/180px-RAID_3.svg.png)
	
Podobnie jak w przypadku RAID 2 system ten również został szybko wyparty przez macierze typu 5 oraz 6.


**RAID 4** -  zasadniczo RAID poziomu 4 niewiele różni się od poprzedniego rodzaju macierzy, jednak w przypadku tego rozwiązania podziału nie dokonuje się na poziomie bajtów czy bitów lecz bloków o wielkości sektora dyskowego. Dzięki temu, iż z dysku można pobrać cały sektor danych (overlaping) – dostęp do danych jest znacznie szybszy, niż w przypadku poprzedniej wersji macierzy. 
 
![image](https://upload.wikimedia.org/wikipedia/commons/thumb/a/ad/RAID_4.svg/180px-RAID_4.svg.png)
 
RAID 4 – może być wykorzystywany dla serwerów plikowych oraz baz danych, natomiast tych, gdzie nie będzie wykonywanych zbyt wiele operacji. 

**RAID 5** – Macierz ta charakteryzuje się tym ,iż podobnie jak w poprzednich macierzach RAID 2 – RAID 4, również są wykorzystywane tak zwane dane parzystości – w tym przypadku jednak nie jest do tego wykorzystywany osobny dysk, a każdy z wykorzystywanych dysków posiada część miejsca zarezerwowaną dla danych kontrolnych. Dzięki temu w macierzy typu RAID 5 uzyskujemy wysoką prędkość zapisu i odczytu, ze względu na to, iż jeden blok informacji może być transmitowany z każdego dysku, co warto nadmienić macierz tego typu jest odporna na awarię, ponieważ usterka jednego dysku nie spowoduje utraty dostępu do danych . Jest to obecnie jeden z popularniejszych systemów macierzy RAID.  Do skonstruowania tego typu macierzy wymagane są co najmniej 3 dyski twarde.


![image](https://upload.wikimedia.org/wikipedia/commons/thumb/6/64/RAID_5.svg/180px-RAID_5.svg.png)


RAID 5, może być wykorzystywany miedzy innymi jako storage pod bazy danych. Minusem tego rozwiązania jest nieco niższa wydajność w porównaniu z RAID 0 z powodu konieczności wyliczania parzystości każdego bloku, co jednak przy dużej odporności na awarię wydaje się być sensownym rozwiązaniem. 

**RAID 6** to rozbudowana wersja RAID 5, gdyż pojemność tej macierzy wynosi n-2 razy pojemność najmniejszego z dysków. Na dysku zapisywane są dwie sumy kontrolne, więc awarii mogą ulec aż dwa HDD bez uszczerbku w działaniu systemu.

 ![image](https://upload.wikimedia.org/wikipedia/commons/thumb/7/70/RAID_6.svg/300px-RAID_6.svg.png)
 
Macierz ta, może być wykorzystywana w takich samych środowiskach jak RAID 5, czyli backup, archiwizacja oraz rozwiązania wysokiej dostępności., ponieważ posiada znacznie wyższą odporność.



**RAID 1+0** – ten rodzaj macierzy charakteryzuje się połączeniem ze sobą dwóch rodzajów systemu RAID 1 oraz 0, system ten charakteryzuje się dużą szybkością oraz odpornością na uszkodzenia. Jeżeli dojdzie do usterki dysku, jedna część macierzy pozostaje niedostępna, natomiast wciąż posiadamy kopię drugiego elementu. 

 ![image](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e6/RAID_10_01.svg/220px-RAID_10_01.svg.png)

Rozwiązanie posiada szybkość na poziomie RAID 0 oraz zabezpieczenie przed utratą danych na poziomie RAID 1, dzięki czemu może być z powodzeniem stosowane jako serwery aplikacyjne czy szybkie magazyny danych lub storage dla ESX lub innych maszyn wirtualnych, dodatkowym atutem tego rodzaju macierzy jest prosta implementacja. Minusem tego rozwiązania jest większy koszt przechowywania danych w stosunku do pozostałych macierzy.   

**RAID 0+1** – jest to odwrócona kombinacja macierzy 1+0, efekt końcowy jest zbliżony również do poprzednika, różni się rodzajem implementacji, jest natomiast nieco mniej wydajny od rozwiązania 1+0. 
 
 
**RAID 5+0** – macierz łącząca w sobie wydajność systemu RAID 1 oraz bezpieczeństwo z poziomu RAID 5, dzięki czemu uzyskujemy dużo wydajniejszy system, który dodatkowo jest dobrze zabezpieczony. 
 
![image](https://upload.wikimedia.org/wikipedia/commons/thumb/a/ad/RAID_01.svg/180px-RAID_01.svg.png)
	
Rozwiązanie znajdzie zastosowanie w większym firmach, ze względu na złożoność wdrożenia oraz koszty, które pojawią się ze względu na ilość wymaganych dysków. 


**RAID 7** - Ostatnia koncepcja zaakceptowana przez RAB jest nazywana Storage Komputer RAID level 7. Poziom 7 jest najbardziej niezawodnym systemem pamięci dyskowej, który jest zarządzany przez przeznaczony jedynie do ochrony danych w pamięciach masowych komputer dedykowany. Maksymalna konfiguracja umożliwia zainstalowanie nawet do 48 różnych kanałów dyskowych napędów. System RAID 7 umożliwia współdziałanie dysków heterogenicznych, czyli takich o różnych parametrach eksploatacyjnych, w tym również dysków, które różnią się rodzajem zapisu danych. Za sprawą rejestracji kodów kontrolnych na specjalnie dedykowanych do tego celu stacjach dyskowych, możliwe jest odtwarzanie informacji nawet w wypadku awarii aż 4 dysków fizycznych.  – opcja ta podobnie jak JBSOD nie jest uważana za system RAID, a jako znak rozpoznawczy firmy Storage Computer Corporation. Rozwiązanie jest niezwykle drogie 

**RAID sprzętowy**
Sprzętowe kontrolery RAID posiadają procesor dla obliczeń wszystkich operacji RAID, przez co nie jest generowane dodatkowe obciążenie dla procesora przez obliczenia RAID.

**RAID programowy**
Programowy RAID nie wymaga kontrolera RAID, mogą zostać wykorzystane normalne kontrolery pamięci masowej SATA lub SAS bez funkcjonalności RAID (np. kontroler SATA, który jest zintegrowany w chipsecie płyty głównej). Funkcjonalność RAID jest kompletnie realizowana przez system operacyjny (np. Windows lub Software RAID w Linuksie). Obliczenia wszystkich operacji RAID są realizowane przez procesor komputera (nie przez dedykowany procesor kontrolera sprzetowego)


**Źródła**
-wikipedia
-forum PcLab
-www.kylos.pl
