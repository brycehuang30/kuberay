OUTPUT_NAME := kuberay
BUILD_GOOS = $(shell go env GOOS)

COMMIT := $(shell git rev-parse --short HEAD)
VERSION := $(shell git describe --tags $(shell git rev-list --tags --max-count=1))
DATE=$(shell date -u +'%Y-%m-%dT%H:%M:%SZ')
REPO="github.com/ray-project/kuberay"

BUILD_FLAGS = -ldflags="-X '${REPO}/cli/pkg/cmd/version.Version=$(VERSION)' \
	-X '${REPO}/cli/pkg/cmd/version.gitCommit=$(COMMIT)' \
	-X '${REPO}/cli/pkg/cmd/version.buildDate=$(DATE)'"

build:
	go build $(BUILD_FLAGS) -o $(OUTPUT_NAME) main.go
	chmod +x $(OUTPUT_NAME)

# GOOS=linux GOARCH=amd64 make build
# GOOS=darwin GOARCH=amd64 make build

