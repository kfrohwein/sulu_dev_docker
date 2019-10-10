# Dirty Sulu env

## Manual
- clone repo
- create an empty sulu folder ``mkdir ./sulu``
- start container ``docker-compose up -d``
- enter container ``docker exec -it sulu_php sh``
- create a sulu project ``php -d memory_limi=-1 /usr/bin/composer create-project sulu/skeleton /var/www/project -n``

