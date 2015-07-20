# FontForge (2012) on Debian (size: 234.4MB)

Debian mininal image to run Fontforge (2012 +Python extension) container through X11-Unix socket. The container user name is `fontdev`.

Sample `docker` commands:

1. Test without saving container.

  ```
  docker run -it --rm -e DISPLAY=unix$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix sungsit/fontforge:debian
  ``` 

2. Mount your projects dir without saving container.

  ```
  docker run -it --rm -e DISPLAY=unix$DISPLAY \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -v /host/projects:/docker/projects \
    sungsit/fontforge:debian
  ```

Mac OS host: See <https://github.com/docker/docker/issues/8710#issuecomment-71113263>
