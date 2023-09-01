# EGZAMIN SO
## WYKLAD 9
- **Brak zarządzania pamięcią operacyjną**:
   - Pierwsza technika opisana jako brak zarządzania pamięcią operacyjną.
   - W tej technice nie ma żadnego kontrolowania dostępu do pamięci operacyjnej, wszyscy mają swobodny dostęp.

- **Pamięć podzielona w systemie MS-DOS**:
   - W systemie MS-DOS pamięć operacyjna była podzielona na dwa obszary: jeden dla systemu operacyjnego i drugi dla programu użytkownika.
   - Programy użytkownika były zawsze ładowane w określone miejsce w pamięci.

- **BIOS (Basic Input Output System)**:
   - BIOS to pakiet procedur umożliwiających niskopoziomowe operacje na urządzeniach, takie jak odczyt i zapis na dysku.
   - BIOS działał na poziomie sprzętu i był dostępny przez przerwania programowe.

- **Nakładki**:
   - W celu wykorzystania większej ilości pamięci programiści mogli korzystać z nakładek, które pozwalają na dzielenie programu na mniejsze fragmenty.

- **Wieloprogramowanie**:
   - W systemach z nakładkami tylko jeden program użytkownika mógł działać naraz.
   - Dopiero wprowadzenie systemu Windows jako nakładki na MS-DOS umożliwiło interaktywne interfejsy graficzne.

- **Wymiana pamięci**:
   - Wymiana pamięci polega na przenoszeniu procesów między pamięcią operacyjną a pamięcią masową (np. dyskiem twardym).
   - Operacja wymiany jest wolniejsza od operacji na pamięci, co wymaga optymalizacji czasu wymiany.

- **Partycja wymiany**:
   - Tworzenie specjalnej partycji wymiany na dysku twardym, aby minimalizować ruch głowicy i przyspieszyć operacje wymiany.

- **Przełączanie kontekstów**:
   - Przełączanie procesów w pamięci operacyjnej w celu zwiększenia efektywności wykorzystania procesora.

- **Wiązanie adresów**:
   - Proces podlegający wymianie musi powrócić do tego samego miejsca w pamięci, jeśli nie stosowano wiązania dynamicznego adresu.

- **Zastosowanie wymiany**:
    - Wymiana pamięci stosowana jako zawór bezpieczeństwa w sytuacjach, gdy system operacyjny jest przeciążony i brakuje pamięci.

**Zarządzanie pamięcią w systemach komputerowych**

W zarządzaniu pamięcią komputerową istnieją różne techniki, z których jedną z nich jest model dynamicznego przydzielania pamięci. Wcześniej omawiano statyczne podejście, ale teraz skupimy się na bardziej elastycznych strategiach.

**Podstawowe pojęcia:**
- Dziury w pamięci: Obszary dostępnej wolnej pamięci, które nie są zajęte przez procesy.
- Proces: Program uruchamiany na komputerze, który wymaga dostępu do pamięci.

**Model dynamicznego przydzielania pamięci:**
- W tym modelu cała dostępna pamięć operacyjna dzielona jest na różne obszary, z których każdy ma swój rozmiar.
- Rozmiary obszarów mogą być różne i zależą od konfiguracji systemu.
- Każdy obszar może pomieścić co najwyżej jeden proces.
- System operacyjny śledzi, które obszary są wolne.

**Przydzielanie pamięci:**
- Gdy proces żąda pamięci, system operacyjny szuka odpowiednio dużego obszaru.
- Proces podaje, jak dużo pamięci potrzebuje.
- System operacyjny znajduje odpowiednio duży obszar i przydziela go procesowi.
- Proces otrzymuje cały obszar, nawet jeśli jest większy niż jego rzeczywiste potrzeby.

**Strategie przydzielania pamięci:**
- Istnieją różne strategie przydzielania pamięci, takie jak FirstFit, BestFit i strategie FirstFit w wersji cyklicznej.
- FirstFit szuka pierwszego dostatecznie dużego obszaru od początku listy wolnych obszarów.
- BestFit szuka najmniejszego wystarczająco dużego obszaru, aby minimalizować straty.
- Cykliczna wersja strategii FirstFit zapamiętuje, gdzie zakończono poprzednie wyszukiwanie i kontynuuje od tego punktu.

**Wady statycznych obszarów:**
- Statyczne obszary mają ograniczoną wieloprogramowość, ponieważ liczba procesów jest ograniczona do dostępnych obszarów.
- Istnieje problem fragmentacji wewnętrznej, gdzie procesy mogą nie wykorzystywać całego przydzielonego obszaru.

**Dynamiczne przydzielanie pamięci:**
- W dynamicznym modelu pamięć jest przydzielana elastycznie, nie ma stałej liczby obszarów.
- Procesy otrzymują dokładnie tyle pamięci, ile potrzebują, a nie stały rozmiar obszaru.

**Wyzwania dynamicznego zarządzania pamięcią:**
- Lista dostępnych dziur w pamięci może być długa, co wymaga dodatkowej kontroli.
- Strategie przydzielania pamięci, takie jak FirstFit, BestFit i strategie cykliczne, mają różne efektywności w wykorzystaniu pamięci.

Poniżej znajdziesz ściągę na podstawie tekstu:

### **Zarządzanie pamięcią: Problem fragmentacji i algorytm Buddy**

**Problemy z wykorzystaniem pamięci:**
- W dynamicznym zarządzaniu pamięcią może występować problem fragmentacji.
- Fragmentacja pamięci oznacza, że dostępna pamięć jest podzielona na wiele małych fragmentów.
- Po pewnym czasie działania systemu może się zdarzyć, że dostępne dziury w pamięci są małe i rozproszone.

**Konsekwencje fragmentacji:**
- Nawet jeśli łączna ilość dostępnej pamięci jest wystarczająca, nie można jej przydzielić jednemu procesowi.
- Dziury mogą być zbyt małe, aby spełnić żądanie procesu, nawet jeśli ich łączny rozmiar jest wystarczający.

**Buddy Allocation Algorithm (Algorytm Buddy):**
- Algorytm Buddy to technika dynamicznego przydzielania pamięci, która pomaga w zwalczaniu problemu fragmentacji.
- Zakłada ona, że rozmiar bloku pamięci musi być potęgą liczby 2.
- Dostępna pamięć jest podzielona na bloki o różnych rozmiarach, gdzie każdy rozmiar jest potęgą dwójki (np. 2^0, 2^1, 2^2, itd.).

