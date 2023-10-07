# gRPC Hello-world

## Prerequisite

Homebrew install javascript-protoc

```sh
brew install protoc-gen-grpc-web
```

## Run in docker

Build the images

```sh
docker-compose build
```

Run the server via docker

```sh
docker-compose up
```

Run the front-end

```sh
npm run start
```

## Run in terminal

 1. Run the NodeJS gRPC Service. This listens at port `:9090`.

 ```sh
 node server.js
 ```

 2. Run the Envoy proxy. The `envoy.yaml` file configures Envoy to listen to
 browser requests at port `:8080`, and forward them to port `:9090` (see
 above).

 ```sh
 docker run -d -v "$(pwd)"/envoy.yaml:/etc/envoy/envoy.yaml:ro \ 
    -p 8080:8080 -p 9901:9901 envoyproxy/envoy:v1.27-latest
 ```

 3. Run the simple Web Server. This hosts the static file `index.html` and
 `dist/main.js` we generated earlier.

 ```sh
 npx http-server -p 8081
 ```

## Reference

More info: <https://github.com/grpc/grpc-web/tree/master/net/grpc/gateway/examples/helloworld>
