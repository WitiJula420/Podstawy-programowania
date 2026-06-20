# Podstawy-programowania



### Zadanie 3: Niesforne dane

```bash
dos2unix dane.txt
echo -e "x\ty\tz" > wynik.txt
paste - - - < dane.txt >> wynik.txt
```
### Zadanie 4: Dodawanie poprawek
```bash
diff -u lista.txt lista-pop.txt > latka.patch

patch lista.txt < latka.patch
```
### Zadanie 5: Z CSV do SQL i z powrotem
```bash
awk -F';' 'NR>1 {print "INSERT INTO stepsData (time, intensity, steps) VALUES ("$1", "$2", "$3");"}' steps-2sql.csv > do_bazy.sql

echo "dateTime;steps;synced" > z_bazy.csv
awk -F'[ ,();]+' '/INSERT/ { print substr($8, 1, length($8)-3) ";" $9 ";" $10 }' steps-2csv.sql >> z_bazy.csv
```
### Zadanie 6: Marudny tłumacz
```bash
sed 's/.*: ".*",/    \/\/ &\n&/' en-7.2.json5 > pl-7.2.json5

diff en-7.2.json5 en-7.4.json5 | grep "^>" | sed 's/^> //' > pl-7.4.json5
```
