# go-grpc

## Overview

- go で 簡易な gRPC Server を作成する

## Start

```bash
go run ./cmd/server/main.go
```

```bash
grpcurl -plaintext -d '{"name": "taro"}' localhost:8082 myapp.GreetingService.Hello
```

## proto setup

- protobuf を installしておく

```bash
# Mac
brew install protobuf
```

- ライブラリを取得

```bash
go install google.golang.org/grpc
go install google.golang.org/protobuf/cmd/protoc-gen-go
```

- proto ファイルから 自動生成する

```bash
protoc --go_out=../pkg/grpc --go_opt=paths=source_relative \
       --go-grpc_out=../pkg/grpc --go-grpc_opt=paths=source_relative \
       ./proto/hello.proto
```
