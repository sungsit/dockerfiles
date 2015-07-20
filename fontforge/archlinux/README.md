# FontForge on Archlinux (size: 604.8MB)

Archlinux mininal image to run Fontforge (+Python extension) container through X11-Unix socket. The container user name is `fontdev`.

Sample `docker` commands:

1. Test without saving container.

  ```
  docker run -it --rm -e DISPLAY=unix$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix sungsit/fontforge:archlinux
  ``` 

2. Mount your projects dir without saving container.

  ```
  docker run -it --rm -e DISPLAY=unix$DISPLAY \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -v /host/projects:/docker/projects \
    sungsit/fontforge:archlinux
  ```

Mac OS host: See <https://github.com/docker/docker/issues/8710#issuecomment-71113263>
