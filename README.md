# webvsc-cli

[![npm](https://flat.badgen.net/npm/license/@visbot/webvsc-cli)](https://www.npmjs.com/package/@visbot/webvsc-cli)
[![npm](https://flat.badgen.net/npm/v/@visbot/webvsc-cli)](https://www.npmjs.com/package/@visbot/webvsc-cli)
[![Travis](https://flat.badgen.net/travis/idleberg/webvsc-cli)](https://travis-ci.org/idleberg/webvsc-cli)
[![David](https://flat.badgen.net/david/dep/idleberg/webvsc-cli)](https://david-dm.org/idleberg/webvsc-cli)
[![David](https://flat.badgen.net/david/dev/idleberg/webvsc-cli)](https://david-dm.org/idleberg/webvsc-cli?type=dev)

## Description

CLI tool to batch-convert [Winamp AVS presets](https://www.wikiwand.com/en/Advanced_Visualization_Studio) into native [Webvs](https://github.com/azeem/webvs) JSON format.

## Installation

Use your preferred [Node](https://nodejs.org) package manager to install the CLI globally

```sh
$ yarn global add @visbot/webvsc-cli || npm install --global @visbot/webvsc-cli
```

## Usage

### CLI

Once setup, you can run `webvsc --help` to list available options:

```
$ webvsc

  Usage: webvsc [options] <file(s)>

  Options:

    -V, --version      output the version number
    -v, --verbose <n>  control the amount of output displayed
    -m, --minify       minify generated JSON
    -q, --quiet        print errors only
    -D, --no-date      don't create date from file meta
    -H, --no-hidden    don't extract hidden strings from fixed-size strings
    -h, --help         output usage information
```

Commonly, you would run `webvsc "avs/**/*.avs"` to convert a bunch of presets, or just one. When using wildcards, you *might* have to wrap the path in quotes.

### Troubleshooting

When trying to convert a large number of files, you might run into an `EMFILE` error. This is a well-documented [issue](https://github.com/nodejs/node/issues/1941) that occurs whenever the number of [maximum open files](http://blog.izs.me/post/56827866110/wtf-is-emfile-and-why-does-it-happen-to-me) exceeds its limit. In such a case, you can use the following as workaround.

```sh
# Bash
$ for dir in avs/*; do echo $dir; webvsc "$dir/**/*.avs" --quiet; done

# Windows
$ for /r %i in (avs/*) do webvsc %i --quiet
```

## License

All code is licensed under [The MIT License](http://opensource.org/licenses/MIT)