**Przydzielanie pamięci algorytmem Buddy:**
- Gdy proces żąda pamięci o określonym rozmiarze, algorytm Buddy znajduje najbliższą większą potęgę dwójki (blok) i sprawdza dostępność bloku o tym rozmiarze.
- Jeśli blok jest dostępny, jest przydzielany procesowi.
- Jeśli blok jest większy niż potrzebny, jest dzielony na dwie części (buddies), z których jedna jest przydzielona procesowi, a druga staje się dostępnym blokiem mniejszego rozmiaru.

**Zalety algorytmu Buddy:**
- Algorytm Buddy minimalizuje fragmentację wewnętrzną, ponieważ rozmiary bloków są zawsze potęgami dwójki.
- Dzięki temu dostępna pamięć jest efektywnie wykorzystywana.

**Wady i wyzwania:**
- Algorytm Buddy jest skuteczny, ale kosztowny obliczeniowo, ponieważ wymaga podziału bloków i śledzenia ich dostępności.
- W praktyce może prowadzić do pewnego marnotrawstwa pamięci, zwłaszcza jeśli procesy żądają niestandardowych rozmiarów pamięci.

**Systemy operacyjne i zarządzanie pamięcią**

W systemach operacyjnych istnieją różne metody zarządzania pamięcią, mające na celu efektywne wykorzystanie dostępnych zasobów. Jednym z problemów jest fragmentacja pamięci, która polega na tym, że dostępna pamięć jest podzielona na małe fragmenty, co może prowadzić do problemów w alokacji pamięci dla procesów.

**Defragmentacja pamięci** to jedna z naturalnych strategii. Polega na przesuwaniu zajętych i wolnych obszarów pamięci w celu utworzenia jednego spójnego obszaru. Jednak jest to kosztowna operacja i może być problematyczna, zwłaszcza przy statycznym wiązaniu adresów.

Inną strategią jest **algorytm Wiązania w Liźniaków**. Pamięć jest podzielona na ramki, a każda strona procesu jest przypisana do konkretnej ramki. To pozwala na elastyczne zarządzanie dostępną pamięcią i alokację stron dla procesów.

Strony są mapowane na konkretne ramki za pomocą **tablicy stron**. Dla każdego procesu istnieje taka tabela, która odzwierciedla, które strony znajdują się w jakich ramkach. Dzięki temu system operacyjny może dokonywać translatcji adresów logicznych procesu na fizyczne.

Strony i ramki mają stały rozmiar, na przykład 4 kilobajty, co ułatwia zarządzanie. Kiedy proces potrzebuje dostępu do danej strony, system operacyjny używa tablicy stron, aby znaleźć odpowiadającą jej ramkę.

**Stronicowanie** pozwala na elastyczne zarządzanie pamięcią, ale wymaga skomplikowanego mechanizmu translacji adresów. Adres logiczny składa się z numeru strony i przesunięcia w obrębie strony.

Warto zauważyć, że stronicowanie jest bardziej elastycznym podejściem do zarządzania pamięcią niż tradycyjne, ciągłe przydzielanie spójnych obszarów pamięci procesom.

Powyższe informacje to tylko wprowadzenie do tematu zarządzania pamięcią w systemach operacyjnych, który jest bardzo obszerny i złożony.

**Stronicowanie i Tablica Stron:**

- Adres przystronicowania można podzielić na dwie części: numer strony i przesunięcie.
- Numer strony jest wykorzystywany jako indeks fabryki stron, aby odczytać numer RAM.
- Odczyt numeru RAM umożliwia podmianę starszych bitów przed numerem RAM, tworząc adres fizyczny.
- Proces translacji adresu sprowadza się do przekształcenia adresu logicznego na adres fizyczny.
- Translacja adresu jest realizowana sprzętowo, a rola systemu operacyjnego polega na uaktualnianiu rejestru przechowującego początkowy adres tablicy stron aktywnego procesu.
- Tablica stron przynależy do procesów, a system operacyjny pomaga procesowi dostarczając informacje o jej położeniu.

**Tablica Stron:**

- Każdy proces musi posiadać własną tablicę stron, a zawartość tablic stron różni się między różnymi procesami.
- Tablica stron znajduje się w pamięci fizycznej.
- System operacyjny przechowuje w rejestrze specjalnym adres początku tablicy stron aktywnego procesu, co pomaga przy translacji adresu.
- Aktualizacja tego rejestru jest konieczna po przełączeniu kontekstu na inny proces.
- W nowszych architekturach, gdzie tablice stron są znacznie większe, stosuje się techniki takie jak wielopoziomowe tablice stron lub haszowane tablice stron, aby zmniejszyć rozmiar tablicy stron.

**Bufor Translacji Adresów (TLB):**

- Bufor translacji adresów (TLB) to mała pamięć podręczna, która przechowuje odwzorowania numerów stron na numery ramek, które były ostatnio używane przez proces.
- TLB przyspiesza proces translacji adresu, ponieważ pozwala uniknąć dostępu do pamięci operacyjnej w przypadku trafienia (hit) w TLB.
- Dla adresów, które nie zostaną znalezione w TLB, konieczne jest odwołanie się do tablicy stron w pamięci operacyjnej.
- Bufor TLB ma ograniczoną liczbę pozycji i działa w sposób asocjacyjny, co oznacza równoczesne porównywanie klucza (numeru strony) z wartościami w komórkach TLB.
- W przypadku trafienia w TLB, proces od razu otrzymuje odpowiadającą ramkę pamięci, co przyspiesza dostęp do danych.

**Wydajność Bufora TLB:**

- Efektywność bufora TLB zależy od współczynnika trafień. Im wyższy współczynnik trafień w TLB, tym szybszy jest dostęp do pamięci.
- Bufor TLB jest zazwyczaj znacznie szybszy niż dostęp do pamięci operacyjnej, co przyspiesza dostęp do danych.
- W przypadku trafienia w TLB, czas dostępu jest równy czasowi dostępu do TLB.
- W przypadku nie trafienia w TLB, czas dostępu jest równy sumie czasów dostępu do TLB i pamięci operacyjnej.
- Bufor TLB pomaga zmniejszyć średni czas dostępu do pamięci, co jest kluczowe dla wydajności systemu.

**Rola Bufora TLB w Wydajności:**

- Wejście na nową stronę w przypadku odwołania do instrukcji do wykonania lub danych do przetworzenia wymaga pobrania kolejnej instrukcji lub danych.
- W programach strukturalnych, wykonywanych cyklicznie lub w pętlach, istnieje duże prawdopodobieństwo, że kolejny rozkaz do wykonania znajduje się na tej samej stronie co poprzedni, co sprawia, że trafienie w TLB jest prawdopodobne.
- Podobnie, jeśli program odwołuje się do zmiennych lub struktur danych, TLB może zawierać wpisy związane z tymi danymi, co ponownie przyspiesza dostęp.

**Zarządzanie Buforem TLB:**

