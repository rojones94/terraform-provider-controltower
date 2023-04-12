HOSTNAME=local.com
NAMESPACE=rojones94
NAME=controltower
VERSION=1.4.0
BINARY=terraform-provider-${NAME}_${VERSION}
GOOS=$(shell go env GOOS)
GOARCH=$(shell go env GOARCH)

default: testacc

# Run acceptance tests
.PHONY: testacc
testacc:
	TF_ACC=1 go test ./... -v $(TESTARGS) -timeout 120m


#  build the provider and copy it to the terraform plugins directory
.PHONY: install-local
install-local:
	go build -o ./bin/${BINARY}_${GOOS}_${GOARCH}

	mkdir -p ~/.terraform.d/plugins/${HOSTNAME}/${NAMESPACE}/${NAME}/${VERSION}/${GOOS}_${GOARCH}

	cp ./bin/${BINARY}_${GOOS}_${GOARCH} ~/.terraform.d/plugins/${HOSTNAME}/${NAMESPACE}/${NAME}/${VERSION}/${GOOS}_${GOARCH}/${BINARY}