
## gRPC Hello World Example

It's hello world example for gRPC in both Java and Go. It's a simple application, which the clien sends its name, which the server sends back a message "hello world".

#### prerequisite

Install [protoc](https://github.com/google/protobuf/blob/master/README.md)

#### Go

Golang has a nice and elegant support for gRPC and protoc-buf.

Firstly, install the protoc Go plugin by:

```
$ go get -u github.com/golang/protobuf/protoc-gen-go
```

To generate the gRPC code in ```goHello```. You can follow the commands:

```
$ cd ./goHello
$ protoc --go_out=plugins=grpc:. helloworld.proto
```

Run and Test:

```
# server
$ go run goHello/server/main.go
# client
$ go run goHello/client/main.go
```

#### Java

Two different ways:

1. protobuf-based codegen integrated with the Gradle build system

    The project is using this way. Read ```build.gradle``` for more information.

2. manual generate gRPC and protoc code
    
    ```
    $ protoc --plugin=protoc-gen-grpc-java=<path_protoc-gen-grpc-java> --grpc-java_out=. --proto_path=. helloworld.proto
    $ protoc --java_out=./ helloworld.proto
    ```
    
    How to get ```protoc-gen-grpc-java```. Clone repo ```https://github.com/grpc/grpc-java```. And then to build and to install by ```./gradlew build``` and ```./gradlew install```. The ```protoc-gen-grpc-java``` can be found in ```grpc-java/compiler/build/exe/java_plugin/protoc-gen-grpc-java```(Ubuntu) or ```grpc-java/compiler/build/binaries/java_pluginExecutable/protoc-gen-grpc-java```(Mac)
    
Run and Test:

```
# server
$ gradle runServer
# client
$ gradle runClient
```
