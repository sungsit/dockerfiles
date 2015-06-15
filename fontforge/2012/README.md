# FontForge 2012 Container

It's Debian mininal container to run older Fontforge (2012) through X11-Unix socket. The container user name is `fontdev`.

Sample `docker` command:

1. Test without saving container.

  ```
  docker run -it --rm -e DISPLAY=unix$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix "sungsit/fontforge:2012"
  ``` 

2. Mount your projects dir without saving container but you can save your files unless precisely specify `:ro` to `-v` flag.

  ```
  docker run -it --rm -e DISPLAY=unix$DISPLAY \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -v /host/projects:/docker/projects \
    "sungsit/fontforge:2012"
  ```

Mac OS host work around: See <https://github.com/docker/docker/issues/8710#issuecomment-71113263>
