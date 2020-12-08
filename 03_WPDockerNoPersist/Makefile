.PHONY: simple 
simple: 
	@echo "WordPress environment with no email"
	@cp docker-compose-nohog.yml docker-compose.yml && docker-compose up --force-recreate 
	
.PHONY: email 
email: 
	@cp docker-compose-email.yml docker-compose.yml && docker-compose up --force-recreate 
