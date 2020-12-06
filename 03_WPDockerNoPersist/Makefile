.PHONY: up
up: 
	@docker-compose up --force-recreate 

.PHONY: simple 
simple: 
	@cp docker-compose-nohog.yml docker-compose.yml && docker-compose up --force-recreate 