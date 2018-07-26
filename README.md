# Docker composer image

This image extends the official Composer image by adding few improvements. It is based on the image of [gambry/composer](https://hub.docker.com/r/gambry/composer/).

Add-Ons:

* Patch: official Composer image ships with the BusyBox version of patch, which has limited functionality compared with the normal patch command you may find in Unix-like environment. This image adds a full patch command so for instance you can it in conjunction with 'cweagans/composer-patches'.
* Added PHP GD (for Drupal 8.5)

To use the composer container directly from the commandline use this or add it to your .bashrc/.zshrc/... file:

```
composer() {
  tty=
  tty -s && tty=--tty
  docker run \
    $tty \
    --interactive \
    --rm \
    --user $(id -u):$(id -g) \
    --volume /etc/passwd:/etc/passwd:ro \
    --volume /etc/group:/etc/group:ro \
    --volume $(pwd):/app \
    cbeier/composer "$@"
}
```
