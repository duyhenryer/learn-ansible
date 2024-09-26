.PHONY: build
build:
	docker build . -t artis3n/docker-oraclelinux8-ansible:$${TAG:-test}

.PHONY: run
run: build
	docker run -id --rm --name runner --privileged --cgroupns=host --volume=/sys/fs/cgroup:/sys/fs/cgroup:rw artis3n/docker-oraclelinux8-ansible:$${TAG:-test}
	-docker exec -it runner /bin/sh
	docker stop runner