- Bufor TLB ma ograniczoną pojemność, więc trzeba zarządzać jego zawartością.
- Dodawanie nowych wpisów może wymagać usunięcia starszych.
- Istnieją różne strategie usuwania wpisów z TLB, które nie będą omawiane w wykładzie.
- Niektóre wpisy, takie jak te związane z często wykorzystywanymi funkcjami systemu operacyjnego, mogą być trwale przypisane do TLB.
- Przy przełączaniu kontekstu, TLB musi zostać wyczyszczony, ponieważ strona numer 0 jest tłumaczona na inną ramkę w nowym procesie, a niektóre rozwiązania sprzętowe uwzględniają identyfikator przestrzeni adresowej jako klucz w TLB, co pozwala uniknąć pełnego czyszczenia TLB przy przełączaniu kontekstu.

**Podsumowanie:**

- Bufor Translacji Adresów (TLB) jest kluczowym elementem przyspieszającym proces translacji adresów w systemach operacyjnych.
- Dzięki TLB możliwe jest skrócenie czasu dostępu do instrukcji i danych, co wpływa na wydajność systemu.
- Zarządzanie zawartością TLB i strategie usuwania wpisów z TLB są ważnymi aspektami zapewnienia efektywnego działania systemu.
- Przy przełączaniu kontekstu konieczne jest unieważnienie wpisów w TLB, aby zapobiec błędnym tłumaczeniom.
- TLB pomaga zmniejszyć narzut związany z translacją adresów, co jest kluczowe dla efektywności systemu.


## WYKLAD 10

**Stronicowanie i problemy z nim związane:**

- Stronicowanie to technika zarządzania pamięcią, która polega na podziale pamięci fizycznej na strony i używaniu tabel stron do mapowania adresów logicznych na fizyczne.
- Główny problem stronicowania to wydłużony czas dostępu do pamięci, ponieważ wymaga on dwóch dostępów do tablicy stron (pierwszy, aby znaleźć adres fizyczny strony, drugi, aby odczytać lub zapisać dane w pamięci).
- Bufory, translacja adresów strony i szybka pamięć asocjacyjna są sposobami radzenia sobie z problemem wydłużonego dostępu.

**Rozmiar tablicy stron:**

- Rozmiar tablicy stron jest istotny, a jego obliczenie zależy od rozmiaru pamięci logicznej i rozmiaru strony.
- Przykładowo, jeśli mamy --bitowe adresy i pamięć logiczną o rozmiarze -GB oraz strony o rozmiarze -KB, to rozmiar tablicy stron wynosi -MB.
- Jednak nowoczesne architektury mogą używać --bitowych adresów, co oznacza większy rozmiar tablicy stron.

**Nieciągła przestrzeń adresowa i mapowanie:**

- Procesy rzadko korzystają z całej przestrzeni adresowej, co oznacza, że wiele adresów logicznych pozostaje nieużywanych.
- Przestrzeń adresowa procesu może być podzielona na różne obszary, w tym na dane systemowe i urządzenia wejścia/wyjścia.
- Mapowanie pamięci nie musi być spójne, więc mogą występować luki w przestrzeni adresowej.
- W związku z tym warto stosować wielopoziomowe tablice stron, które pozwalają na efektywne zarządzanie przestrzenią adresową procesu i oszczędność pamięci.

**Wielopoziomowe tablice stron:**

- Wielopoziomowe tablice stron polegają na hierarchicznym podziale tablicy stron na poziomy, co pozwala na zaoszczędzenie pamięci.
- Przykładem może być tablica dwupoziomowa, gdzie mamy zewnętrzną tablicę stron i wewnętrzne tablice stron.
- Zaletą jest oszczędność pamięci przez uniknięcie alokowania tablicy stron dla nieużywanych obszarów.
- Wadą jest wydłużony czas dostępu, ponieważ wymaga on dodatkowych odczytów, aby znaleźć właściwą stronę w pamięci.

**Adresowanie wielopoziomowe:**

- Wielopoziomowe adresowanie oznacza, że adres logiczny dzieli się na różne fragmenty, które odpowiadają poziomom tablicy stron.
- Starsze bity numeru strony wskazują pozycję w zewnętrznej tablicy stron, środkowe bity wskazują pozycję w wewnętrznej tablicy stron, a młodsze bity to przesunięcie w obrębie strony.
- Wprowadzenie dodatkowych poziomów stronicowania nie zwiększa przestrzeni adresowej, ale pozwala na bardziej elastyczne zarządzanie nią.

**Bit modyfikacji:**

- Bit modyfikacji może wskazywać, czy strona jest przeznaczona tylko do zapisu lub tylko do odczytu, co ma znaczenie w kontekście implementacji pamięci wirtualnej.

Oczywiście, oto ściąga na podstawie tekstu:

**Organizacja tablicy stron w systemach operacyjnych:**

W systemach operacyjnych istnieją różne metody organizacji tablicy stron, które pozwalają na efektywne zarządzanie pamięcią. Poniżej omówiono dwie z tych metod:

- **Haszowanie tablicy stron:**
   - Haszowanie tablicy stron to modyfikacja organizacji stronic pamięci, w której strony są haszowane, aby skrócić dostęp do nich.
   - W tej metodzie, długie adresy, takie jak --bitowe, są przekształcane za pomocą funkcji haszującej, która wskazuje na pozycję w tablicy stron.
   - W tablicy stron znajdują się listy mapowań strony na ramkę.
   - Aby znaleźć mapowanie strony S na numer ramki, należy przeszukać listę mapowań w danej pozycji tablicy stron.
   - Ta metoda pozwala zmniejszyć rozmiar tablicy stron kosztem wydłużenia czasu translacji adresów.

- **Odwrotna tablica stron:**
   - Odwrotna tablica stron to inna metoda organizacji stronic pamięci.
   - W tej metodzie każda pozycja w tablicy stron odpowiada jednej ramce pamięci fizycznej.
   - W danej pozycji tablicy znajdują się informacje o stronie znajdującej się w danej ramce oraz informacje o procesie, który jest właścicielem tej strony.
   - Generowanie adresu opiera się na numerze strony, przesunięciu i identyfikatorze procesu, który jest doklejany sprzętowo.
   - Ta metoda umożliwia dostęp do stron, ale wymaga stosowania technik haszowania w celu skrócenia czasu dostępu.

**Zalety stronicowania w porównaniu do innych technik zarządzania pamięcią:**

- **Brak fragmentacji zewnętrznej:** Stronicowanie eliminuje problem fragmentacji zewnętrznej, w przeciwnieństwie do niektórych innych technik zarządzania pamięcią.
- **Możliwość współdzielenia pamięci:** Dzięki odpowiedniemu ustawieniu tablicy stron, możliwe jest łatwe współdzielenie pamięci między procesami.
- **Skuteczne zarządzanie pamięcią:** Stronicowanie umożliwia efektywne zarządzanie dostępną pamięcią fizyczną.

