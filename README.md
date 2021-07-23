# Hosting cyberfolks.pl (dawniej linuxpl.com) jako hosting dla Laravel

## Założenia
# laravel_cyberfolks
Laravel na cyberfolks.pl

Lokalna instalacja Composera na koncie hostingowym jest bardzo prosta i ogranicza się do kilku poleceń. Po zalogowaniu się na konto przez SSH, wywołujemy polecenie:
https://cyberfolks.pl/pomoc/instalacja-composera/
 curl -sS https://getcomposer.org/installer | php74

php74 composer.phar install --optimize-autoloader --no-dev

php74 artisan key:generate

php74 artisan migrate:fresh --seed
