# Podstawy-programowania



\### Zadanie 3: Niesforne dane



Rozwiązanie polegało na naprawieniu formatowania końców linii (z DOS na UNIX), dodaniu nagłówka i połączeniu pojedynczej kolumny w trzy:



```bash

dos2unix dane.txt

echo -e "x\\ty\\tz" > wynik.txt

paste - - - < dane.txt >> wynik.txt