**Implementacja stronicowania:**

- System translacji adresów za pomocą stronicowania jest realizowany przez architekturę sprzętową.
- System operacyjny odgrywa rolę pośrednika w dostarczaniu informacji o położeniu tablicy stron aktualnie wykonywanego procesu.
- W tym celu wykorzystuje się specjalne rejestry, które przechowują informacje o początku tablicy stron procesu.
- System operacyjny odpowiada także za zapewnienie bezpieczeństwa dostępu do pamięci współdzielonej między procesami, wykorzystując semafory i inne mechanizmy.

Stronicowanie jest efektywną metodą zarządzania pamięcią, która pozwala na uniknięcie fragmentacji zewnętrznej, umożliwia współdzielenie pamięci i skuteczne zarządzanie zasobami pamięciowymi w systemach operacyjnych.

**Pamięć wirtualna i stronicowanie:**

Pamięć wirtualna to technika, która umożliwia efektywne zarządzanie pamięcią operacyjną w komputerze. Pozwala na obsługę większej ilości procesów niż dostępna fizyczna pamięć RAM. Działanie pamięci wirtualnej opiera się na stronicowaniu.

- Stronicowanie polega na podziale pamięci operacyjnej na małe fragmenty zwane stronami. Każda strona ma stały rozmiar, na przykład -kilobajty.
  
- Procesy operacyjne wykorzystują te strony jako jednostki dostępu do pamięci. Dzięki temu można ładować do pamięci tylko te strony, które są potrzebne w danym momencie, zamiast całości programu.

- Strony zawierają zarówno instrukcje programu, które są wykonywane, jak i dane, na których operuje procesor.

- System operacyjny może zarządzać tym, które strony są w pamięci RAM, a które na dysku twardym. Strony na dysku są dostępne, ale wymagają wczytania do pamięci RAM, co może potrwać dłużej.

- System operacyjny obsługuje błędy braku strony. Gdy proces próbuje uzyskać dostęp do strony, która nie jest w pamięci RAM, generowany jest błąd. Wtedy system operacyjny musi wczytać brakującą stronę z dysku do pamięci RAM.

- Jeśli pamięć RAM jest pełna, system operacyjny musi zdecydować, która strona zostanie usunięta, aby zrobić miejsce na nową. To może prowadzić do sytuacji, gdzie strona jest wczytywana, a następnie szybko z niej usunięta, co może być nieefektywne.

- Dla procesu korzystającego z pamięci wirtualnej, cały proces wydaje się być w pamięci, nawet jeśli część stron jest na dysku. To tworzy iluzję posiadania dużej ilości pamięci RAM, nawet jeśli jej fizyczna ilość jest ograniczona.

- System operacyjny musi skoordynować operacje wczytywania i usuwania stron z pamięci RAM oraz zarządzać dostępem do tych stron przez różne procesy.

- Wydajność pamięci wirtualnej zależy od częstotliwości występowania błędów braku strony. Jeśli są one rzadkie, to wprowadzenie pamięci wirtualnej może być bardzo korzystne, ponieważ procesy mogą działać tak, jakby miały dostęp do dużo większej ilości pamięci RAM.

- Bufory TLB (Translation Lookaside Buffers) są używane w procesie tłumaczenia adresów wirtualnych na adresy fizyczne. Pozwalają one na przechowywanie odzorowań stron do ramek pamięci, co przyspiesza dostęp do stron.

- Bufory TLB muszą być unieważniane w przypadku zmiany kontekstu procesu lub gdy strona jest usuwana z pamięci RAM.

Warto zauważyć, że wydajność pamięci wirtualnej zależy od wielu czynników, w tym od ilości dostępnej pamięci RAM, sposobu zarządzania stronami przez system operacyjny oraz lokalności odwołań w programach. Optymalne zarządzanie pamięcią wirtualną może znacząco poprawić wydajność systemu komputerowego.

## WYKLAD 11
Pamięć wirtualna to istotny element systemów operacyjnych, który pozwala na efektywne zarządzanie dostępną pamięcią operacyjną. W poprzednich częściach omawialiśmy już kilka kluczowych kwestii związanych z pamięcią wirtualną, takie jak sprowadzanie stron do pamięci i strategie zastępowania stron. Dzisiaj skoncentrujemy się na podziale tych strategii na dwie klasy: zastępowanie globalne i lokalne.

- **Zastępowanie lokalne**:
   - Strategia ta polega na wybieraniu stron do usunięcia z pamięci operacyjnej spośród własnych stron procesów. Jeśli proces napotyka na błąd braku strony i brakuje wolnych ramek, to system operacyjny usuwa stronę tego samego procesu i umieszcza w pamięci nową stronę.
   - Gwarantuje, że w pamięci zawsze znajduje się określona liczba stron tego samego procesu, która nie jest mniejsza niż liczba ramek przydzielonych temu procesowi. Jeśli proces nie wykorzystuje wszystkich ramek, część z nich pozostaje pusta.

- **Zastępowanie globalne**:
   - W strategii globalnej strony są usuwane niezależnie od tego, do którego procesu należą. To oznacza, że inne procesy mogą konkurować o dostęp do ramek pamięci, co może prowadzić do sytuacji, w której jakiś proces ma zbyt mało ramek lub stron w pamięci.
   - To podejście może prowadzić do mniejszej przewidywalności czasu wykonywania procesów, ponieważ nie ma gwarancji, ile ramek zostanie przydzielonych danemu procesowi.

Wybór między strategią lokalną a globalną zastępowania stron zależy od wielu czynników i jest kompromisem między elastycznością a przewidywalnością. Strategia lokalna gwarantuje, że każdy proces ma określoną liczbę ramek, ale może prowadzić do marnotrawstwa zasobów. Strategia globalna jest bardziej elastyczna, ale może wprowadzać większą niestabilność w czasie wykonania procesów.

Warto również zrozumieć, że przydział ramek pamięci dla procesów musi być starannie rozważany. Nie można przydzielać zbyt małej liczby ramek, ponieważ procesy muszą mieć dostęp do stron zawierających kod rozkazów i argumentów, a te strony mogą być wielobajtowe i leżeć na granicy stron. Dlatego rozważając przydział ramek, musimy uwzględnić te różne aspekty, aby zapewnić efektywne działanie systemu operacyjnego.

- Liczba ramek pamięci:
   - Liczba ramek pamięci musi być dobrze przemyślana, aby uniknąć błędów braku strony.
   - Zbyt mała liczba ramek może prowadzić do błędów braku strony, co z kolei wpływa na wydajność systemu.
   - Niedostateczna liczba ramek może wymusić zapisywanie stron na dysku, co jest czasochłonne.

