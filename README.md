
# Specyfikacja

(Poniższa specyfikacja jest silnie inspirowana wytycznymi z opisu The Project Game na stronie [prowadzącego przedmiot](http://www.mini.pw.edu.pl/~okulewiczm/www/?Dydaktyka:IO) oraz ustaleniami na zajęciach).

## Wstęp

System pozwala na organizowanie meczy pomiędzy zespołami.

## Pojęcia

* Gracz (_Player_) - agent grający w Grę.
* Kawałek (_Piece_) - token, reprezentujący zasób.
* Plansza (_Board_) - prostokątny obszar, podzielony na kafelki.

* Strefa Celu (_Goal Area_) - część Planszy, na której Gracze umieszczają Kawałki.
* Strefa Zadań (_Tasks Area_) - część Planszy, z której Gracze podnoszą Kawałki.

* Projekt (_Project_) - symulowany projekt; ma swój cel, który jest reprezentowany kształtem w Strefie Celu.
* Cel Gry (_Game Goal_) - odkrycie kształtu Projektu poprzez umieszczanie Kawałków w Strefie Celu.
* Zespół (_Team_) - grupa współpracujących Graczy, dążących do osiągnięcia Celu Gry.
* Gra (_Project Game_) - gra czasu rzeczywistego, odbywająca się na Planszy, gdzie rywalizują dwa Zespoły.

## Notatki

### 2016-10-23

* Nie można wejść w Strefę Celu przeciwnika.
* Mając Kawałek można wejść na pole z innym Kawałkiem.
* Gra się kończy, gdy którakolwiek drużyna odkryje wszystkie cele.
* Gracze w obrębie jednego Zespołu mogą mieć inne strategie.
* Na jednym polu może znajdować się co najwyżej jeden Gracz.
* Odpowiadamy całą Planszą przy wymianie informacji.
* Wymiana informacji przebiega w jedną stronę.
    * Podczas wymiany informacji obydwaj gracze tracą czas
* Jednym z konfigurowalnych ustawień Gry jest "komunikacja pomiędzy Zespołami" (jako `true`/`false`). Nazwijmy to roboczo "flagą komunikacji".
* Podawanie fałszywych informacji jest zabronione.
* Lider ma obowiązek odpowiadania swojemu Zespołowi.
* Lider ma obowiązek odpowiadanie przeciwnemu Zespołowi, o ile jest ustawiona "flaga komunikacji".
* Jeśli dane pole nie jest celem, to Kawałek *nie* znika po odłożeniu. Można (być może warto) go podnieść.
* Gracz raczej nie powinien zostawiać Lipnych Kawałków w Strefie Celu, ale nie jest to formalny wymóg.
    * A nie ustaliliśmy przypadkiem tak, że trzeba wynieść ten kawałek poza Strefę Celu?
* Można przechodzić przez pola z Kawałkami i ich nie podnosić.
* Zawsze widzimy pole pod sobą (wraz z odległością do najbliższego Kawałka, być może równą 0).
* Podniesienie Kawałka zwraca Graczowi informację o nowej odległości do najbliższego Kawałka.
    * Jest to rówznoznaczne z tym, że Master musi przeliczyć całą planszę po podniesieniu kawałka
* Cel odkrywamy tylko poprzez położenie Kawałka, nie poprzez odkrywanie pól dookoła.
* Kawałek można testować tylko, jeśli Gracz "ma go w ręku".
* Odłożenie Kawałka na pole sprawia, że Kawałek tam zostaje, niezależnie od tego, czy to cel.
* Znamy tylko pozycje Graczy, nie to, czy "mają w ręku" Kawałek.
* Przy generowaniu Planszy, stosujemy symetrię środkową ułożenia celu.
* W przypadku Lipnego Kawałka, przy odkładaniu, nie dostajemy informacji, czy to pole celu, czy też nie.
    * Tym samym mamy informację, że to Lipny Kawałek
* W przypadku Porządnego Kawałka, przy odkładaniu, dostajemy informację, czy to pole celu, czy też nie.
* Mistrz Gry może usunąć Lipny Kawałek (o ile nie jest właśnie "w czyjejś dłoni"). Może też wygenerować nowy, na wolnym polu.
    * Przyjęliśmy, że jest maksymalna liczba fałszywek na planszy
* Domyślne parametry Gry będą ustalone, ale są one zmienialne.
* Wymiana informacji nie przechodzi przez Mistrza Gry.

### 06.11.2017

* Niepoprawny ruch (np. ktoś już stoi na danym polu) nic nie kosztuje.
* Game Master zarządza i pilnuje opóźnień dla wszystkich graczy.
* Gra nie jest turowa, jest czas rzeczywistego (z opóźnieniami).
* Podczas dodawania kolejnego Lipnego Kawałka, jeśli zostanie przekroczony limit, usunięty zostanie najstarszy możliwy do usunięcia.
* Do serwera komunikacyjnego łączą się sami gracze. Klasa Team jest opcjonalna - może pomóc w zarządzaniu strategiami w drużynie.
* Sposób komunikacji (sieciowej) zostanie ustalony później.
* W dokumentacji należy umieścić wszystkie notatki, ustalenia i diagramy (aczkolwiek to nie wszystko).

### 20.11.2017
* Komunikacja też idzie przez GameMastera.
* Gracz dostaje informację o odległości od najbliższego kawałka wchodząc na dane pole, informacja nie jest potem uaktualniana.
* Ruch - gracz wysyła rządanie do Game Mastera, Game Master wysyła odpowiedź czy akcja może być wykonana, jeśli ruch jest dozwolony wykonuje ruch gracza, odkładanie kawałka, GameMaster czeka tyle ile trzeba, wysyła odpowiedź, jaki jest stan planszy, że czas się skończył i można wysłać następne polecenie.
* Po położeniu dobrej flagi na dobry kafelek zaznaczamy że jest to spełniony cel.
* Game Master tworzy kawałki jak chce.
* Dodajemy akcję która nie wymaga opóźnienia w której możemy poznać informacje: położenie wszystkich graczy, odległość na polu pod sobą.
* Wysłanie prośby o informacje kosztuje jakiś czas, a potem oddzielnie dostajemy odpowiedź, w międzyczasie można wykonywać akcje.
* Widzimy odległości tylko do kawałków na Task Area i swoim Goal Area.
* Informacje po odłożeniu flagi na goal area: jeśli mamy fałszywkę dostajemy informację, że jest fałszywka. Jak mamy dobrą flagę dostajemy informację czy pole jest dobre, czy złe.

### 04.12.2017

* Początkowe ustawienie gracza jest losowane przez Game Mastera.
* Serwer komunikacyjny ma być jedynie pośrednikiem. Cała logika gry jest przechowywana przez Game Mastera.


