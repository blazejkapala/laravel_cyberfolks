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

## Instalacja Composer'a
### Instrukcja jest poprawna dla PHP w wersji 7.4

Lokalna instalacja Composer'a na koncie (źródło: https://cyberfolks.pl/pomoc/instalacja-composera/): 
curl -sS https://getcomposer.org/installer | php74

php74 composer.phar install --optimize-autoloader --no-dev

php74 artisan key:generate

php74 artisan migrate