- Lokalne i globalne strategie zastępowania stron:
   - Lokalne strategie mogą przydzielać ramki indywidualnie każdemu procesowi.
   - Globalne strategie mogą przydzielać ramki na podstawie priorytetów procesów.
   - Wybór strategii wpływa na liczbę błędów braku strony i ogólną wydajność systemu.

- Zjawisko "migotania strony":
   - Występuje, gdy proces nie ma wystarczającej liczby ramek, a wszystkie strony w pamięci są aktywnie używane.
   - Spowodowane brakiem dostępnej pamięci fizycznej.
   - Procesy oczekują na sprowadzenie swoich stron, co wpływa negatywnie na wydajność.

- Zarządzanie zbiorami roboczymi (working set):
   - Zbiór roboczy to zbiór stron, które są aktywnie wykorzystywane przez proces w danym czasie.
   - Monitorowanie zbiorów roboczych może pomóc w zarządzaniu pamięcią.
   - Delta czasu jest używana do przybliżenia aktywnie wykorzystywanych stron.

- Sposób oszczędzania informacji o odwołaniach do pamięci:
   - Przy użyciu bitów odwołania, które są ustawiane w przypadku odwołania do danej strony.
   - Może być używany do przybliżenia zbioru roboczego procesu.

- Wprowadzenie procesów do pamięci:
   - W przypadku braku wystarczającej ilości dostępnej pamięci, procesy mogą być zapisywane na dysku i ponownie wczytywane w pamięć.
   - To może prowadzić do migracji stron i spadku wydajności.

- Wyznaczanie granic ilości dostępnej pamięci:
   - System operacyjny musi monitorować ilość dostępnej pamięci fizycznej.
   - Jeśli ilość ta jest zbyt mała, może być konieczne wstrzymanie procesów lub zapisywanie ich na dysku.


**Zarządzanie stronami i wymiana ramek w systemie operacyjnym:**

- **Wstęp**
   - W systemie operacyjnym zarządzanie pamięcią jest kluczowym elementem.
   - Wymagane jest efektywne przechowywanie i zarządzanie stronami procesów.
   
- **Tablica Stron**
   - W systemie operacyjnym istnieje tablica stron, która śledzi dostępność stron pamięci fizycznej.
   - Każda strona zawiera informacje bitowe.
   
- **Bit Odwołania**
   - Bit odwołania ustawiany jest sprzętowo w momencie odwołania do strony.
   - Pomaga określić, czy strona była używana od ostatniej wymiany.
   
- **Bit Modyfikacji**
   - Bit modyfikacji informuje, czy strona była zmieniana od ostatniej wymiany.
   - Jeśli strona była modyfikowana, musi zostać zapisana podczas wymiany.
   
- **Algorytm Zegarowy z Przybliżaniem Zbioru Roboczego**
   - Algorytm ten pomaga w wyborze stron do wymiany.
   - Krok - Algorytm inicjuje zapis i zeruje bit modyfikacji oraz odwołania, a także aktualizuje czas ostatniego odwołania.
   - Krok - Przeszukuje tablicę ramek w poszukiwaniu kandydatów.
   - Krok - Wybiera strony, które są kandydatami do wymiany na podstawie bitów odwołania, modyfikacji i czasu odwołania.
   - Krok - Jeśli jest idealny kandydat (brak odwołań, brak modyfikacji), strona jest wymieniana.
   - Krok - Jeśli brakuje idealnego kandydata, algorytm może wybrać stronę do zapisania, oczekując na zakończenie zapisu.
   - Krok - W przypadku braku wolnych stron lub strony do zapisu, algorytm podejmuje decyzję o zawieszeniu jednego z procesów, aby zwolnić miejsce w pamięci.

- **Parametr Delta**
   - Parametr ten przybliża zbioru roboczego, określając, które strony są potrzebne na podstawie czasu odwołań.
   - Deltate określa, ile ostatnich jednostek czasu jest brane pod uwagę.
   
- **Wymiana Stron w Pamięci**
   - Wymiana ramek na dysku zachodzi tylko wtedy, gdy brakuje pamięci.
   - Gdy jest wystarczająco wolnych ramek, nowe strony są przydzielane bez wymiany.
   
- **Podsumowanie**
   - Algorytm zegarowy z przybliżaniem zbioru roboczego jest używany do zarządzania stronami w pamięci fizycznej.
   - Efektywnie wybiera strony do wymiany, minimalizując liczbę zapisów na dysk.
   - Wymiana ramek zachodzi tylko w przypadku braku wolnej pamięci.

Powyższy tekst omawia kilka kwestii związanych z zarządzaniem pamięcią w systemach operacyjnych. Oto ściąga na podstawie tego tekstu:

**- Zarządzanie stronami:**
   - Błędy braku strony mogą wystąpić na początku lub później działania programu.
   - Błędy braku strony są obsługiwane przez czytanie potrzebnej strony do wolnej ramki.
   - Jeśli wolne ramki są dostępne przez cały czas, nie ma potrzeby uruchamiania algorytmu wymiany stron.
   - Wymiana stron jest konieczna, gdy proces potrzebuje więcej pamięci niż jest dostępne fizycznie.

**- Praca w trybie jądra:**
   - Jądro systemu operacyjnego jest mapowane na przestrzeń adresową każdego procesu, powyżej adresu -.
   - Dostęp do funkcji systemowych jest możliwy dla każdego procesu, bez konieczności osobnej mapy pamięci.

**- Ustawianie bitów sprzętowo:**
   - Bit kontrolujący dostęp do strony musi być ustawiany sprzętowo, aby uniknąć konieczności przejmowania kontroli przez system operacyjny przy każdym odwołaniu do pamięci.

**- Informacje o tablicy stron:**
   - System operacyjny przekazuje sprzętowi informacje o tablicy stron poprzez dedykowany rejestr.
   - Rejestr ten zawiera adres początku tablicy stron i jest uaktualniany przy każdym przełączeniu kontekstu.

**- Tryb jądra i tablica stron:**
   - Jądro systemu operacyjnego ma dostęp do przestrzeni adresowej każdego procesu i używa wspólnych map pamięci.
   - Przy przełączaniu kontekstu zmienia się wskaźnik na początek tablicy stron aktywnego procesu.

**- Implementacja funkcji fork:**
   - Implementacja funkcji fork polega na tworzeniu nowego procesu, który jest kopią procesu macierzystego.
   - Współdzielona pamięć między procesem macierzystym a potomnym jest osiągnięta poprzez oznaczenie stron jako tylko do odczytu.
   - Kopiowanie stron jest opóźniane, aż do momentu, gdy proces potomny lub macierzysty próbuje je zmodyfikować.

