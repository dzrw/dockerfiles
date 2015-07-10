SHELL=/bin/bash

REPOSITORY := politician/ftb-horizons2
TAG ?= latest
NAME ?= ftb_horizons2

.PHONY: all build

build:
	docker build --pull -t $(REPOSITORY):$(TAG) .

clean:
	docker rm $(NAME)

push:
	docker push $(REPOSITORY)

# daemonize the container
run:
	docker run -d -p 25565:25565 --name $(NAME) $(REPOSITORY):$(TAG)

run_with_ramdisk:
	docker run -d -v /ramdisk:/var/lib/minecraft -p 25565:25565 --name $(NAME) $(REPOSITORY):$(TAG)

# open a shell in a running container
sh:
	docker exec -it $(NAME) /bin/sh

# tail stdout
logs:
	docker logs -f $(NAME)

# open a shell in a temporary container
tmp:
	docker run --rm -i -t --entrypoint "/bin/sh" $(REPOSITORY):$(TAG)



