
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
