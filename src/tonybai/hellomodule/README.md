This is a simple go module for learning.

## go mod
```
go mod init github.com/tonybai/hellomodule
go mod tidy
```
## go build
```
go build -o hellomodule.so -buildmode=c-shared main.go
```

## run built executable
```
./hellomodule.so
```

## downgrade go version
```
go list -m -versions github.com/valyala/fasthttp
go mod edit -require=github.com/valyala/fasthttp@v1.60.0

# go get github.com/valyala/fasthttp@v1.60.0
go mod tidy

``` 

