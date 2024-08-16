# niv-updater

## Install

`niv-updater` can be installed and updated via niv itself:

1. add niv-updater to your sources:

```bash
niv add herbetom/niv-updater
```

2. edit `shell.nix` to add niv-updater to your development shell:


```nix
{ pkgs ? import <nixpkgs> {} }:
pkgs.mkShell {
  packages = with pkgs; [
    niv
    # This is the important line:
    (pkgs.callPackage "${(import ./nix/sources.nix).niv-updater}/pkgs/niv-updater.nix" {})
  ];
}
```

3. enter `nix-shell`. That's it!


## Usage

```
$ niv-updater --help
usage: niv-updater [-h] [--no-changelog] [-c CONFIG] [PACKAGE]

Update niv sources and commit changes with a changelog

positional arguments:
  PACKAGE               The repo to update

options:
  -h, --help            show this help message and exit
  --no-changelog        do not create a changelog
  -c CONFIG, --config CONFIG
                        provide a config file
```
