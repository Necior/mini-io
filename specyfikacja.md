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

* Mistrz Gry (_Game Master_) - generuje Planszę oraz Projekt, przechowuje stan Gry, generuje nowe Kawałki w Strefie Zadań.
* Serwer (_Communications Sever_) - odpowiedzialny za przekazywanie wiadomości pomiędzy Mistrzem Gry a Graczami.
