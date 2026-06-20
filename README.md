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
### Zadanie 7: Fotografik gamoń
```bash

cd "/c/Users/Daik/Desktop/Studia/semestr 2/PROJEKT-podstawy programowania/zadania"

unzip kopie-1.zip
unzip kopie-2.zip

for z in 20*.zip; do unzip -o "$z"; done

for f in *; do
    if [ -f "$f" ] && [[ "$f" != *.zip ]]; then
        magick "$f" -density 96x96 -resize x720 "${f%.*}.jpg"
        if [[ "${f##*.}" != "jpg" ]]; then rm "$f"; fi
    fi
done

zip przetworzone_zdjecia.zip *.jpg
```
###  Zadanie 8:Wszędzie te PDF-y
```bash

@media print {
  @page { margin: 0; }
  body { margin: 0; padding: 0; background: white; }
  .responsive { 
    width: 50% !important; 
    float: left !important; 
    box-sizing: border-box !important;
    padding: 10px !important;
    page-break-inside: avoid !important;
  }
  .gallery img { 
    width: 100% !important; 
    height: 220px !important; 
    object-fit: cover !important; 
  }
  .responsive:nth-child(8n) { page-break-after: always !important; }
}

"/c/Program Files/Google/Chrome/Application/chrome.exe" --headless --disable-gpu --print-to-pdf="portfolio.pdf" index.html
```
### Zadanie 9:Porządki w kopiach zapasowych
```bash
mkdir -p kopie

for plik in 20*.zip; do
    if [ -f "$plik" ]; then
        rok=$(echo "$plik" | cut -d'-' -f1)
        miesiac=$(echo "$plik" | cut -d'-' -f2)
        mkdir -p "kopie/$rok/$miesiac"
        mv "$plik" "kopie/$rok/$miesiac/"
    fi
done
```
### Zadanie 10: Galeria dla grafika
```bash

echo "" > kod_galerii.html

for f in *.jpg; do
    if [ -f "$f" ]; then
        echo "  <div class=\"responsive\">" >> kod_galerii.html
        echo "    <div class=\"gallery\">" >> kod_galerii.html
        echo "      <a target=\"_blank\" href=\"$f\">" >> kod_galerii.html
        echo "        <img src=\"$f\">" >> kod_galerii.html
        echo "      </a>" >> kod_galerii.html
        echo "      <div class=\"desc\">$f</div>" >> kod_galerii.html
        echo "    </div>" >> kod_galerii.html
        echo "  </div>" >> kod_galerii.html
    fi
done

div.gallery img {width: 100%; height: 200px; object-fit: cover;}
```