**- Strategia odkładania kopiowania:**
   - System operacyjny stosuje strategię opóźniania kopiowania stron, aby uniknąć kopiowania niezmienionych danych.
   - Kopiowanie jest wykonywane dopiero w momencie próby zapisu na współdzieloną stronę.

**- Strony anonimowe i ich zarządzanie**
- Strony anonimowe są wykorzystywane do przechowywania danych w procesach.
- Nie są one inicjowane od razu, tylko w momencie faktycznego zapisu danych na nie.
- Gdy proces odwołuje się do strony anonimowej, system operacyjny inicjuje wczytanie strony z dysku do pamięci.
- Operacja ta jest wywoływana przez błąd braku strony (page fault) i spowodowana odwołaniem do adresu logicznego, który nie ma odpowiadającej mu fizycznej strony w pamięci.

**- Zarządzanie pamięcią dyskową**
- Dla stron anonimowych, miejsce na dysku jest rezerwowane z wyprzedzeniem, ale bloki na dysku są wykorzystywane dopiero w przypadku rzeczywistego zapisu danych.
- Miejsce na dysku jest optymalnie rozmieszczane, aby zoptymalizować operacje sekwencyjnego zapisu danych na dysk.
- Strony anonimowe nie mają fizycznego backupu na dysku, dopiero w momencie zapisu dane są faktycznie zapisywane na dysk.

**- Przełączanie do trybu jądra**
- Istnieją różne możliwości przełączania się do trybu jądra, włączając w to wywołanie funkcji systemowej, przerwania zegarowe związane z końcem kwantu czasu i inne przerwania, które wymagają obsługi przez system operacyjny.
- Adres, do którego zostanie wykonany skok po wystąpieniu przerwania, zależy od rodzaju tego przerwania i jest określany w tablicy wektorów przerwań.
- Tablica wektorów przerwań zawiera adresy funkcji obsługi przerwań i jest skonfigurowana uprzednio.

**- Wektor przerwań**
- Wektor przerwań to tablica, która przyporządkowuje numerom przerwań adresy funkcji obsługi tych przerwań.
- Numer przerwania jest przypisywany sprzętowo, na przykład przerwanie od timera ma swój określony numer.
- Adresy funkcji obsługi przerwań są zapisane w tablicy wektorów przerwań i wywoływane są w odpowiedzi na konkretne przerwanie.

## WYKLAD 12
Powyższy tekst dotyczy różnych aspektów związanych z urządzeniami wejścia-wyjścia oraz systemami plików. Poniżej znajdziesz ściągę na podstawie tego tekstu:

- **Różnorodność urządzeń wejścia-wyjścia:** Istnieje szeroka różnorodność urządzeń wejścia-wyjścia, co sprawia, że opowiadanie o nich jest trudne. Przedstawiają one wyzwania związane z obsługą na poziomie systemu operacyjnego.

- **Jednolity obraz urządzeń:** System operacyjny stara się stworzyć jednolity obraz różnych urządzeń wejścia-wyjścia, aby programiści mogli korzystać z tych samych funkcji systemowych niezależnie od rodzaju urządzenia, czy to jest plik, urządzenie wejścia typu myszka, konsola czy dysk.

- **Kategorie urządzeń:** Urządzenia wejścia-wyjścia można podzielić na dwie główne kategorie: urządzenia blokowe i urządzenia znakowe. Urządzenia blokowe operują na danych w blokach określonego rozmiaru, podczas gdy urządzenia znakowe przesyłają strumienie bajtów bez konkretnej struktury.

- **Prędkości urządzeń:** Urządzenia operują z różnymi prędkościami. Na przykład klawiatura może przesyłać kilkanaście bajtów na sekundę, podczas gdy niektóre magistrale oferują znacznie większe prędkości.

- **Dostępność urządzeń:** Dostęp do urządzeń może być sekwencyjny lub swobodny. Urządzenia mogą komunikować się z procesorem synchronicznie lub asynchronicznie.

- **Rodzaj komunikacji:** Urządzenia mogą komunikować się z procesorem w sposób synchroniczny, np. za pomocą sygnału zegarowego, lub asynchroniczny, gdzie dane pojawiają się w różnych momentach czasu.

- **Współdzielenie urządzeń:** Urządzenia mogą być o dostępie wyłącznym lub współdzielonym. W przypadku dostępu wyłącznego tylko jeden proces może korzystać z urządzenia jednocześnie, podczas gdy w przypadku dostępu współdzielonego wiele procesów może korzystać z urządzenia jednocześnie.

- **Typy urządzeń w systemie uniksowym:** W systemie uniksowym urządzenia są grupowane na kilka powszechnie przyjętych typów, takich jak urządzenia blokowe, urządzenia znakowe, interfejsy sieciowe i wirtualne urządzenia. Procesory mogą być również widoczne w systemie plików jako rodzaj urządzenia.

- **Ważność informacji niskopoziomowych:** Choć istnieją informacje niskopoziomowe dotyczące urządzeń wejścia-wyjścia, są one ważne głównie z perspektywy programisty, który musi obsłużyć różnorodność tych urządzeń.

- **Ostateczny cel:** Ostatecznym celem jest stworzenie spójnego interfejsu dla programistów, aby mogli korzystać z urządzeń wejścia-wyjścia w sposób efektywny i zrozumiały, niezależnie od rodzaju urządzenia, z którym pracują.

**Budowa dysku twardego:**
- Dysk twardy ma budowę warstwową.
- Składa się z talerzy, na których znajdują się dane.
- Nad talerzami porusza się głowica, która wykonuje ruchy odczytu i zapisu.
- Talerze pokryte są warstwą magnetyczną, gdzie przechowywane są dane.

**Adresowanie i dostęp do danych:**
- Dane na dysku są adresowane w blokach.
- Blok ma unikalny numer, który mapowany jest na konkretne ścieżki, cylindry i sektory przez sterownik dysku.
- Sterownik dysku może dynamicznie przemapowywać uszkodzone bloki na inne miejsca na dysku.
- Wcześniej, adresowanie było statyczne, ale obecnie jest bardziej elastyczne i inteligentne.

**Optymalizacja dostępu do dysku:**
- Dostęp do danych może być optymalizowany, aby zminimalizować czas ruchu głowicy.
- Strategia "Shortest Seek First" polega na obsługiwaniu żądań do najbliższych bloków najpierw, aby zminimalizować przemieszczanie głowicy.
- Inne strategie, takie jak "Scan" i "Look," również mogą być używane w zależności od sytuacji.

