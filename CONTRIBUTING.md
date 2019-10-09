# Contributing

Thanks for considering a contribution to [Xpring SDK](https://github.com/xpring-eng/xpring-sdk)!

We're thrilled you're interested and your help is greatly appreciated. Contributing is a great way to learn about the [XRP Ledger](https://xrpl.org) and [Interledger Protocol (ILP)](https://interledger.org/). We are happy to review your pull requests. To make the process as smooth as possible, please read this document and follow the stated guidelines.

## About This Library

TODO: Diagram of Xpring SDK

This library is made up of [protocol buffers](https://developers.google.com/protocol-buffers) which form common model objects for Xpring SDK. There are also [gRPC service definitions](https://grpc.io), which form a network interface for  Xpring SDK.

This library is consumed by both the [Xpring Common JavaScript](https://github.com/xpring-eng/xpring-common-js), the server side component (TODO: link), and the [language specific client libraries](https://github.com/xpring-eng/xpring-sdk#client-side-libraries).

This library is widely consumed and must remain backwards compatible. Therefore, Xpring will be fairly judicious about what new functionality gets added here.

Additionally, code changes to this library will likely be accompanied by a feature change in one or more dependent libraries. A new pull request should document how the new fields and functionality will be used.

## Requirements for a Successful Pull request

- Title is prefixed with "[WIP]" if the pull request is not ready for review.
- Continuous integration tests pass on pull request.
- Documentation in pull request about how the new functionality will be used in client libraries.
- Changes to protocol buffers adheres to [Google's Protocol Buffer style guide](https://developers.google.com/protocol-buffers/docs/style).
- Changes to gRPC services adhere to [Google's API design guidelines](https://cloud.google.com/apis/design/).
- Text and comments of pull request adhere to the [code of conduct](CODE_OF_CONDUCT.md) for this repository.

## Building The Library

Any successful compilation of protocol buffers is sufficient to prove this library builds. By default, the protocol buffer compiler compiles to C++ code, which is what the continuous integration build for this library also uses.

The following commands should bootstrap a developer environment:
```
# Install Protocol Buffer Compiler
# OSX
$ brew install protobuf
# Linux
$ sudo apt install protobuf-compiler
# Otherwise, see: https://github.com/protocolbuffers/protobuf#protocol-compiler-installation

# Install gRPC
git clone -b $(curl -L https://grpc.io/release) https://github.com/grpc/grpc
cd grpc
git submodule update --init
make

# Build the protocol buffers!
protoc --proto_path=./proto/ --cpp_out ./generated/  --grpc_out=./generated --plugin=protoc-gen-grpc=grpc/bins/opt/grpc_cpp_plugin ./proto/*.proto
```
