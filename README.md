# BackstopJS container for docker

A self-contained minimal (230Mb) image to run BackstopJS 2.5.0. Build on top of Alpine linux.

This image include PhantomJS 2.1.1 and CasperJS 1.1.3.

## Usage

```sh
docker run --rm -u backstop -v $PWD:/app/ dimanech/backstopjs-alp test
# If you don't use standard path to config than
docker run --rm -u backstop -v $PWD:/app/ dimanech/backstopjs-alp test --configPath=path/to/backstop.json
```

```sh
docker run --rm -u backstop -v $PWD:/app/ dimanech/backstopjs-alp reference
# or
docker run --rm -u backstop -v $PWD:/app/ dimanech/backstopjs-alp reference --configPath=path/to/backstop.json
```

### Usage with Bitbucket pipelines

If you use this image with Bitbucket pipeline you need to use command name since bitbucket override entry point to `sh`.

```sh
backstop test
# or
backstop test --configPath=path/to/backstop.json
```

### Run not from root

```sh
docker run --rm -u backstop -v $PWD:/app/ dimanech/backstopjs-alp test
docker run --rm -u backstop -v $PWD:/app/ dimanech/backstopjs-alp reference
```

## Websafe fonts inside container

If you app require **websafe** fonts you can emulate user preseted fonts by adding it under `.fonts` directory in your project. Content of this folder will be accessible in docker. For example you can add some proprietary fonts to use it in tests. To do this just add `.fonts/some-font.ttf` and this font will be available as installed on system.

## Debug

```sh
docker run --rm -v $PWD:/app/ -it --entrypoint=bash dimanech/backstopjs-alp
```

---

This work based on https://github.com/docksal/backstopjs/blob/master/Dockerfile
