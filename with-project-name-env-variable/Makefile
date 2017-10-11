containers-rm:
	(export COMPOSE_PROJECT_NAME="propertyfinder" && cd cms && docker-compose stop && docker-compose rm -v -f)
	(export COMPOSE_PROJECT_NAME="propertyfinder" && cd website && docker-compose stop && docker-compose rm -v -f)

containers-up:
	(export COMPOSE_PROJECT_NAME="propertyfinder" && cd cms && docker-compose up -d)
	(export COMPOSE_PROJECT_NAME="propertyfinder" && cd website && docker-compose up -d)

network-up:
	docker network create portal.local

network-rm:
	docker network rm portal.local

up: network-up containers-up

rm: containers-rm network-rm

test:
	@echo "From cms to website"
	@echo "\t" && (cd cms && docker-compose run --rm curl.cms.portal.local curl -I nginx.website.portal.local)
	@echo "From website to cms"
	@echo "\t" && (cd website && docker-compose run --rm curl.website.portal.local curl -I nginx.cms.portal.local)
