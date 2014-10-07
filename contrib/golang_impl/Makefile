GIT_COMMIT = $(shell git rev-parse --short HEAD)
GIT_STATUS = $(shell test -n "`git status --porcelain`" && echo "+CHANGES")

all:
	CGO_ENABLED=0 go build -a -ldflags "-s -X main.GITCOMMIT $(GIT_COMMIT)$(GIT_STATUS)" -o ./bin/docker-registry

image:
	mkdir -p ./tmp && touch ./tmp/.gitignore
	docker build -t minimal-registry .
	rm -rf ./tmp

test:
	@go get github.com/remogatto/prettytest
	go test -v
