## OCFS 1
Pierwsza wersja OCFS została wydana przez firmę Oracle dla systemu Linux-jądra w wersji 2.4. I choć wersja, wydany na wolnej licencji, miała pewne ograniczenia, ona pozwalała uzyskać bezpośredni dostęp do plików bazy danych, a także dawała szereg innych korzyści administratorom. Tak jak pierwsza wersja systemu została stworzona tylko dla klastra baz danych Oracle, nie była POSIX-zgodny, w przeciwieństwie do drugiej wersji OCFS.

## OCFS 2
System OCFS została zastąpiona przez system OCFS2, w której dodano zgodność z POSIX, co znacznie poszerzyło zakres zastosowania systemu. Jedną z zalet OCFS2, oprócz zapewnienia zgodności z POSIX, polega na tym, że ona została zintegrowana w kernel 2.6.16. Znak "experimental" ("Eksperyment") została usunięta z systemu OCFS2 w wersji jądra 2.6.19.

Oracle Cluster Filesystem 2 (OCFS2) — system przeznaczony do podziału na dwa lub więcej Linux-systemy, jednocześnie pracującymi z jednym i tym samym rozdzielającym repozytorium (shared storage). Charakteryzuje się wysoką wydajnością i niezawodnością. Jest rozwijany przez firmę Oracle. Jest wolnym oprogramowaniem. 
System plików ma semantyka lokalnego systemu plików i nie wymaga żadnej specjalnej modyfikacji oprogramowania korzystającego z jej.

W chwili obecnej system plików OCFS2 jest używany w produkcie firmy Oracle Real Application Cluster. Oprócz tego, często stosuje się przy budowaniu skalowalnych serwerów Www, serwerów plików, systemów pocztowych, a także do przechowywania obrazów maszyn wirtualnych.

System działa na każdej magazynu, do którego dostęp może odbywać się za pomocą protokołów takich jak iSCSI, AoE lub DRBD.

## Możliwości systemu plików OCFS2

* Bloki o zmiennym rozmiarze;
* Elastyczne przydzielanie przestrzeni (zakresy, rozrzędzony pliki, nieutrwalonych zakresów z możliwością tworzenia dziur);
* Logowanie (obsługiwane są tryby ordered i writeback);
* W systemach różnych platform sprzętowych działa tak samo (x86, x86_64, ia64 i ppc64);
* Obsługa wbudowanego Clusterstack z rozproszonym systemem kontroli blokad (Distributed Lock Manager);
* Wsparcie bezpośredniego, asynchroniczne, splice() wejścia/wyjścia, a także możliwość wyświetlania pamięci na system plików (Memory Mapped I/Os);
* Różnorodne narzędzia, które zapewniają kompleksowe wsparcie dla systemu plików.

## Oprogramowanie

mkfs.ocfs2 — utwórz system plików OCFS2;
mount.ocfs2 — montuje system plików OCFS2;
mounted.ocfs2 — znaleźć wszystkie systemy plików OCFS2 na tej witrynie;
fsck.ocfs2 — sprawdzić integralność systemu plików OCFS2;
o2cb — zatrzymanie, uruchomienie, konfiguracja klastra (stos OCFS2); zawiera je w swoim składzie wiele składników (o2nm, o2hb, o2net, o2dlm).
ocfs2console — graficzny  interfejs do zarządzania OCFS2.
Składniki o2cb:

o2nm — kierownik węzłów (node manager);
o2hb — heratbeat agent;
o2net — agent sieciowy;
o2dlm — rozproszony kierownik blokad (distributed lock manager).

Konfiguracja
Plik konfiguracyjny:

  /etc/ocfs2/cluster.conf
  /etc/sysconfig/o2cb
 
 Przykład:
 
 node:
        
        ip_port = 7777
        
        ip_address = 192.168.2.100
        
        number = 0
        
        name = linux1
        
        cluster = ocfs2
        

node:

        ip_port = 7777
        
        ip_address = 192.168.2.101
        
        number = 1
        
        name = linux2
        
        cluster = ocfs2
        

cluster:

        node_count = 2
        
        name = ocfs2

Plik konfiguracyjny opisuje instalację z dwóch węzłów (linux1, linux2), ich adresy i porty, na których dostępna jest usługa.

Wartości budzików opisano w pliku /etc/sysconfig/o2cb. Skonfigurować limity czasu można za pomocą skryptu startowego o2cb.

Po tym jak konfiguracja klastra opisana, można utworzyć system plików:

       mkfs.ocfs2 /dev/drbd1

Tutaj zakładamy, że na węzłach dostępne wymianę magazynie /dev/drbd1.

Wpisujemy jej w /etc/fstab.

      /dev/drbd1  /ocfs2/vol1   ocfs2  defaults   0 0
      
Uruchomienie:

     /etc/init.d/o2cb online CLUSTER-NAME
     
     
Żródła:

https://ru.wikipedia.org/wiki/OCFS

https://lwn.net/Articles/137278/

https://ru.bmstu.wiki/OCFS_(Oracle_Cluster_File_System)


ANDRII CHABAN 
     



