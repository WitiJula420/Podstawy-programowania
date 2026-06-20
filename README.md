# Podstawy-programowania




Zadanie 3: Niesforne dane

dos2unix dane.txt

echo -e "x\\ty\\tz" > wynik.txt

paste - - - < dane.txt >> wynik.txt


Zadanie 4: Dodawanie poprawek


`diff -u lista.txt lista-pop.txt > latka.patch`

`patch lista.txt < latka.patch`


Zadanie 5: Z CSV do SQL i z powrotem

awk -F';' 'NR>1 {print "INSERT INTO stepsData (time, intensity, steps) VALUES ("$1", "$2", "$3");"}' steps-2sql.csv > do_bazy.sql


Zadanie 6: Marudny tłumacz

sed 's/.*: ".*",/    \/\/ &\n&/' en-7.2.json5 > pl-7.2.json5
