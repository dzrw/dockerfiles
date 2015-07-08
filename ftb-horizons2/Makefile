SHELL=/bin/bash

.PHONY: all build

build:
	docker build --pull -t politician/ftb-horizons2:latest .

push:
	docker push politician/ftb-horizons2

# daemonize the container
run:
	docker run -d -p 25565:25565 --name ftb_horizons2 politician/ftb-horizons2:latest

# open a shell in a running container
sh:
	docker exec -it ftb_horizons2 /bin/sh

# tail stdout
tail:
	docker logs ftb_horizons2

# open a shell in a temporary container
tmp:
	docker run --rm -i -t --entrypoint "/bin/sh" politician/ftb-horizons2:latest



