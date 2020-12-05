.PHONY: compose-up
compose-up: 
	@docker-compose up --force-recreate 

.PHONY: simple 
simple: compose-up
	@docker-compose -f docker-compose-nohog.yml build