**Przykład działania strategii optymalizacji:**
- Przykład zastosowania strategii "Shortest Seek First" pokazuje, jak można zminimalizować ruch głowicy i czas dostępu do danych, obsługując najbliższe bloki przed odległymi.

**Wyzwania związane z dyskiem twardym:**
- Dyski twarde mają ograniczoną prędkość obrotową, co wpływa na czas dostępu do danych.
- Dla napędów optycznych, stała gęstość bitów jest utrzymana przez regulację prędkości liniowej, a nie obrotowej.
- Warto również zauważyć, że istnieją sektory rezerwowe na dyskach, które pozwalają na dynamiczne przemapowywanie bloków w przypadku uszkodzeń.

### Dyski twarde:
- Dyski twarde składają się z zewnętrznej krawędzi do środka.
- Obsługują różne żądania dostępu do danych.
- Głowica może poruszać się w lewo, obsługując żądania malejących celinów, a potem w drugą stronę, obsługując żądania rosnących celinów.
- Unika się zastoje w większości przypadków, stosując strategię FZWS (First Come, Zero Wait State).
- Strategie cyklicznego skanowania pomagają zrównoważyć czas oczekiwania na różnych celinach.

### Systemy operacyjne a dyski:
- System operacyjny musi zarządzać fizycznym położeniem sektorów na dysku.
- Sterownik dysku może próbować to robić, ale system operacyjny może wymagać określonej kolejności zapisów, co komplikuje sprawę.
- Dyski SSD wykorzystują techniki rozpraszania zapisów, aby przedłużyć trwałość komórek pamięci.

### Komunikacja z urządzeniami:
- Komunikacja z urządzeniami odbywa się za pomocą portów lub odzwierciedlenia rejestrów urządzenia w przestrzeni adresowej procesu.
- Sterowniki urządzeń obsługują operacje specyficzne dla urządzenia, podczas gdy warstwa niezależna od urządzenia zarządza buforami i dostarcza wspólny interfejs.
- Synchronizacja przesyłania danych odbywa się przez aktywne oczekiwanie (polling) lub przerwania.

### Systemy plików:
- System plików jest logiczną warstwą umożliwiającą tworzenie, dostęp i operacje na plikach.
- Interfejs systemu plików zapewnia funkcje do zarządzania plikami.
- Architektura systemu plików określa wewnętrzną implementację plików w systemie.

### Różne systemy plików:
- W systemach Unix/Linux można mieć wiele różnych systemów plików jednocześnie, np. ext- ext- ext-
- Każdy użytkownik ma swój katalog domowy na lokalnym systemie plików.

### Wirtualne urządzenia:
- Systemy operacyjne mogą obsługiwać wirtualne urządzenia, które niekoniecznie są fizyczne.
- Przykłady to wirtualne pliki, np. informacje o procesorze lub partycjach na dysku twardym.

### System plików:
- Systemy plików: Systemy plików to sposoby organizacji i przechowywania danych na dyskach twardych lub innych nośnikach. Przykłady to NWS (Network type system) i Tempe FS (system plików do przechowywania plików tymczasowych).

- Dowiązania: Pliki w systemach plików mogą mieć wiele dowiązań, zarówno sztywnych (hard linki) jak i symbolicznych. Dowiązania pozwalają na dostęp do tego samego pliku poprzez różne ścieżki.

- Katalogi: Katalogi są strukturami hierarchicznymi, które zawierają spisy plików znajdujących się w danym folderze. Nazwa ścieżkowa pliku jest identyfikowana przez jego pozycję w drzewie katalogów.

- Atrybuty plików: W systemie plików plik jest identyfikowany przez i węzał (inode), który zawiera informacje o typie pliku, liczbie dowiązań, rozmiarze, identyfikatorze urządzenia itp.

- Operacje na plikach: System operacyjny udostępnia operacje do manipulowania plikami, takie jak otwieranie, zamykanie, odczytywanie i zapisywanie danych. Dyskryptor pliku jest obiektem związanym z procesem i służy do szybkiego dostępu do danych pliku.

- Katalog roboczy: Każdy proces ma związaną z nim katalog roboczy, względem którego określa się ścieżki względne. To miejsce, od którego rozpoczynają się te ścieżki.

- Tablica otwartych plików: System operacyjny przechowuje informacje o otwartych plikach w tablicy otwartych plików. Dyskryptory plików są związane z procesem i wskazują na pozycje w tej tablicy.

## WYKLAD 13

**- Struktura Systemu Plików:**
   - System plików składa się z plików i katalogów.
   - Każdy plik i katalog jest identyfikowany przez i-węzeł (inode), który przechowuje informacje o pliku/katalogu.
   - I-węzły zawierają m.in. identyfikator urządzenia, liczbę dowiązań, informacje o położeniu bloków na dysku.

**- Operacje na Plikach:**
   - Pliki muszą być otwarte przed operacjami na nich.
   - Operacja `open` otwiera plik i zwraca deskryptor pliku, który jest używany do operacji na pliku.
   - Deskryptory plików są związane z konkretnym procesem i pozycją w tablicy otwartych plików.

**- Duplikacja Deskryptorów:**
   - Deskryptory plików mogą być duplikowane, co pozwala na współdzielenie dostępu do plików między procesami.
   - Duplicating deskryptora tworzy nowy deskryptor, ale wskazuje na ten sam plik lub urządzenie.

**- Zamykanie Plików:**
   - Operacja `close` zamyka plik i usuwa deskryptor z tablicy otwartych plików.
   - Licznik dowiązań (link count) określa, ile deskryptorów wskazuje na dany plik.
   - Po zamknięciu ostatniego deskryptora plik jest zwalniany.

**- Systemowa Tablica Otwartych Plików:**
   - Systemowa tablica otwartych plików przechowuje informacje o plikach otwartych przez procesy.
   - Każda pozycja w tej tablicy zawiera informacje o pliku, pozycji w pliku, liczbie dowiązań itp.

**- Współdzielenie Pozycji w Tablicy Otwartych Plików:**
   - Jeśli kilka procesów otwiera ten sam plik, każdy otrzymuje własny deskryptor, ale wskazuje na tę samą pozycję w tablicy otwartych plików.
   - Operacje na pliku przesuwają pozycję w pliku, co wpływa na kolejne operacje na tym samym pliku.

**- Struktura i-węzła:**
   - I-węzły zawierają informacje o lokalizacji bloków danych pliku na dysku.
   - I-węzły w pamięci różnią się od i-węzłów na dysku, ponieważ zawierają dodatkowe pola, takie jak licznik dowiązań.

**- Wielkość Struktury i-węzła:**
   - Struktura reprezentująca i-węzeł w pamięci jest większa niż na dysku ze względu na dodatkowe pola, takie jak licznik dowiązań.

**Wzajemne wykluczanie w dostępie do licznika od dowiąceń do i węzła:**

