GOPKGNAME:=github.com/yahoo/athenz/provider/aws/sia-ec2
export GOPATH ?= /tmp/go
export GOPRIVATE=github.com

FMT_LOG=/tmp/fmt.log

build: get build_linux test

linux: get build_linux test

build_linux:
	@echo "Building linux client..."
	GOOS=linux go install -ldflags -v $(GOPKGNAME)/...

get:
	@echo "Getting dependencies..."
	go get -t -d -tags testing $(GOPKGNAME)/...

vet:
	go vet $(GOPKGNAME)/...

fmt:
	gofmt -d . >$(FMT_LOG)
	@if [ -s $(FMT_LOG) ]; then echo gofmt FAIL; cat $(FMT_LOG); false; fi

test: vet fmt
	go test -v $(GOPKGNAME)/...

clean:
	go clean -i -x $(GOPKGNAME)/...
