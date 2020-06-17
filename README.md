# alpine-pkg-glibc

This is the [GNU C Library](https://gnu.org/software/libc/) as a Alpine Linux package to run binaries linked against `glibc`. This package utilizes a custom built glibc binary based on the vanilla glibc source. Built binary artifacts come from https://github.com/gravitational/docker-glibc-builder.

## Releases

See the [releases page](https://github.com/gravitational/alpine-pkg-glibc/releases) for the latest download links. If you are using tools like `localedef` you will need the `glibc-bin` and `glibc-i18n` packages in addition to the `glibc` package.

## Installing

The current installation method for these packages is to pull them in using `wget` or `curl` and install the local file with `apk`:

    wget -q -O /etc/apk/keys/gravitational.rsa.pub https://gist.githubusercontent.com/webvictim/a02fe5a0146e381307b5cb6901b617b1/raw/790df9d2ce758793d3df96d7cda570c69eecabbf/gravitational.rsa.pub
    wget https://github.com/gravitational/alpine-pkg-glibc/releases/download/2.31-r0/glibc-2.31-r0.apk
    apk add glibc-2.31-r0.apk

## Locales

You will need to generate your locale if you would like to use a specific one for your glibc application. You can do this by installing the `glibc-i18n` package and generating a locale using the `localedef` binary. An example for en_US.UTF-8 would be:

    wget https://github.com/gravitational/alpine-pkg-glibc/releases/download/2.31-r0/glibc-bin-2.31-r0.apk
    wget https://github.com/gravitational/alpine-pkg-glibc/releases/download/2.31-r0/glibc-i18n-2.31-r0.apk
    apk add glibc-bin-2.31-r0.apk glibc-i18n-2.31-r0.apk
    /usr/glibc-compat/bin/localedef -i en_US -f UTF-8 en_US.UTF-8
