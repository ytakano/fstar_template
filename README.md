# Template of F star

## Run Container and Compile F star's source code

### Host

Build a container image and run the container.

```
$ cd docker
$ docker-compose build
$ docker-compose run fstar
```

### Guest Container

Compile an example file, and execute it.

```
# cd src
# make
# ./hello.exe
Hello F*!
```
