# Go Wasm Playground

Compile Golang to WebAssembly for rendering web apps.

## Build

Go provides an out of the box compilation target. Just set `GOOS` and `GOARCH` like so:

```bash
$ GOOS=js GOARCH=wasm go build -o ./web/dist/app.wasm
```

## Browser execution

To support `GOOS=js` you must include a support file from Go

```bash
$ cp "$(go env GOROOT)/misc/wasm/wasm_exec.js" ./web/dist
```

There is a basic HTTP server in `server`:

 ```bash
$ go build -o ./server/dist/server ./server
$ chmod u+x ./server/dist/server
$ ./server/dist/server --listen :9999 --dir ./web
```