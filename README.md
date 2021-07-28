# Hosting cyberfolks.pl (dawniej linuxpl.com) jako hosting dla Laravel

## Wgranie plików na hasting do katalogu ./nazawa.domeny/public_html
Kopiujemy katalog root'a Laravela tak aby katlog public znajdował się w public_html

```
/home/nazwa_uzytkownia_cyberfolks/domains/nazwa_domeny/public_html/public/
```
czyli cały projekt znajdował się w:
```
/home/nazwa_uzytkownia_cyberfolks/domains/nazwa_domeny/public_html/
```

## Przypisanie domeny do katalogu "public"
Znajdujemy w panelu serwera "Przypisz katalog do domen i subdomen"

i dla naszej domeny wprowadzamy jako  "pełną ścieżkę dostępową":

```
/home/nazwa_uzytkownia_cyberfolks/domains/nazwa_domeny/public_html/public/
```

## Tworzymy nową bazę danych
Znajdujemy w panelu serwera "Utwórz nową bazę danych MySQL":
dane bazy zapiszemy w kolejnym kroku

## Edycja ustawień zmiennych środowiskowych .env
Aby edytować plik .env:
```
nano .env
```
W stosunku do środowiska developerskiego należy ustawić
```
APP_NAME=NazaProjektu
APP_ENV=production #ustawiamy Laravela w wersji produkcyjnej
APP_KEY=
APP_DEBUG=false #wyłączamy wyświetlanie błędów
APP_URL=http://nasza.domena.com.pl

```

Wprowadzamy dane uzyskane podczas tworzenia bazy danych
```
DB_CONNECTION=mysql
DB_HOST=localhost#domyślne dla cyberfolks baza na tym samym serwerze
DB_PORT=3306
DB_DATABASE=nazwauzytkownikacyberfolks_nazwabazy
DB_USERNAME=nazwauzytkownikacyberfolks_uzytkownikbazy
DB_PASSWORD=skomplikowanehaslo
```

## Instalacja Composer'a
### Instrukcja jest poprawna dla PHP w wersji 7.4

Lokalna instalacja Composer'a na koncie (źródło: https://cyberfolks.pl/pomoc/instalacja-composera/): 
```
curl -sS https://getcomposer.org/installer | php74
```
następnie wywołujemy polecenie
```
php74 composer.phar install --optimize-autoloader --no-dev
```
## "Uruchomienie" Laravela
### Należy wygenerować nowy klucz aplikacji
```
php74 artisan key:generate
```
### Wykonać migrację
```
php74 artisan migrate
```

## Sprawdzenie
Jeżeli wykonaliśmy wszystko poprawnie to po wprowadzeniu adresu naszej domeny w przeglądarce powinna się nam wyświetlić nasza stona/aplikacja oparta o Laravel'a

## Wykonanie symlinka do storage
Nie wiem czemu nie zadziałało. Tzn zadziałoało jakoś dziwnie - skopiowało pliki, a nie utworzyło linka.
```
php74 artisan storage:link
```
utworzyłem simulinka ręcznie będąc w katoalogou root'a Laravela
```
ln -s ../storage/app/public storage
```
