ifndef VERBOSE
.SILENT:
endif

name =

.PHONY: migrate-add
migrate-add:
	cd docker && docker compose run --rm app \
	sh -c "sqlx migrate add $(name)"

.PHONY: migrate-run
migrate-run:
	cd docker && docker compose run --rm app \
	sh -c "sqlx db setup"

.PHONY: up
up: migrate-run
	cd docker && docker compose up --build

.PHONY: down
down:
	cd docker && docker compose down

.PHONY: db-drop
db-drop: down
	cd docker && docker compose run --rm app \
	sh -c "sqlx db drop"
