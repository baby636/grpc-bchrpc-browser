[grpc-bchrpc-browser](README.md) › [Globals](globals.md)

# grpc-bchrpc-browser

# grpc-bchrpc-browser

A bchd rpc client for browsers using grpc/grpc-web 

This package provides a simple gRPC client for connecting web applications to 
a [bchd](https://bchd.cash) full node.

[A mobile friendly version](www.grpc.cash) of this [project](https://github.com/2qx/grpc-bchrpc-browser) README. 

## Getting Started

For a quick [example usage subscribing of transactions see the console here](example/).

Detailed [RPC Documentation](https://www.grpc.cash/docs_bchrpc/) for the rpc protocol is a work in progress.

As a big-endian language, certain convenience parameters were added to the client wrapper,
 for ease of use. Also all parameters are are passed as an object, and any metadata needed
 for the connection is passed as a second argument. 

[Client Documentation](https://www.grpc.cash/docs/) which is generated using typedoc.

[Mocha browser tests](https://www.grpc.cash/test/) should provide some working examples.

## Motivation

This project uses Google's grpc/grpc-web library 
to generate a client, rather than the older and 
more widely used @improbable-eng/grpc-web.

The client is built from the pb files in advance rather
than on-the-fly, a functionality which may be employed with the @improbable library.

The motivation is toward lower maintenance, long-term stability and support by using 
the google library, not that this thinking played out well with the framework formerly known as angular. 

One notable limitation of the official grpc/grpc-web library is a lack of FETCH support.

## See also

- The [official documentation](https://github.com/gcash/bchd/tree/master/bchrpc/) for bchrpc.
- The [reference implementation](https://github.com/gcash/bchd/tree/master/bchrpc/pb-js) from the bchd team.
- Notes on the [limitations of multiplexing from a browser](https://github.com/gcash/bchd/blob/master/bchrpc/documentation/web.md)

Alternative implementations of this project are built using the improbable-eng library here:

- For the web: [grpc-bchrpc-web](https://github.com/simpleledgerinc/grpc-bchrpc-web)
- Using a local bchd node from nodejs: [grpc-bchrpc-node](https://github.com/simpleledgerinc/grpc-bchrpc-node)

## Scripts

**Note:** this project was created in node v12.2.0 (LTS) and used `protoc` version 3.11.4; and is open to using features from es2017 although initially targeted at es6.

### Build

To build:
    
    npm run build        # transpile typescript, browserify and minify use
    npm run build:docs   # build documentation for the client class

### Running Tests

Tests can be run either from console or in a browser.  The test modules and javascript must be built prior to running tests

    npm run test          # run tests in node
    npm run test:browser  # run tests in a browser

### Updating the Spec

If for some reason you need to update the gcash proto files yourself to add some future functionality use:

**Important:** an [installed](https://github.com/protocolbuffers/protobuf/releases/latest) version of `protoc`  
 is required to run `pb-build`. 

    npm run pb-clean     # remove old definitions
    npm run pb-update    # download bchrpc.proto from gcash/bchd/master
    npm run pb-build     # create client library
    npm run pb-doc       # generate documentation

### Using bchrpc in a Postman-like webgui

To facilitate debugging and development of the client, it may be useful make calls using a webui. The following npm scripts are 
provided, assuming you have golang installed.

    npm run pb-grpcui-install     # install grpcui
    npm run pb-grpcui             # run a local webui against a bchd node

## BCHD Full Nodes w/ gRPC

Mainnet:
* https://bchd.greyh.at:8335
* https://bchd.imaginary.cash:8335
* https://bchd.fountainhead.cash:443
* https://bchd.sploit.cash:443
    

Testnet:
* https://bchd.greyh.at:18335
* https://bchd-testnet.greyh.at:18335