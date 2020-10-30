start:
	docker-compose start

stop:
	docker-compose stop

up:
	docker-compose up -d

down:
	docker-compose down

composer-install:
	docker-compose exec php bash -c "cd /var/www/html/app && composer install"

composer-update:
	docker-compose exec php bash -c "cd /var/www/html/app && composer update"

composer-autoload:
	docker-compose exec php bash -c "cd /var/www/html/app && composer dump-autoload --optimize"

js-npm-install:
	docker run -it --rm -u 1000 -v $(dir $(PWD)):/app node:12.16.1 bash -c 'cd /app && npm install'

js-npm-watch:
	docker run -it --rm -u 1000 -v $(dir $(PWD)):/app node:12.16.1 bash -c 'cd /app && npm run watch'

ps:
	docker-compose ps

ssh-php:
	docker-compose exec -u dev php bash

ssh-postgres:
	docker-compose exec postgres bash -c 'psql -U app'

ssh-redis:
	docker-compose exec redis redis-cli

add-hosts:
	# ============================= добавляем тестовые хосты ============================================
	bash init/hosts

rebuild-hard:
	# === пересоздание контейнеров (с удалением данных), полная пересборка образов (без кеша) ===
	docker-compose down --volumes --remove-orphans
	docker-compose build --force-rm --no-cache
	docker-compose up -d

rebuild-soft:
# === пересоздание контейнеров (с удалением данных), частичная пересборка образов ===
	docker-compose down --volumes --remove-orphans
	docker-compose build
	docker-compose up -d

down-with-data-drop:
	docker-compose down --volumes --remove-orphans
