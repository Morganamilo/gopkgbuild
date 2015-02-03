# goPKGBUILD

A golang package for parsing [Arch Linux][archlinux] [PKGBUILDs][pkgbuilds]. It
uses `mksrcinfo` to create a `.SRCINFO` formatted string which is then parsed
into a slice of PKGBUILD structs.

## Dependencies

* [pkgbuild-introspection][pkg-introspec] (specifically `mksrcinfo`)

## TODO

- [x] Handle split PKGBUILDs like [linux][linux-pkg]
- [ ] Try to parse maintainer from top of PKGBUILD
- [ ] Handle multiple dependency versions
- [x] Add support for reading a `.SRCINFO` file directly
- [x] Update to pacman 4.2

## Usage

[Godoc][godoc]

Example usage

```go
package main

import (
    "fmt"

    "github.com/mikkeloscar/gopkgbuild"
)

func main() {
    pkgbs, err := ParsePKGBUILD("/path/to/PKGBUILD")
    if err != nil {
        fmt.Println(err)
    }

    for _, pkgb := range pkgbs {
        fmt.Printf("Package name: %s", pkgb.Pkgname)

    }
}
```

## LICENSE

Copyright (C) 2015  Mikkel Oscar Lyderik Larsen

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.


[archlinux]: http://archlinux.org
[pkgbuilds]: https://wiki.archlinux.org/index.php/PKGBUILD
[linux-pkg]: https://projects.archlinux.org/svntogit/packages.git/tree/trunk/PKGBUILD?h=packages/linux
[pkg-introspec]: https://github.com/falconindy/pkgbuild-introspection
[godoc]: https://godoc.org/github.com/mikkeloscar/gopkgbuild