- W jądrze systemowym wykluczanie dostępu do struktur danych może być zapewniane różnymi mechanizmami, w zależności od typu jądra.
- W przypadku jądra nie wyłączalnego, procesy w trybie jądra nie tracą procesora na rzecz innych procesów, co zapewnia naturalne wykluczanie.
- W przypadku jądra wyłączalnego, konieczne jest używanie odpowiednich narzędzi do synchronizacji, takich jak semafory.

**Semafor jako narzędzie synchronizacji:**

- Semafory są używane do synchronizacji dostępu do współdzielonych struktur danych w jądrze.
- Operacje P i V (czekaj i zwolnij) na semaforze pozwalają na kontrolowanie dostępu do współdzielonych zasobów.
- Użycie semaforów jest skuteczne, ale operacja P może spowodować oczekiwanie procesu, co może prowadzić do przełączenia kontekstu, co jest czasochłonne.

**Spinlock jako alternatywa:**

- Spinlocki są stosowane na poziomie jądra do synchronizacji dostępu do współdzielonych struktur danych.
- Spinlocki różnią się od semaforów tym, że oczekiwanie na spinlock jest aktywne, co oznacza, że proces nie jest wstrzymywany, a oczekuje aktywnie na zwolnienie blokady.
- Spinlocki są używane, gdy oczekiwanie na dostęp do danych nie powinno trwać zbyt długo.

**Różnica między wywłaszczaniem w trybie jądra a użytkownika:**

- Wywłaszczenie w trybie jądra i w trybie użytkownika nie różni się technicznie.
- Obie operacje zachowują wartości rejestru.
- Wywłaszczenie jest wynikiem przełączenia kontekstu między procesami.

**Usuwanie pliku i licznik odwołań:**

- Procesy mogą tworzyć pliki tymczasowe, a operacja "unlink" usuwa wpis pliku z katalogu.
- Usunięcie pliku nie oznacza natychmiastowego usunięcia go z systemu plików. Plik pozostaje dostępny, dopóki licznik odwołań do niego nie spadnie do zera.
- Zamknięcie pliku przez proces spowoduje zmniejszenie licznika odwołań. Plik zostanie usunięty z systemu plików, gdy licznik spadnie do zera, zwykle po zakończeniu procesu.

**Dostęp do plików i operacje na plikach:**

- Odczyt i zapis plików są wykonywane za pomocą funkcji systemowych "read" i "write".
- Operacje "read" i "write" są niepodzielne.
- Pliki można otwierać w różnych trybach, takich jak "apend" lub "do dopisywania", co może zmieniać pozycję wskaźnika pliku przed każdą operacją zapisu.
- Funkcja "lseek" pozwala na ręczne przesunięcie wskaźnika pliku.

**Montowanie różnych systemów plików:**

- Struktura drzewa katalogów może być złożona z niezależnych systemów plików.
- Montowanie polega na przyłączaniu innych systemów plików do istniejącej struktury.
- Operacja montowania może zasłonić fragmenty istniejącego systemu plików.
- Pliki specjalne, takie jak urządzenia i koleje FIFO, mogą być reprezentowane w systemie plików.
- Linki symboliczne pozwalają na tworzenie odnośników do innych plików i katalogów.

Oczywiście, oto ściąga na podstawie tekstu:

### Systemy Plików i Urządzenia

#### Pliki Reprezentujące Urządzenia

W systemach operacyjnych, pliki reprezentujące urządzenia są powiązane z dwiema liczbami: liczbą główną urządzenia i liczbą podrzędną urządzenia.

- **Liczba Główna Urządzenia**: Jest to rodzaj indeksu, który identyfikuje program obsługi danego urządzenia. Na przykład, wszystkie dyski twarde będą miały tę samą liczbę główną, ponieważ są obsługiwane przez ten sam sterownik. Można to traktować jako identyfikator programu obsługi urządzenia.

- **Liczba Podrzedna Urządzenia**: Jest to numer, który identyfikuje konkretne urządzenie w grupie wszystkich urządzeń obsługiwanych przez ten sam sterownik. Te dwie liczby można sprawdzić, używając polecenia `ls` z odpowiednimi parametrami.

#### Węzły Wirtualne

W kontekście systemów plików węzły wirtualne są abstrakcyjnymi obiektami, które pozwalają na reprezentację różnych systemów plików i plików. Możemy to zrozumieć jako obiektową koncepcję.

- Istnieje ogólna klasa abstrakcyjna zwana "foul węzłem."
- Konkretne instancje "foul węzła" to instancje podklas, dziedziczących z klasy "foul węzła."
- Każda podklasa opisuje konkretny system plików lub konkretny plik w danym systemie plików.

Funkcje takie jak "open," "read," "write," i "look up" mogą być implementowane w różny sposób w zależności od rodzaju systemu plików lub pliku. Na przykład, odczyt pliku z dysku lokalnego różni się od odczytu pliku z serwera plików, co wymaga nawiązania połączenia i przesłania odpowiednich bloków danych.

#### Analiza Nazwy Ścieżkowej

Analiza nazwy ścieżkowej jest algorytmem wykonywanym, gdy użytkownik używa ścieżki do pliku. Ścieżka może zawierać różne elementy, takie jak katalogi, linki symboliczne itp. W takim przypadku konieczne jest sparsowanie całej ścieżki, co może być bardziej skomplikowane niż się wydaje.

#### Systemy Plików z Kroniką

Systemy plików z kroniką utrzymują migawki stanu systemu plików w określonych interwałach czasowych. W przypadku awarii zasilania można przywrócić system plików do wcześniejszego, spójnego stanu za pomocą tych migawek. Jest to szczególnie przydatne w unikaniu niespójności systemu plików.

#### Systemy Plików Specjalnego Przeznaczenia

Niektóre systemy plików mają specjalne przeznaczenie, na przykład system plików `/proc`, który reprezentuje procesy w systemie. Można uzyskiwać informacje o procesach i zasobach systemowych, korzystając z takich systemów plików.

#### Inne Systemy Plików

Istnieją również inne specjalne systemy plików, takie jak systemy plików tymczasowe, systemy plików z wbudowaną kontrolą wersji itp. Każdy z tych systemów ma swoje zastosowanie w określonych scenariuszach.

#### Podsumowanie

Systemy plików są kluczowym elementem każdego systemu operacyjnego, pozwalając na zarządzanie plikami i danymi. Różne rodzaje systemów plików oferują różne funkcje i właściwości, które można dostosować do konkretnych potrzeb. Analiza nazwy ścieżkowej, węzły wirtualne i inne koncepcje pomagają w efektywnym zarządzaniu plikami i urządzeniami w systemie operacyjnym.